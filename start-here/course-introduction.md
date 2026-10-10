---
title: Course Introduction
parent: Start Here
nav_order: 1
permalink: /start-here/course-introduction/
---

# Course Introduction

## Course information

| | |
|:--|:--|
| **Course** | Actuation and Sensing Mechanism Design for Robots (001) |
| **Semester** | 2026-2 |
| **Department** | Mechanical Engineering, Seoul National University |
| **Level** | Graduate |
| **Instructor** | Prof. Yong-Lae Park |
| **Teaching assistant** | Seunghoon Kang ([alaska97@snu.ac.kr](mailto:alaska97@snu.ac.kr)) |

{: .important }
Course notices, homework, and presentation submissions are on [eTL]({{ site.etl_url }}). If anything on this site conflicts with eTL, follow eTL.

## About the course

In this course, you will build a bipedal humanoid robot as a team:

- **Hardware:** build 3d-printed quasi-direct-drive actuators, then the full robot structure, including the computer and the battery and power circuits.
- **Electronics and firmware:** understand CAN communication and motor driver firmware, such as field-oriented control (FOC) and torque control.
- **Low-level software:** understand the low-level runtime program that runs the humanoid.
- **Robot Learning:** learn reinforcement learning in simulation, train your own locomotion policy, and make your humanoid walk in the real world, carrying out your team's own idea.

{: .note }
For the lecture schedule and all course announcements, follow the notices on [eTL]({{ site.etl_url }}).

## The humanoid robot project

Since 2024, the course has included a team project to build a humanoid robot. This semester, teams build a **modified bipedal version of [Berkeley Humanoid Lite]({{ '/start-here/berkeley-humanoid-lite/' | relative_url }})**:

1. **Build the actuators** that drive the robot's joints.
2. **Build the full structure** of the bipedal humanoid.
3. **Train a locomotion policy** with reinforcement learning in simulation and transfer it to the real robot so it walks.
4. **Make the robot do a task** of your team's own design.

### What the course provides

The course provides skeleton materials to build on:

- **Guides** for each stage of the project (on this site)
- **Hardware** for the robot platform
- **Firmware**, such as for the motor driver board
- **Software**, such as low-level runtime code and a CAN library

### Make it your own

You don't need to follow the course robot platform exactly. Teams are welcome to improve the humanoid, for example by adding sensors such as encoders, IMUs, or cameras, and to train new policies so the robot can do new tasks.

Examples of team ideas this semester:

- A bipedal robot that takes photos with a camera on its head
- A firefighting bipedal robot that puts out a real fire
