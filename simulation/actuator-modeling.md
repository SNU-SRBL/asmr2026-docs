---
title: Actuator Modeling
parent: Simulation and Learning
nav_order: 2
permalink: /simulation/actuator-modeling/
---

# Actuator Modeling
{: .no_toc }

A policy trained in simulation only works on the real robot if the simulated actuators behave like the real ones. An **actuator model** describes how a command, such as a target joint position, turns into the torque the joint actually produces. It covers effects like friction, inertia, torque limits, and delay.

Inaccurate actuator models and missing latency were identified early on as two major causes of the sim-to-real gap in legged robots (Tan et al., 2018). This page summarizes the common approaches, from simple to advanced.

<details open markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## The workflow

Whichever model you choose, the process is the same:

1. **Bench test a single actuator.** Typical tests:
   - **Static test:** hold a known load at known angles to measure the torque constant and breakaway friction.
   - **Swing (pendulum) test:** attach a known mass on an arm, let it swing, and record the motion. This reveals armature (reflected inertia) and friction.
   - **Step or chirp response:** command steps or sweeping frequencies to see the response speed and delay.
2. **Choose a model** (see below).
3. **Fit the parameters:** replay the same commands in simulation and adjust the parameters until the simulated trajectory matches the recorded one.
4. **Validate** on data you didn't fit on, for example a different load or a different motion, and then on the robot.
5. **Randomize around the fitted values** during training, so the policy tolerates the differences that remain.

{: .note }
The actuator parameters in our [Robot Model (v1)]({{ '/simulation/robot-model/' | relative_url }}) come from static and swing tests on one 6512 and one 5010 actuator, fitted to a Coulomb + viscous friction model. That model fit well with a 2 kg load but noticeably worse with 5 kg. This is a sign of **load-dependent friction** in our 3D-printed gearbox, which the simple model can't capture.

## Approaches at a glance

