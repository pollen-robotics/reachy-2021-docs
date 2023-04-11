---
title: "Introduction"
description: "Quick overview of the Python SDK and of the other options available to control the robot."
date: 2021-03-30T09:54:59+02:00
lastmod: 2021-03-30T09:54:59+02:00
draft: false
images: []
menu:
  SDK:
    parent: "getting-started"
weight: 100
toc: true
---

## The SDK in a nutshell

The [Python SDK](https://github.com/pollen-robotics/reachy-sdk) lets you easily control and program a Reachy robot. It is used to read sensor information (eg. force sensor, camera image or joint position) and send actuator commands (eg. target position, turning on a fan).

It is designed to:

* let you start controlling your robot in a few lines of codes,
* allow to focus on your application and not on hardware synchronisation issues,
* facilitate fast prototyping and iteration.

Connecting to your robot and getting the up-to-date position of all joints is as simple as:
```python
from reachy_sdk import ReachySDK

reachy = ReachySDK(host='192.168.0.42')  # Replace with the actual IP

for name, joint in reachy.joints.items():
    print(f'Joint "{name}" position is {joint.present_position} degree.')
```

You can use it directly on Reachy's computer or work remotely on another computer, as long as you are connected on the same network. The SDK works on Windows/Mac/Linux and requires Python >= 3.6. It is entirely open-source and released under an [Apache 2.0 License](https://github.com/pollen-robotics/reachy-sdk/blob/main/LICENSE).

## Is this the right option for me?

The Python SDK is only one way to control Reachy. There are other options that have different pros and cons. 

To know if the SDK is the right option, the TL;DR here would be something like:

* You want to **focus on creating an application or behavior on Reachy**.
* You **don't want to dig into the details** on how it can be controlled or run very time constrained code (eg. need more than 100Hz control).
* You have **basic knowledge of Python** (no advanced knowledge is required).
* You do not already have an important code base running on ROS2.

## The other options

### Unity VR App

If you are interested in tele-operation and want to control Reachy via VR controllers, you can directly use our Unity VR App. More information on the [dedicated section]({{< ref "VR/introduction/introduction" >}}).

### ROS2 Humble packages

Reachy runs on [ROS2 Humble](https://docs.ros.org/en/humble/index.html). ROS is a Robotic Operating System, it offers a huge variety of compatible algorithms and hardware drivers. Yet, if you are not familiar with ROS, the beginning can be a bit overwhelming. 

The embedded NUC computer comes with ROS2 and Reachy specific packages already installed and running. They provide full access to Reachy (lower-level than the SDK). You can:
- get the *joint states* and *forward position controllers*
- use *Rviz*
- subscribe to various sensor topic (camera, force sensor, etc)
- access client for IK/FK

For more information, please refer to the [dedicated section]({{< ref "advanced/software/ros2-level" >}}).

### Custom gRPC client

If you want to use another language than Python, for instance to integrate Reachy's control within an existing code base, you can write your own [gRPC](https://grpc.io) client. Our API is available [here](https://github.com/pollen-robotics/reachy-sdk-api).

The API is used both by the Python SDK and the VR App.
