---
title: Actuator Assembly
parent: Robot Hardware
nav_order: 2
permalink: /hardware/actuator-assembly/
---

# Actuator Assembly Guide

We build the robot's 3D-printed actuators by following the official [Berkeley Humanoid Lite documentation](https://berkeley-humanoid-lite.gitbook.io/docs). This page shows which upstream pages to use, and where our course version differs.

## What's different from Berkeley Humanoid Lite

Our actuators use a different motor driver board: the **XDrive MINI** from Makerbase, which is based on ODrive v3.6 and has an on-board AS5047P encoder. See the [Motor Driver]({{ '/hardware/motor-driver/' | relative_url }}) page for details.

Because of the new driver board, a few parts are changed or added:

- **Magnet extender** (new): a small cylinder, 6 mm in diameter, placed between the motor shaft and the rotary magnet. It brings the magnet closer to the encoder on the back of the driver board, reducing the air gap between them. Its height depends on the actuator:
  - **6512 actuator:** 6 mm
  - **5010 actuator:** 3 mm
- **Driver board spacer** (new): a spacer between the steel heat plate and the driver board.
- **Motor shell v2** (modified): our modified version of the motor shell. Use it in place of the upstream motor shell.

<!-- IMAGE: driver board spacer between the heat plate and the driver board -->

## Course part files

| Part | Actuator | File |
|:-----|:---------|:-----|
| Magnet extender (6 mm) | 6512 | <a href="{{ '/assets/downloads/actuator/magnet-extend-6mm.stl' | relative_url }}" download>magnet-extend-6mm.stl</a> |
| Magnet extender (3 mm) | 5010 | <a href="{{ '/assets/downloads/actuator/magnet-extend-3mm.stl' | relative_url }}" download>magnet-extend-3mm.stl</a> |
| Motor shell v2 | 6512 | <a href="{{ '/assets/downloads/actuator/motor-shell-v2-6512.step' | relative_url }}" download>motor-shell-v2-6512.step</a> |
| Motor shell v2 | 5010 | <a href="{{ '/assets/downloads/actuator/motor-shell-v2-5010.step' | relative_url }}" download>motor-shell-v2-5010.step</a> |
| Driver board spacer | 6512, 5010 | <a href="{{ '/assets/downloads/actuator/driver-board-spacer.stl' | relative_url }}" download>driver-board-spacer.stl</a> |

## 1. Get the 3D print files

{: .important }
This step covers the **actuators only**. Files and instructions for the rest of the robot body are in the [Full Robot Assembly]({{ '/hardware/robot-assembly/' | relative_url }}) guide.

On the upstream **Releases** page, under *3D Printing Project Files*, get the files for the **6512 Actuator** and the **5010 Actuator**. Then replace the upstream motor shell with our **motor shell v2**, and add the **magnet extender** and **driver board spacer** from the table above.

