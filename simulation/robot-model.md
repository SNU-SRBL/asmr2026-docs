---
title: Robot Model (v1)
parent: Simulation and Learning
nav_order: 1
permalink: /simulation/robot-model/
---

# Robot Model (v1)

The simulation model of our course robot, for **MuJoCo** and **mjlab**: a 12-joint biped with 6 joints per leg. It includes the robot geometry and a first set of actuator parameters.

<a href="{{ '/assets/downloads/asmr2026-humanoid-v1.zip' | relative_url }}" download class="btn btn-primary">Download ASMR2026 Humanoid v1 (ZIP, 10 MB)</a>

## What's inside

| File | Description |
|:-----|:------------|
| [`mjcf/asmr2026_humanoid.xml`]({{ '/assets/downloads/asmr2026-humanoid-v1/mjcf/asmr2026_humanoid.xml' | relative_url }}) | MuJoCo model with position actuators and sensors |
| [`mjcf/scene.xml`]({{ '/assets/downloads/asmr2026-humanoid-v1/mjcf/scene.xml' | relative_url }}) | The MuJoCo model on a ground plane |
| [`mjlab/asmr2026_humanoid_mjlab.xml`]({{ '/assets/downloads/asmr2026-humanoid-v1/mjlab/asmr2026_humanoid_mjlab.xml' | relative_url }}) | Same geometry without actuators; mjlab adds them from the config below |
| [`mjlab/asmr2026_humanoid_constants.py`]({{ '/assets/downloads/asmr2026-humanoid-v1/mjlab/asmr2026_humanoid_constants.py' | relative_url }}) | Actuator parameters and the mjlab robot config (`get_asmr2026_humanoid_cfg()`) |
| `meshes/` | Visual meshes (STL), in the ZIP only |
| [`README.md`]({{ '/assets/downloads/asmr2026-humanoid-v1/README.md' | relative_url }}) | Short overview of the package |

## Quick start

Unzip the package and open the model in the MuJoCo viewer:

```bash
pip install mujoco
python -m mujoco.viewer --mjcf=asmr2026-humanoid-v1/mjcf/scene.xml
```

For mjlab, use `get_asmr2026_humanoid_cfg()` from `asmr2026_humanoid_constants.py` as the robot in your task config. See the [mjlab]({{ '/simulation/mjlab/' | relative_url }}) page for mjlab itself.

{: .note }
For **Isaac Sim / Isaac Lab**, convert the model to USD yourself. See [Isaac Sim and Isaac Lab]({{ '/simulation/isaac-sim/' | relative_url }}).

## Frames and joints

- **Frame:** +X forward, +Y left, +Z up.
- **Joints**, per leg from hip to foot: `hip_roll`, `hip_yaw`, `hip_pitch`, `knee_pitch`, `ankle_pitch`, `ankle_roll`, named `leg_left_*_joint` and `leg_right_*_joint`.
- **IMU:** the `imu` site.
- **Feet:** the sole boxes `left_foot_collision` and `right_foot_collision`, with sites `left_foot` and `right_foot`.

## Actuator parameters

| Joints | Actuator | Kp | Kd | Torque limit | Armature | Friction (static / viscous) |
|:-------|:---------|---:|---:|---:|---:|:---|
| hip roll, hip yaw, hip pitch, knee pitch | 6512 | 90.01 | 5.730 | 18.09 N·m | 0.0228 kg·m² | 0.377 N·m / 0.090 N·m·s/rad |
| ankle pitch, ankle roll | 5010 | 21.95 | 0.489 | 22.57 N·m | 0.00556 kg·m² | 0.317 N·m / 0.030 N·m·s/rad |

Armature and friction were fitted from bench tests on a single actuator of each type. Kp and Kd are derived from the armature with a 10 Hz natural frequency and a damping ratio of 2.0 (hip and knee) or 0.7 (ankle). The torque limit comes from the motor driver's 18 A current limit.

{: .warning }
> These parameters **may not be accurate** for your robot.
> We recommend running your own experiments on your real actuators and building your own **actuator model**. For example, the ANYmal team at ETH Zurich's Robotic Systems Lab trained a **neural network** that maps actuator commands to output torque from real measurements: Hwangbo et al., "[Learning agile and dynamic motor skills for legged robots](https://arxiv.org/abs/1901.08652)", *Science Robotics*, 2019.
>
> See [Actuator Modeling]({{ '/simulation/actuator-modeling/' | relative_url }}) for methods you can use.

## Versions

| Version | Date | Notes |
|:--------|:-----|:------|
| v1 | 2026-10-16 | First release |

## Copyright

Copyright © 2026 Seunghoon Kang, Soft Robotics and Bionics Laboratory (SRBL), Department of Mechanical Engineering, Seoul National University. All rights reserved.
Provided for use in the 2026-2 Actuation and Sensing Mechanism Design for Robots course.
{: .fs-2 .text-grey-dk-000 }
