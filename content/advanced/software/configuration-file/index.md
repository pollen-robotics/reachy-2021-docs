---
title: "Reachy's configuration file"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  advanced:
    parent: "software"
weight: 420
toc: true
---
We created a custom yaml file (***~/.reachy.yaml***) to indicate which Reachy's configuration your robot has and whether a mobile base is connected to the robot or not. Having this file is useful to start only the necessary code required by the Reachy version you are using.

This file is read when [Reachy's main services]({{< ref "/advanced/services/available" >}}) are launched at boot or by the bringup launch file.

The configuration file has multiple entries:
- **model**: model of your Reachy (if it is a full kit, a starter kit, ...). When [reachy_sdk_server.service]({{< ref "/advanced/services/available#reachy_sdk_serverservice" >}}) starts, it will look at this entry to choose what code it has to run depending on the model of the robot.
- **zuuu_model**: is at None if no mobile base is attached with the robot, else the mobile base version is indicated (current mobile base version is 1.0). When [reachy_mobile_base.service]({{< ref "/advanced/services/available#reachy_mobile_baseservice" >}}) starts, if *zuuu_model* is not None, the mobile base code is launched.
- **neck_zero_hardware**: hardware position of the three disks. You should not need to change those values unless you changed Orbita.


Typically, *~/.reachy.yaml* looks like this:

```yaml
generation: 2023
model: full_kit
zuuu_version: 1.2
neck_orbita_zero:
    top: 0.0
    middle: 0.0
    bottom: 0.0
camera_parameters:
    left:
        fx: 0.0
        fy: 0.0
        cx: 0.0
        cy: 0.0
        k1: 0.0
        k2: 0.0
        k3: 0.0
        p1: 0.0
        p2: 0.0
    right:
        fx: 0.0
        fy: 0.0
        cx: 0.0
        cy: 0.0
        k1: 0.0
        k2: 0.0
        k3: 0.0
        p1: 0.0
        p2: 0.0
```

You can find a template [here](https://github.com/pollen-robotics/reachy_2023/blob/develop/reachy_utils/reachy_utils/files/.reachy.yaml).