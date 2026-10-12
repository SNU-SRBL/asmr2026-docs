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

This is a project-based course in which students work in teams to build and program a bipedal humanoid robot. The course provides guides, hardware components, firmware, and starter software; teams use these resources to complete the project and gain hands-on experience in:

- **Hardware:** Building 3D-printed quasi-direct-drive actuators and assembling the robot, including its computer, battery, and power circuits.
- **Electronics and firmware:** Working with CAN communication and motor-driver firmware, including field-oriented control (FOC) and torque control.
- **Low-level software:** Understanding and adapting the runtime software that operates the humanoid.
- **Robot learning:** Training a locomotion policy with reinforcement learning in simulation, transferring it to the real robot, and developing a team-designed task.

## The humanoid robot project

Since 2024, the course has included a team project to build a humanoid robot. This semester, teams build a **modified bipedal version of [Berkeley Humanoid Lite]({{ '/start-here/berkeley-humanoid-lite/' | relative_url }})** and then use their robot to carry out a task of their own design.

### Make it your own

You don't need to follow the course robot platform exactly. Teams are welcome to improve the humanoid, for example by adding sensors such as encoders, IMUs, or cameras, and to train new policies so the robot can do new tasks.

Examples of team ideas this semester:

- A bipedal robot that takes photos with a camera on its head
- A firefighting bipedal robot that puts out a real fire