[Berkeley Humanoid Lite: Releases](https://berkeley-humanoid-lite.gitbook.io/docs/releases){: .btn .btn-primary }

## 2. Print the parts

Follow the upstream **3D Printing Instructions** for print settings. The actuator parts use specific print profiles, so check which profile each part needs.

[Berkeley Humanoid Lite: 3D Printing Instructions](https://berkeley-humanoid-lite.gitbook.io/docs/getting-started-with-hardware/3d-printing-instructions){: .btn }

<!-- TA: add print settings for the magnet extender and driver board spacer if they differ from upstream. -->

## 3. Build the actuator

Follow the upstream **Building the Actuator** guide to assemble the actuator, with the changes below.

[Berkeley Humanoid Lite: Building the Actuator](https://berkeley-humanoid-lite.gitbook.io/docs/getting-started-with-hardware/building-the-actuator){: .btn }

{: .warning }
**Skip "Preparing the magnetic encoder"** in the upstream guide. That step is for the original AS5600 encoder board. The XDrive MINI has its own on-board AS5047P encoder.

### Mounting the magnet

Place the **magnet extender** between the motor shaft and the rotary magnet. You can attach the extender to the shaft, and the magnet to the extender, with double-sided tape or a hot glue gun. The diagram below shows the stacking order, from the driver board down to the motor, for each actuator.

![Side view of the stacking order for the 6512 and 5010 actuators. From top to bottom: XDrive driver board, encoder on the back of the board, rotary magnet (2 mm tall), magnet extender (6 mm tall for the 6512, 3 mm tall for the 5010), and motor.]({{ '/assets/images/actuator/image_magnet_extend_guide.png' | relative_url }})

Side view, not to scale. Left: 6512 actuator with the 6 mm magnet extender. Right: 5010 actuator with the 3 mm magnet extender. The magnet in this diagram is 2 mm tall.
{: .fs-2 .text-grey-dk-000 }

{: .important }
> The rotary magnet that comes with the XDrive MINI is **6 mm in diameter and 2.5 mm tall**, slightly taller than the 2 mm magnet in the diagram. Magnet dimensions can vary, so **measure your magnet before assembling**.
>
> Make sure the air gap between the magnet and the encoder stays within **0.5–3 mm**, as we recommend.

<img src="{{ '/assets/images/actuator/20260727_220649_IMG.jpg' | relative_url }}" alt="Close-up of the motor shaft through the center opening of the motor mount, with the magnet extender and the rotary magnet attached on top of the shaft." style="max-width: 240px; width: 100%;">

The magnet extender and rotary magnet attached to the motor shaft.
{: .fs-2 .text-grey-dk-000 }

### Assembled actuator

The assembled actuator, seen from the driver board side:

<div style="display: flex; flex-wrap: wrap; gap: 1rem; align-items: flex-start;">
  <img src="{{ '/assets/images/actuator/20260617_170101_IMG.jpg' | relative_url }}" alt="Top view of an assembled actuator, with the XDrive MINI driver board mounted on the back of the actuator and the motor and power wires connected to its terminal blocks." style="flex: 1 1 280px; max-width: 100%; min-width: 0;">
  <img src="{{ '/assets/images/actuator/20260617_170110_IMG.jpg' | relative_url }}" alt="Angled view of an assembled actuator, showing the XDrive MINI driver board mounted on top of the 3D-printed actuator housing." style="flex: 1 1 220px; max-width: 100%; min-width: 0;">
</div>

<!-- IMAGE / TA: more course-specific assembly steps (driver board spacer, motor shell v2). -->

### Soldering the wires

The XDrive MINI comes with screw terminal blocks, as in the photos above. Terminal blocks are fine for testing a single actuator, but for the full robot you need to **remove them and solder the wires directly to the board**.

#### Tools

- **Long-nose pliers**
- **Magnetic PCB holder**: a steel base plate with neodymium magnetic posts that hold the board in place while you solder
- **Soldering iron** and solder

<div style="display: flex; flex-wrap: wrap; gap: 1rem; align-items: flex-end;">
  <img src="{{ '/assets/images/actuator/tool-long-nose-pliers.jpg' | relative_url }}" alt="Long-nose pliers." style="flex: 0 1 180px; max-width: 100%; min-width: 0;">
  <img src="{{ '/assets/images/actuator/tool-magnetic-pcb-holder.jpg' | relative_url }}" alt="Magnetic PCB holder: a steel base plate with four magnetic posts holding a circuit board above it." style="flex: 0 1 240px; max-width: 100%; min-width: 0;">
</div>

Left: long-nose pliers. Right: magnetic PCB holder.
{: .fs-2 .text-grey-dk-000 }

#### 1. Remove the terminal blocks

Fix the driver board in the magnetic PCB holder. Hold the terminal block with the long-nose pliers, and heat its solder joints with the soldering iron until the block comes off the board.

<img src="{{ '/assets/images/actuator/terminal-block-removal.jpg' | relative_url }}" alt="Back of the XDrive MINI driver board held in a magnetic PCB holder. A soldering iron heats the terminal block's solder joints while long-nose pliers hold the removed terminal block." style="max-width: 480px; width: 100%;">

Removing the terminal block at the soldering station.
{: .fs-2 .text-grey-dk-000 }

#### 2. Solder the wires

Solder the wires directly to the pads where the terminal blocks were:

- **A, B, C:** the three BLDC motor phase wires
- **DC +, DC −:** the power wires

<div style="display: flex; flex-wrap: wrap; gap: 1rem; align-items: flex-start;">
  <img src="{{ '/assets/images/actuator/soldered-wires-front.jpg' | relative_url }}" alt="XDrive MINI driver board with the terminal blocks removed. Three black motor phase wires are soldered to pads A, B, and C, and red and black power wires to DC plus and minus." style="flex: 1 1 260px; max-width: 100%; min-width: 0;">
  <img src="{{ '/assets/images/actuator/soldered-wires-angle.jpg' | relative_url }}" alt="Angled view of an assembled actuator with motor and power wires soldered directly to the driver board, connected to a bench power supply." style="flex: 1 1 260px; max-width: 100%; min-width: 0;">
</div>

Examples of finished actuators with the wires soldered directly to the board.
{: .fs-2 .text-grey-dk-000 }

#### 3. Secure the wires

To keep the wiring tidy and stop the solder joints from being strained, we recommend fixing the wires to the board with a **hot glue gun**, as shown below.

<img src="{{ '/assets/images/actuator/soldered-wires-hot-glue.jpg' | relative_url }}" alt="Actuator mounted in the robot leg, with the motor and power wires fixed to the driver board with hot glue over the solder joints." style="max-width: 320px; width: 100%;">

Wires fixed to the board with hot glue, on an actuator mounted in the robot.
{: .fs-2 .text-grey-dk-000 }
