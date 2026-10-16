---
title: mjlab
parent: Simulation and Learning
nav_order: 4
permalink: /simulation/mjlab/
---

# mjlab

**mjlab** is a robot learning framework that combines [Isaac Lab](https://github.com/isaac-sim/IsaacLab)'s manager-based API with **MuJoCo Warp**, a GPU-accelerated version of the MuJoCo physics simulator. It provides building blocks for designing environments and training policies, with minimal dependencies and direct access to MuJoCo's data structures.

- [mjlab on GitHub](https://github.com/mujocolab/mjlab)
- [mjlab documentation](https://mujocolab.github.io/mjlab/)

{: .important }
mjlab needs an NVIDIA GPU for training. macOS is supported for evaluation only.

## Try it

You can try the mjlab demo without installing anything:

```bash
uvx --from mjlab --refresh demo
```

Or run it in [Google Colab](https://colab.research.google.com/github/mujocolab/mjlab/blob/main/notebooks/demo.ipynb), with no local setup.

## Example: Unitree RL Mjlab

**Unitree RL Mjlab** is Unitree's reinforcement learning project built on mjlab, supporting robots such as the Unitree G1 and H1_2. It's a useful example of the whole workflow, from training a policy in simulation to deploying it on a real robot:

**Train** → **Play** (replay the trained policy in simulation) → **Sim2Real** (deploy it on the real robot)

[Unitree RL Mjlab (GitHub)](https://github.com/unitreerobotics/unitree_rl_mjlab){: .btn .btn-primary }

## MuJoCo

mjlab is built on **MuJoCo**, an open-source physics engine widely used in robotics research.

- [MuJoCo website](https://mujoco.org)
- [MuJoCo documentation](https://mujoco.readthedocs.io/en/stable/overview.html)
- [MuJoCo Warp on GitHub](https://github.com/google-deepmind/mujoco_warp)

<!-- TA: add course-specific mjlab setup notes here. -->
