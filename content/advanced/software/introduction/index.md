---
title: "Working with ROS2 Foxy"
description: "Using ROS2 Foxy for low-level control."
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  advanced:
    parent: "software"
weight: 300
toc: true
---

Reachy runs natively on [ROS2 Foxy](https://docs.ros.org/en/foxy/index.html). ROS stands for Robotic Operating System, it offers a huge variety of compatible algorithms and hardware drivers.

The embedded NUC computer comes with ROS2 and Reachy specific packages already installed and running. They provide full access to Reachy. You can:
- get the */joint_state* and publish joint goals
- use *Rviz*
- subscribe to various sensor topic (camera, force sensor, etc)
- access client for IK/FK

While describing ROS or explaining how to use it is beyond the scope of this documentation (you should refer to the [official documentation](https://docs.ros.org/en/foxy/index.html) for that), we will describe the specfic ROS2 packages for Reachy and how to use them.