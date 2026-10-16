---
title: Home
layout: home
nav_order: 1
description: Course guide and project materials for ASMR 2026 (Actuation and Sensing Mechanism Design for Robots).
permalink: /
---

# Build a humanoid, teach it to walk
{: .fs-9 }

Course guide and project materials for **2026-2 Actuation and Sensing Mechanism Design for Robots (001)**.
{: .fs-6 .fw-300 }

[Start here](start-here/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Go to eTL]({{ site.etl_url }}){: .btn .fs-5 .mb-4 .mb-md-0 }

---

{: .important }
> **eTL is the official channel.** Course notices, homework, and presentation submissions are handled on [eTL]({{ site.etl_url }}).
> This site is a guide and materials portal. If anything here conflicts with eTL, follow eTL.

## The project

Over the semester you will:

1. **Assemble** a bipedal humanoid robot, a modified version of the open-source [Berkeley Humanoid Lite](start-here/berkeley-humanoid-lite/).
2. **Model** the robot and its actuators so it can be simulated.
3. **Train** a walking policy with reinforcement learning in simulation.
4. **Transfer** the policy from simulation to the real robot (sim-to-real).
5. **Carry out** a task of your team's own design.

## Where to find things

| Section | What's inside |
|:--------|:--------------|
| [Start Here](start-here/) | Course introduction and the Berkeley Humanoid Lite reference |
| [Robot Hardware](hardware/) | Bill of materials, actuator assembly, motor driver, USB-to-CAN adapter, body system, low-level software, full robot assembly |
| [From CAD to Robot](cad-to-robot/) | Onshape CAD and converting it to a robot description |
| [Simulation and Learning](simulation/) | Robot model (MuJoCo / mjlab), actuator modeling, Isaac Sim and Isaac Lab, mjlab, real robot safety |
| [References](references/) | References for the course project |
| [Downloads and Versions](downloads/) | Released files (part files and the robot model) and their version history |
| [Help](help/) | Where to ask questions and how to report problems with this site |

## Material status

Materials are published as the course progresses. Sections marked
<span class="label label-blue">Partly available</span> are usable but still being expanded.

| Section | Status |
|:--------|:-------|
| [Start Here](start-here/) | <span class="label label-green">Available</span> |
| [Robot Hardware](hardware/) | <span class="label label-green">Available</span> |
| [From CAD to Robot](cad-to-robot/) | <span class="label label-green">Available</span> |
| [Simulation and Learning](simulation/) | <span class="label label-green">Available</span> |
| [References](references/) | <span class="label label-blue">Partly available</span> |

## Gallery

The humanoid robots built by previous classes of this course.

<div style="display: flex; flex-wrap: wrap; gap: 1rem;">
  <figure style="flex: 1 1 280px; margin: 0; min-width: 0;">
    <img src="{{ '/assets/images/home/asmr-2024.jpg' | relative_url }}" alt="ASMR 2024: students and Professor Yong-Lae Park gathered around the class's humanoid robot during a demo in the lab." style="width: 100%; aspect-ratio: 4 / 3; object-fit: cover; border-radius: 8px;">
    <figcaption class="fs-2 text-grey-dk-000">ASMR 2024</figcaption>
  </figure>
  <figure style="flex: 1 1 280px; margin: 0; min-width: 0;">
    <img src="{{ '/assets/images/home/asmr-2025.jpg' | relative_url }}" alt="ASMR 2025: students and Professor Yong-Lae Park posing with the class's humanoid robot, which holds drumsticks and a drum." style="width: 100%; aspect-ratio: 4 / 3; object-fit: cover; border-radius: 8px;">
    <figcaption class="fs-2 text-grey-dk-000">ASMR 2025</figcaption>
  </figure>
</div>
