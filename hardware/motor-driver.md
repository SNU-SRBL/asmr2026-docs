---
title: Motor Driver
parent: Robot Hardware
nav_order: 3
permalink: /hardware/motor-driver/
---

# Motor Driver Guide

Our robot uses the **XDrive MINI** motor driver board from Makerbase (MKS) in place of the motor controller used by the original Berkeley Humanoid Lite. The XDrive MINI is based on **ODrive v3.6** and has an on-board AS5047P encoder.

<img src="{{ '/assets/images/hardware/xdrive-mini.png' | relative_url }}" alt="XDrive MINI motor driver board, with green screw terminal blocks for motor phases A, B, C and DC power, five capacitors, and connectors along the bottom edge." style="max-width: 240px; width: 100%;">

XDrive MINI (image: Makerbase)
{: .fs-2 .text-grey-dk-000 }

- [XDrive MINI product page (Makerbase)](https://makerbase3d.com/product/makerbase-xdrive-mini-high-precision-brushless-servo-motor-controller-based-on-odrive3-6-with-as5047p-on-board/)

{: .note }
Changing the driver board also changed some actuator parts. See [What's different from Berkeley Humanoid Lite]({{ '/hardware/actuator-assembly/' | relative_url }}#whats-different-from-berkeley-humanoid-lite) on the actuator assembly page.

## Official documentation and resources

- **[ODrive documentation (v0.5.6): Getting Started](https://docs.odriverobotics.com/v/0.5.6/getting-started.html)**: the official ODrive documentation for the ODrive v3.6 generation, which the XDrive MINI is based on.
- **[MKS ODrive video playlist (YouTube)](https://www.youtube.com/playlist?list=PLc2RScfrSFEDcQp6Qvc7mBNre8ABCoz9p)**: Makerbase's official tutorial videos for their ODrive-based boards, covering the important setup steps.
- **[MKS ODrive GitHub repository](https://github.com/makerbase-mks/ODrive-MKS)**: Makerbase's repository with the original firmware. The XDrive MINI firmware is in the [`Firmware/MKS ODrive_S`](https://github.com/makerbase-mks/ODrive-MKS/tree/main/Firmware/MKS%20ODrive_S) folder.

## Community project: MKS-XDRIVE-MINI

A community member has made a guide project for the XDrive MINI, with configuration instructions using the ODrive tool, firmware files, and troubleshooting tips, for example for running several drivers on one CAN bus. It's a great place to start trying out and playing with the motor driver.

- [Video (YouTube)](https://www.youtube.com/watch?v=yRx7dsJmNvU)
- [GitHub repository: MKS-XDRIVE-MINI](https://github.com/justlovescience/MKS-XDRIVE-MINI)

{: .note }
> We recommend using this project to get comfortable with the motor driver before building the full robot. Practice:
> - using `odrivetool`
> - flashing firmware
> - setting up the motor driver configuration
> - running CAN communication

## Course firmware (recommended)

For the project, we recommend using our **modified firmware** for the XDrive MINI:

[xdrive-mini-fw-instant-start (GitHub)](https://github.com/omletkang/xdrive-mini-fw-instant-start){: .btn .btn-primary }

It is a modified version of the MKS ODrive v0.5.1 firmware. The XDrive MINI's on-board AS5047P is an absolute encoder, but the stock firmware still runs the encoder offset calibration again at every power-on. We modified the firmware so that the driver:

- **skips the encoder offset calibration** at power-on, after a one-time calibration
- **starts from any rotor position** and goes straight into closed-loop control, without jumping

To use it:

1. Download the `.hex` or `.elf` file from the repository's [Releases](https://github.com/omletkang/xdrive-mini-fw-instant-start/releases) page.
2. Flash it to the XDrive MINI (see [Flashing firmware](#flashing-firmware) below).
3. Configure the driver with the ODrive tool using `xdrive_config.txt` from the repository, which includes the one-time calibration.

See the repository's README for the details of what was changed and how to configure the driver.

## Flashing firmware

If your firmware is a `.bin`, `.hex`, or `.elf` file, we recommend **STM32CubeProgrammer** from STMicroelectronics to flash it quickly.

[STM32CubeProgrammer (STMicroelectronics)](https://www.st.com/en/development-tools/stm32cubeprog.html){: .btn }
