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
- **neck_zero_hardware**: TODO


Typically, *~/.reachy.yaml* looks like this:

```yaml
model: full_kit
zuuu_model: None
TODO:
```

For a Reachy mobile, i.e. a Reachy Full Kit with a mobile base, the configuration file looks like this:

```yaml
model: full_kit
zuuu_model: 1.0
TODO:
```