| Approach | What it models | Data needed | Where to use it |
|:---------|:---------------|:------------|:----------------|
| [PD + joint parameters](#1-pd-control-with-joint-parameters) | Gains, torque limit, armature, Coulomb and viscous friction | Small (bench tests) | MuJoCo, mjlab, Isaac Lab |
| [DC motor model](#2-dc-motor-model) | Adds the torque-speed curve and electrical motor behavior | Small, plus motor datasheet | MuJoCo, mjlab, Isaac Lab |
| [Extended friction (BAM)](#3-extended-friction-models-bam) | Stribeck, load-dependent, and other friction effects | Medium (pendulum bench trajectories) | BAM |
| [Actuator network](#4-learned-actuator-networks) | Whatever the data shows, learned by a neural network | Large (real actuator or robot data) | Isaac Lab, mjlab |
| [Delta action model](#5-learning-the-gap-on-the-real-robot) | The remaining sim-to-real mismatch, learned from robot rollouts | Real-robot rollouts | Research code |

## 1. PD control with joint parameters

The simplest and most common approach. The actuator is an ideal PD controller with a torque limit, and the joint gets three physical parameters:

- **armature:** reflected rotor inertia, roughly rotor inertia × gear ratio²
- **frictionloss:** Coulomb (dry) friction
- **damping:** viscous friction

In MuJoCo, this is a `<position>` actuator (`kp`, `kv`, `forcerange`) with `armature`, `frictionloss`, and `damping` on the joint. In mjlab, it's `BuiltinPositionActuatorCfg`. This is what our Robot Model (v1) uses.

It's also what Unitree's open-source mjlab configs use: [unitree_rl_mjlab](https://github.com/unitreerobotics/unitree_rl_mjlab) sets position actuators with an armature computed from each motor's rotor inertia and planetary gear ratios. Berkeley Humanoid follows the same idea: rotor inertia from CAD, plus simple friction experiments on each actuator (Liao et al., 2024).

- **Pros:** few parameters, fast, easy to fit from a swing test.
- **Cons:** the Coulomb + viscous friction model is too simple for many real gearboxes (Duclusaud et al., 2024).

## 2. DC motor model

A real motor can't produce its full torque at high speed: the available torque drops along a **torque-speed curve**. DC motor models add this velocity-dependent torque limit, and some also model the motor's electrical side.

- **MuJoCo:** the native [`<dcmotor>`](https://mujoco.readthedocs.io/en/stable/XMLreference.html) actuator, available in recent versions (for example 3.16). It has parameters for the motor constant, resistance, inductance, saturation, cogging, thermal behavior, LuGre friction, and an actuation delay.
- **mjlab:** `DcMotorActuatorCfg`.
- **Isaac Lab:** `DCMotor`, which applies a four-quadrant DC motor torque-speed curve ([Isaac Lab actuators](https://isaac-sim.github.io/IsaacLab/main/source/api/lab/isaaclab.actuators.html)).

Disney Research's bipedal character uses custom actuator models with velocity-dependent torque limits, and also models **backlash** and encoder noise in the measured joint position (Grandia et al., 2025).

## 3. Extended friction models (BAM)

**BAM (Better Actuator Models)** from the Rhoban team extends the Coulomb + viscous model with effects like **Stribeck friction**, **load-dependent friction**, and quadratic terms. Parameters are identified from trajectories recorded on a **pendulum test bench**, the same kind of swing test described above.

It was validated on servo actuators (Dynamixel MX-64 and MX-106, eRob80:50 and eRob80:100) and showed clear accuracy improvements over the Coulomb + viscous model (Duclusaud et al., 2024). Because our gearbox shows load-dependent friction, this is worth trying.

- [BAM on GitHub](https://github.com/Rhoban/bam)
- Duclusaud et al., "[Extended Friction Models for the Physics Simulation of Servo Actuators](https://arxiv.org/abs/2410.08650)", 2024

## 4. Learned actuator networks

Instead of choosing equations, train a **neural network** that predicts the actuator's output torque from a short history of commands and joint states. The network is trained on data measured from the real actuator.

The ANYmal team at ETH Zurich's Robotic Systems Lab used this approach to train agile locomotion in simulation and transfer it to the real robot (Hwangbo et al., 2019). It captures effects that are hard to write down, such as delays and complex friction, but it needs a lot of data, and the network has to run inside the simulator.

- **Isaac Lab:** `ActuatorNetMLP` (uses a history of joint states) and `ActuatorNetLSTM` (a recurrent network).
- **mjlab:** `LearnedMlpActuatorCfg`.

## 5. Learning the gap on the real robot

A recent trend for humanoids: first train in simulation, then run the policy on the real robot, collect data, and learn a model of the remaining mismatch.

- **ASAP** trains a **delta (residual) action model** from real-world rollouts, which corrects the simulator so it behaves like the real robot. The policy is then fine-tuned with this corrected simulator. It reduced tracking error compared to system identification, domain randomization, and delta dynamics baselines on agile whole-body motions (He et al., 2025). [Code on GitHub](https://github.com/LeCAR-Lab/ASAP).

## Domain randomization

No actuator model is perfect, so policies are trained with the parameters **randomized** around their identified values. Common choices are Kp/Kd, motor strength, friction, armature, added mass, and action delay. Disney Research, for example, randomizes its actuator parameters within their experimentally observed range (Grandia et al., 2025).

Randomization makes a policy more robust, but too much can make it overly cautious. A good actuator model lets you use narrower ranges.

{: .note }
**Model latency, too.** Communication and control-loop delay between the computer, the CAN bus, and the motor drivers can matter as much as friction. Measure it, and add a delay of that size in simulation (Tan et al., 2018).

## What companies do

- **Boston Dynamics (electric Atlas):** uses only two types of rotary actuators, which they describe as "much easier to represent well in simulation", and reports a very small sim-to-real gap. The lesson is to design hardware so that it is easy to simulate ([Boston Dynamics blog](https://bostondynamics.com/blog/training-a-humanoid-robot-for-hard-work/)).
- **Unitree:** its public training code ([unitree_rl_gym](https://github.com/unitreerobotics/unitree_rl_gym), [unitree_rl_mjlab](https://github.com/unitreerobotics/unitree_rl_mjlab)) uses PD position actuators with physically derived armature, plus domain randomization of friction, mass, and pushes.
- **Disney Research:** bench-tests single actuators on a test bench that measures output torque, then models friction, torque-speed limits, and backlash, with randomization (Grandia et al., 2025).

## References

- Tan et al., "[Sim-to-Real: Learning Agile Locomotion For Quadruped Robots](https://arxiv.org/abs/1804.10332)", RSS 2018
- Hwangbo et al., "[Learning agile and dynamic motor skills for legged robots](https://arxiv.org/abs/1901.08652)", *Science Robotics*, 2019
- Liao et al., "[Berkeley Humanoid: A Research Platform for Learning-based Control](https://arxiv.org/abs/2407.21781)", 2024
- Duclusaud et al., "[Extended Friction Models for the Physics Simulation of Servo Actuators](https://arxiv.org/abs/2410.08650)", 2024
- Grandia et al., "[Design and Control of a Bipedal Robotic Character](https://arxiv.org/abs/2501.05204)", 2025
- He et al., "[ASAP: Aligning Simulation and Real-World Physics for Learning Agile Humanoid Whole-Body Skills](https://arxiv.org/abs/2502.01143)", RSS 2025
