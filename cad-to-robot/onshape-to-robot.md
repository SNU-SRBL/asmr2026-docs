---
title: Onshape-to-Robot
parent: From CAD to Robot
nav_order: 2
permalink: /cad-to-robot/onshape-to-robot/
---

# Onshape-to-Robot Guide

**onshape-to-robot** is a tool that exports a robot designed in Onshape to robot description formats that simulators can load, such as URDF, SDF, and MuJoCo (MJCF).

<img src="{{ '/assets/images/cad/onshape-to-robot-overview.png' | relative_url }}" alt="Overview diagram: a robot designed in Onshape, with an arrow pointing to the same robot exported and loaded in four simulators: URDF in PyBullet, MuJoCo, SDF in Gazebo, and URDF in Meshcat." style="max-width: 800px; width: 100%;">

From an Onshape design to URDF, SDF, and MuJoCo (image: onshape-to-robot documentation)
{: .fs-2 .text-grey-dk-000 }

## Official resources

- [onshape-to-robot documentation](https://onshape-to-robot.readthedocs.io/en/latest/)
- [onshape-to-robot on GitHub](https://github.com/rhoban/onshape-to-robot)

## Example: Berkeley Humanoid Lite

Berkeley Humanoid Lite uses onshape-to-robot to generate its robot description files. Their scripts are a very useful example of how to use onshape-to-robot in practice from a Python program:

[Berkeley Humanoid Lite Assets: scripts (GitHub)](https://github.com/HybridRobotics/berkeley-humanoid-lite-assets/tree/fc90fedd008b1e56a22e3c5221548d6b24f49707/scripts){: .btn .btn-primary }

| Script | What it does |
|:-------|:-------------|
| `export_onshape_to_urdf.py` | Exports the Onshape CAD model to URDF |
| `export_onshape_to_mjcf.py` | Exports the Onshape CAD model to MJCF (MuJoCo) |
| `convert_urdf_to_usd.py` | Converts the URDF to USD |

The export scripts run onshape-to-robot with a `config.json` file that describes the export settings.

<!-- TA: add course-specific steps for exporting your team's robot. -->
