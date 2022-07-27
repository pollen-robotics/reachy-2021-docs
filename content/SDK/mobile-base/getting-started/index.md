---
title: "Getting started with the mobile base"
description: "Quick overview of the mobile base control using the Python SDK"
date: 2021-03-30T09:54:59+02:00
lastmod: 2021-03-30T09:54:59+02:00
draft: false
images: []
menu:
  SDK:
    parent: "mobile-base"
weight: 300
toc: true
---

## Overview
To control the mobile base, we developed a Python SDK working similarly to *reachy-sdk* but only for the mobile base: [mobile-base-sdk](https://github.com/pollen-robotics/mobile-base-sdk). As with *reachy-sdk*, you can use *mobile-base-sdk* to connect to the base remotely from another computer, as long as your computer and Reachy's computer are connected to the same network.

However, to avoid having to use two different Python SDks when working on Reachy mobile, we integrated the use of mobile-base-sdk in reachy-sdk so that when you're accessing the mobile base with the *reachy_mobile.mobile_base* attribute, you are actually using *mobile-base-sdk*.

Having a dedicated SDK for the mobile base still gives the advantage of having the possibility to work on the mobile base alone.
More detailed in the page [Using the mobile base without Reachy]({{< ref "/sdk/mobile-base/mobile-base-alone" >}}).

## Installation
If you did not do it yet, follow the instructions from the [install page]({{< ref "/sdk/getting-started/install" >}}) to learn how to install Reachy's Python SDK on your computer. We recommend performing the installation in a virtual environment.

> :bulb: You will need to make sure that you get a version of [reachy-sdk](https://github.com/pollen-robotics/reachy-sdk) > xx [TODO] to be able to connect to the mobile base.

Even though you used PyPi for the installation, we recommend cloning the [mobile-base-sdk repository](https://github.com/pollen-robotics/mobile-base-sdk) on your computer as it gives you access to many [examples](https://github.com/pollen-robotics/mobile-base-sdk/tree/main/mobile_base_sdk/examples) to learn how to use the mobile base.

## Connecting to Reachy mobile
Connecting to the mobile base using Reachy's Python SDK is as simple as connecting to Reachy. When instanciating the ReachySDK object with your Reachy's IP as in the [Hello World page]({{< ref "/sdk/getting-started/hello-world" >}}), you just have to specify that you are using a mobile base.

```python
from reachy_sdk import ReachySDK

reachy_mobile = ReachySDK(host='your-reachy-ip', with_mobile_base=True)
```

The mobile base is then accessible with the *reachy_mobile.mobile_base* attribute.

```python
reachy_mobile.mobile_base
>>> <MobileBase host='your-reachy-ip' - version=1.0 - battery_voltage=
        29.1 - drive mode=cmd_vel - control mode=open_loop>
```

## What is accessible on the mobile base
The following are accessible with *reachy_mobile.mobile_base*:
* mobile base version,
* battery level,
* odometry of the base,
* control and drive modes,
* goto and set_speed methods to make the mobile base move.

The section [moving the mobile base]({{< ref "/sdk/mobile-base/moving-the-base" >}}) details the use of the goto and set_speed methods, the odometry of the base while the [advanced]({{< ref "/sdk/mobile-base/drive-control-modes" >}}) section explains the role of the control and drive modes.

## Moving the mobile base

### Using the goto method
You can move the base with just one line of code, using the goto method. For example, you can make a 90 degrees rotation:

```python
reachy_mobile.mobile_base.reset_odometry()
reachy_mobile.mobile_base.goto(x=0.0, y=0.0, theta=90.0)
```

Okay, that was 2 lines of code, but the first one is not needed and was added for safety. The section [moving the mobile base]({{< ref "/sdk/mobile-base/moving-the-base" >}}) is dedicated to explaining how to move the base using the Python SDK.

Check the [getting-started notebook](https://github.com/pollen-robotics/reachy-sdk/blob/main/reachy_sdk/examples/mobile-base-getting-started.ipynb) for a detailed getting started example using the Python SDK.


### Using a joystick
The best (and easiest) way to get a sense of how the mobile base moves is by moving it yourself! It is easy to do that with the [joy_controller.py script](https://github.com/pollen-robotics/mobile-base-sdk/blob/main/mobile_base_sdk/examples/scripts/joy_controller.py) where you can fully control the mobile base using an Xbox or PlayStation joystick (a controller should be included with your Reachy mobile).

To start controlling the base with *joy_controller.py*, just type:
```bash
cd ~/dev/mobile-base-sdk/examples/script
python3 joy_controller.py
```
The left joystick will be used for translation and the right one for rotation.

<p align="center">
    <video controls="controls" width="100%" >
    <source type="video/mp4" src="../safety/lidar_safety_360.mp4"></source>
    </video>
    <br>
</p>

The script reads the controller and uses the *mobile-base-sdk* to send speed commands to the mobile base. Don't hesitate to take a look at the [code](https://github.com/pollen-robotics/mobile-base-sdk/blob/main/mobile_base_sdk/examples/scripts/joy_controller.py) to have an example of good practices for an app involving the base.

## Hardware Abstraction Layer
In this documentation, you'll find references to the Hardware Abstraction Layer (HAL). The HAL is the ROS2 middleware that interacts with the hardware while the SDK interacts with the HAL. This modular software architecture allows for more flexibility and a simple, high level interface. However, if you need more control or a feature that wasn't ported to the SDK, you can interact directly with the HAL. The philosophy behind this documentation is to give an easy access to the most common usages, and to give pointers that can be useful when pursuing a more advanced usage. The [HAL repository can be found here.](https://github.com/pollen-robotics/zuuu_hal)