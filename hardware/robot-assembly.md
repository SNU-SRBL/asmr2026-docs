---
title: Full Robot Assembly
parent: Robot Hardware
nav_order: 7
permalink: /hardware/robot-assembly/
---

# Full Robot Assembly

Once your [actuators]({{ '/hardware/actuator-assembly/' | relative_url }}) are built, print the leg structure parts, then assemble the legs and the body into the full robot.

<img src="{{ '/assets/images/robot-assembly/full-robot.png' | relative_url }}" alt="The fully assembled course robot: an aluminum-frame body holding the batteries, power relay, and electronics, on top of two legs built from orange and black 3D-printed actuators and structure parts, standing on flat feet." style="max-width: 320px; width: 100%;">

The fully assembled robot.
{: .fs-2 .text-grey-dk-000 }

## 1. Print the leg structure parts

Download the STL files for the leg structure and print them. For print settings, see *Printing the rest of the robot* in the upstream [3D Printing Instructions](https://berkeley-humanoid-lite.gitbook.io/docs/getting-started-with-hardware/3d-printing-instructions).

<a href="{{ '/assets/downloads/leg-structure-stl.zip' | relative_url }}" download class="btn btn-primary">Download all leg structure parts (ZIP)</a>

Parts marked **L** or **R** are for the left or right leg. Parts without a side label are symmetric or single-shape parts that can be used on either leg.

| Part | Side | File |
|:-----|:-----|:-----|
| 6512 Housing Hip – Housing Middle | — | <a href="{{ '/assets/downloads/leg-structure/6512-Housing-Hip_Housing-Middle.stl' | relative_url }}" download>STL</a> |
| 6512 Housing 6512 – UpperLeg X Housing Middle | — | <a href="{{ '/assets/downloads/leg-structure/6512-Housing-6512_UpperLeg-X-Housing-Middle.stl' | relative_url }}" download>STL</a> |
| 6512 Housing Knee – Housing Middle | L | <a href="{{ '/assets/downloads/leg-structure/6512-Housing-Knee_Housing-Middle-L.stl' | relative_url }}" download>STL</a> |
| 6512 Housing Knee – Housing Middle | R | <a href="{{ '/assets/downloads/leg-structure/6512-Housing-Knee_Housing-Middle-R.stl' | relative_url }}" download>STL</a> |
| 6512 Housing Knee – Rear Struct | L | <a href="{{ '/assets/downloads/leg-structure/6512-Housing-Knee_Rear-Struct-L.stl' | relative_url }}" download>STL</a> |
| 6512 Housing Knee – Rear Struct | R | <a href="{{ '/assets/downloads/leg-structure/6512-Housing-Knee_Rear-Struct-R.stl' | relative_url }}" download>STL</a> |
| 6512 Rear Cover – Rear Struct | — | <a href="{{ '/assets/downloads/leg-structure/6512-Rear-Cover_Rear-Struct.stl' | relative_url }}" download>STL</a> |
| 5010 Housing Ankle – Ankle Mount 1 | — | <a href="{{ '/assets/downloads/leg-structure/5010-Housing-Ankle_Ankle-Mount-1.stl' | relative_url }}" download>STL</a> |
| 5010 Housing Ankle – Ankle Mount 2 | — | <a href="{{ '/assets/downloads/leg-structure/5010-Housing-Ankle_Ankle-Mount-2.stl' | relative_url }}" download>STL</a> |
| 5010 Rear Cover – Rear Struct | — | <a href="{{ '/assets/downloads/leg-structure/5010-Rear-Cover_Rear-Struct.stl' | relative_url }}" download>STL</a> |
| Ankle – Feet Mount | L | <a href="{{ '/assets/downloads/leg-structure/Ankle_Feet-Mount-L.stl' | relative_url }}" download>STL</a> |
| Ankle – Feet Mount | R | <a href="{{ '/assets/downloads/leg-structure/Ankle_Feet-Mount-R.stl' | relative_url }}" download>STL</a> |
| Ankle – Feet Mount 2 | L | <a href="{{ '/assets/downloads/leg-structure/Ankle_Feet-Mount-2-L.stl' | relative_url }}" download>STL</a> |
| Ankle – Feet Mount 2 | R | <a href="{{ '/assets/downloads/leg-structure/Ankle_Feet-Mount-2-R.stl' | relative_url }}" download>STL</a> |
| Feet – Flat Foot | — | <a href="{{ '/assets/downloads/leg-structure/Feet_Flat-Foot.stl' | relative_url }}" download>STL</a> |

{: .note }
For any other parts you need, export them from our [baseline CAD model on Onshape]({{ '/cad-to-robot/onshape-cad/' | relative_url }}).

## 2. Assemble the robot

For the assembly steps, you can follow the upstream **Building the Robot** guide and its videos, especially the *Leg* and *Entire robot* videos.

[Berkeley Humanoid Lite: Building the Robot](https://berkeley-humanoid-lite.gitbook.io/docs/getting-started-with-hardware/building-the-robot){: .btn .btn-primary }
[Leg assembly video (YouTube)](https://www.youtube.com/watch?v=aRtWpbteiNA){: .btn }

{: .warning }
Our robot's design is **different** from Berkeley Humanoid Lite, so be careful when following the upstream guide. Check our [baseline CAD model]({{ '/cad-to-robot/onshape-cad/' | relative_url }}) and the photos below when something doesn't match.

### Assembly photos

Sample photos from assembling our robot:

<div style="display: flex; flex-wrap: wrap; gap: 1rem; align-items: flex-start;">
  <figure style="flex: 1 1 280px; margin: 0; min-width: 0;">
    <img src="{{ '/assets/images/robot-assembly/hip-actuators.jpg' | relative_url }}" alt="Two hip actuators with XDrive MINI driver boards, attached to a black 3D-printed hip structure part." style="width: 100%;">
    <figcaption class="fs-2 text-grey-dk-000">Hip actuators on the hip structure</figcaption>
  </figure>
  <figure style="flex: 1 1 280px; margin: 0; min-width: 0;">
    <img src="{{ '/assets/images/robot-assembly/leg-assembly-in-progress.jpg' | relative_url }}" alt="A leg being assembled on a workbench: several orange and black actuators joined by black leg structure parts, with bolts and an actuator ring nearby." style="width: 100%;">
    <figcaption class="fs-2 text-grey-dk-000">Assembling a leg</figcaption>
  </figure>
  <figure style="flex: 1 1 220px; margin: 0; min-width: 0;">
    <img src="{{ '/assets/images/robot-assembly/legs-and-body.jpg' | relative_url }}" alt="Top view of both assembled legs laid out on a workbench, with the body frame in front showing the 12 V to 24 V booster, the computer, and the emergency stop button." style="width: 100%;">
    <figcaption class="fs-2 text-grey-dk-000">Both legs and the body frame, before joining them</figcaption>
  </figure>
  <figure style="flex: 1 1 220px; margin: 0; min-width: 0;">
    <img src="{{ '/assets/images/robot-assembly/body-frame.jpg' | relative_url }}" alt="Front view of the body frame: the computer on the top floor, the power relay and other components on the middle floor, and the battery below." style="width: 100%;">
    <figcaption class="fs-2 text-grey-dk-000">The body frame (see <a href="{{ '/hardware/body-system/' | relative_url }}">Body System</a>)</figcaption>
  </figure>
</div>
