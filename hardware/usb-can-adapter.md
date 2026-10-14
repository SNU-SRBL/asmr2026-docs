---
title: USB-to-CAN Adapter
parent: Robot Hardware
nav_order: 4
permalink: /hardware/usb-can-adapter/
---

# USB-to-CAN Adapter

The computer talks to the motor drivers over CAN, through a USB-to-CAN adapter. In this course we use the **CANable V2.0 Pro USB to CAN module** from Makerbase (MKS), which is based on the open-source [CANable](https://canable.io).

<img src="{{ '/assets/images/hardware/canable-v2-pro.png' | relative_url }}" alt="CANable V2.0 Pro USB-to-CAN module: a small board with a USB-C connector at one end and a green screw terminal for the CAN bus at the other." style="max-width: 240px; width: 100%;">

CANable V2.0 Pro USB to CAN module (image: Makerbase)
{: .fs-2 .text-grey-dk-000 }

- [Product page (DeviceMart, Korean)](https://www.devicemart.co.kr/goods/view?no=15775527)
- [CANable official website](https://canable.io)
- [MKS CANable GitHub repository](https://github.com/makerbase-mks/CANable-MKS)

## Firmware: slcan vs. candleLight

The adapter ships with **slcan** firmware, which is slower than SocketCAN.

We recommend flashing it with the **candleLight** firmware instead. With candleLight, the adapter shows up on Linux as a native **SocketCAN** interface (for example `can0`), so you can use it directly with standard Linux CAN tools and libraries.

| Firmware | Interface on Linux | Recommended |
|:---------|:-------------------|:------------|
| slcan (stock) | Serial device, set up through `slcand` | |
| candleLight | Native SocketCAN interface (`can0`) | ✓ |

## Flashing candleLight

Follow the **Updating Firmware** instructions on the CANable website. The easiest way is the **CANable Updater** web app in Google Chrome.

[CANable: Getting Started](https://canable.io/getting-started.html){: .btn .btn-primary }
[CANable Updater](https://canable.io/updater/){: .btn }

After flashing, plug the adapter in and bring up the CAN interface on Linux, for example:

```bash
sudo ip link set can0 up type can bitrate 500000
```

{: .note }
The bitrate must match the CAN bitrate configured on your motor drivers.
