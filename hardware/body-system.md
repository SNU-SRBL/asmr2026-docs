---
title: Body System
parent: Robot Hardware
nav_order: 5
permalink: /hardware/body-system/
---

# Body System

Besides the actuators, the robot's body carries an on-board computer and a battery that powers everything.

## Single-board computer

The baseline on-board computer for the robot is the **Radxa ROCK 3C** single-board computer.

- [Radxa ROCK 3C product page](https://radxa.com/products/rock3/3c/)
- [Radxa ROCK 3C documentation](https://docs.radxa.com/en/rock3/rock3c)

### Setting up the board

An SD card for the OS is provided in the course.

1. **Before you start:** read the [ROCK 3C getting started guide](https://docs.radxa.com/en/rock3/rock3c/getting-started/before-start) in the Radxa documentation.
2. **Download the OS image** from the [ROCK 3C OS images](https://docs.radxa.com/en/rock3/images?model=ROCK+3C) page. We recommend **Rock3C-Debian12-Bookworm-kde-b1.img**. The downloaded file is named `rock-3c_bookworm_kde_b1.output_512.img.xz`.
3. **Write the image to the SD card and boot the board.** The [Radxa wiki getting started page](https://wiki.radxa.com/Rock3/3c/getting_started) has easy-to-follow step-by-step instructions.

<!-- TA: add course-specific setup notes for the ROCK 3C (connection to the USB-to-CAN adapter, etc.). -->

### Alternative: NVIDIA Jetson Orin Nano

Teams can also use an **NVIDIA Jetson Orin Nano** as the on-board computer instead of the ROCK 3C. See NVIDIA's official pages:

- [Jetson Orin Nano Developer Kit (NVIDIA)](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/)
- [Jetson Orin Nano Developer Kit quick start guide (NVIDIA)](https://docs.nvidia.com/jetson/orin-nano-devkit/user-guide/latest/quick_start.html)

## Battery and power circuit

The robot uses **two separate batteries**: a 24 V battery for the motor drivers, and a 12 V battery for the computer and the control circuit.

<img src="{{ '/assets/images/body-system/battery-system.png' | relative_url }}" alt="Battery system diagram. The 24 V power battery (two batteries) connects to the 12 actuators through a diode and a normally open power relay placed in parallel. The 12 V power battery feeds a 12 V to 24 V DC/DC converter, whose output drives the power relay through an emergency stop button, and also powers the computer. The computer communicates with the actuators through a USB-to-CAN adapter." style="max-width: 800px; width: 100%;">

Battery system. Thick lines: power. Thin lines: logic. Green lines: communication.
{: .fs-2 .text-grey-dk-000 }

### 24 V: motor power

The **24 V battery** (two batteries in parallel) powers the **12 motor drivers**. On the way, the power line passes through a **Schottky barrier diode** and a **power relay (normally open)**, which are connected in parallel.

### 12 V: control power

The **12 V battery** is split two ways:

1. **Relay control:** through a **12 V → 24 V DC/DC converter (booster)** to the power relay's signal line. The **emergency stop** button is on this line.
2. **Computer:** to the single-board computer.

{: .note }
If your single-board computer runs on **5 V**, you need a separate voltage regulator for it.

### Layout in the body

The body frame has several floors:

| Position | Components |
|:---------|:-----------|
| Top (third) floor | 12 V → 24 V booster, computer |
| Second floor | 12 V battery, diode, power relay, emergency stop button |
| First floor | 24 V batteries (two, in parallel) |
| Bottom | IMU |

<img src="{{ '/assets/images/body-system/body-assembly.png' | relative_url }}" alt="CAD model of the robot's body: an aluminum extrusion frame with several floors holding the computer and booster at the top, the power relay and other components on the middle floor, the batteries below, and the IMU mounted at the bottom." style="max-width: 480px; width: 100%;">

CAD model of the body assembly.
{: .fs-2 .text-grey-dk-000 }

### Reference: MEVITA

For reference, see the hardware documentation of **MEVITA**, an open-source bipedal robot:

- [MEVITA hardware](https://haraduka.github.io/mevita-hardware/)
