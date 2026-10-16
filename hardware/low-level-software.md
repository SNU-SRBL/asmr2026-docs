---
title: Low-Level Software
parent: Robot Hardware
nav_order: 6
permalink: /hardware/low-level-software/
---

# Low-Level Software

The **low-level program** runs on the robot's on-board computer (see [Body System]({{ '/hardware/body-system/' | relative_url }})) and connects everything:

- talks to the 12 motor drivers over **CAN**, through the [USB-to-CAN adapter]({{ '/hardware/usb-can-adapter/' | relative_url }})
- reads the joint states and the **IMU**
- receives user commands, for example from a joystick
- runs your trained **policy** and sends the joint targets to the motor drivers

You will write your team's own low-level program. The two projects below are good references.

## Berkeley Humanoid Lite low-level control

The low-level control code of Berkeley Humanoid Lite, our robot's base. It's very helpful as a starting point for your own program. It covers:

- bringing up the CAN interface and checking the connection to every joint
- receiving joystick commands
- calibrating the joint zero positions
- running the main controller with a trained policy

[berkeley-humanoid-lite-lowlevel (GitHub)](https://github.com/HybridRobotics/berkeley-humanoid-lite-lowlevel){: .btn .btn-primary }

{: .important }
Berkeley Humanoid Lite uses a different motor controller. Our [XDrive MINI]({{ '/hardware/motor-driver/' | relative_url }}) uses the **ODrive CAN protocol**, so adapt the motor communication part of the code. See [CAN communication with the XDrive MINI](#can-communication-with-the-xdrive-mini) below.

## CAN communication with the XDrive MINI

The XDrive MINI firmware speaks ODrive's **CAN Simple** protocol. Each CAN message ID combines the motor driver's **node ID** (upper 6 bits) with a **command ID** (lower 5 bits), for example heartbeat, set position, or get encoder estimates.

To write the CAN library on the computer side, use the motor-driver-side code as a reference. It is in Makerbase's firmware source, **`ODrive_S-fw-v0.5.1.zip`**, in the [`Firmware/MKS ODrive_S`](https://github.com/makerbase-mks/ODrive-MKS/tree/main/Firmware/MKS%20ODrive_S) folder of the MKS ODrive repository:

| File in the ZIP | What it is |
|:----------------|:-----------|
| `docs/can-protocol.md` | The CAN protocol for this firmware version: frame format, message IDs, and signals |
| `Firmware/communication/can_simple.cpp`, `can_simple.hpp` | How the motor driver handles each CAN message |
| `tools/odrive/tests/can_test.py` | A Python test script that sends CAN messages to the driver |

{: .note }
The XDrive MINI firmware is based on **ODrive v0.5.1**, so `docs/can-protocol.md` in the ZIP matches it exactly. The online [ODrive CAN protocol (v0.5.6)](https://docs.odriverobotics.com/v/0.5.6/can-protocol.html) is a newer version and may differ in some messages.

## MEVITA

MEVITA's repository includes its software, built on **ROS**. It's a useful reference if your team wants to add **sensors such as a camera or LiDAR** and use ROS. For example, MEVITA uses a Livox LiDAR with optional FAST-LIO odometry.

[MEVITA (GitHub)](https://github.com/haraduka/mevita){: .btn }

{: .warning }
Before running any policy on the robot, read [Real Robot Safety]({{ '/simulation/real-robot-safety/' | relative_url }}).
