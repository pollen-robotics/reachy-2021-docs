---
title: "Set Reachy ready"
description: ""
lead: "Prepare your robot for teleoperation"
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  VR:
    parent: "use-teleop"
weight: 641
toc: true
---

## To teleoperate Reachy from the same network
If the computer used for the teleoperation app is connected to the same network as your robot, you only need to know your robot IP address.  

{{< alert icon="💡" text="<i>Don't know how to get it? </i><a href=\"/help/system/find-my-ip\">Find out Reachy's IP address</a>." >}}

## To teleoperate Reachy remotely
To teleoperate Reachy from another network, you need to create a redirection of an IP address towards your robot local IP address.  
Set a static IP address to your robot and use the redirection address on the VR application.

## Make sure the robot is ready
For the application to connect to be able to connect to the robot make sure:
* the robot is turned on
* the robot is connected to the network. We advise the robot to be **hard-wired** using an ethernet cable.
* all robot services are launched.  
*By default, all required services are launched automatically when you turn the robot on for **full/starter kits**. For more information, check the [available system services]({{< ref "advanced/services/available" >}}).* 