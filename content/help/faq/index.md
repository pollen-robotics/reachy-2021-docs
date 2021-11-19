---
title : "FAQ"
description: "FAQ"
lead: ""
date: 2020-10-06T08:48:23+00:00
lastmod: 2020-10-06T08:48:23+00:00
draft: false
images: []
menu:
  help:
    parent: help
weight: 110
toc: true
---
Non exhaustive list of common questions from Reachy's users. 
If you don't see yours in it, don't hesitate to drop a message on our support channel on [Discord](https://discord.gg/Kg3mZHTKgs)!

<br/>

{{% expand "> How to find the IP of my robot?" %}}
Check the [Find my IP section]({{< ref "help/system/find-my-ip" >}}).
{{% /expand %}}

{{% expand "> The SDK server is not starting." %}}
Check the [Debug section]({{< ref "docs/debug/debug-method" >}}).
{{% /expand %}}

{{% expand "> One of Reachy's motor red led is blinking" %}}
This means the motor has overheat and needs to cooldown. Turn the robot off, wait for it to cooldown and turn it on again.
{{% /expand %}}

{{% expand "> One of Reachy's module blue led is blinking" %}}
This means the module encounter an issue (safety shutdown, incorrect instruction, etc.). You need to turn the robot off and on again to restart the module. If the issue persists check the logs to get more information on the source of the issue.
{{% /expand %}}

{{% expand "> Reachy's head doesn't look straight when asked." %}}
You need to start the robot with the head in a position close to straight when starting the robot. Indeed, orbita's position encoder only covers part of the whole motion range. We use this starting position to recalibrate the absolute position.
{{% /expand %}}

{{% expand "> Why is Reachy's computer not running?" %}}
Check the dedicated [Notion page](https://www.notion.so/70ebaaa10a0b4577a936fcd2e5488085) explaining why you couldn't have Reachy's computer on.
{{% /expand %}}

{{% expand "> One of Reachy's motor has a red LED blinking." %}}
This means the motor has overheat and needs to cooldown. You should turn the robot off and let the motor cooldown. After that, you can use the robot as usual.
{{% /expand %}}

{{% expand "> Orbita blue LED is on or blinking." %}}
Check the dedicated [Notion page](https://www.notion.so/8c0373d0c46f4d00bc42007f3cd85957) explaining the meaning of Orbita's led.
{{% /expand %}}

{{% expand "> Reachy SDK Server is not running." %}}
Check the dedicated [Notion page](https://www.notion.so/a1d69e918f4c4253a55c2827473a3d06) explaining reasons which could prevent the server from running correctly.
{{% /expand %}}

{{% expand "> How can I view the camera feed?" %}}
A [python script](https://github.com/pollen-robotics/reachy_controllers/blob/master/examples/view_cam.py) is available in Reachy to check what the cameras are viewing. 
If the SDK server is running (which is the default behavior), for the left camera:
```bash
python3 ~/reachy_ws/src/reachy_controllers/examples/view_cam.py left ros
```
For the right camera:
```bash
python3 ~/reachy_ws/src/reachy_controllers/examples/view_cam.py right ros
```
If the SDK server is not running, replace the *ros* argument by *opencv*.
 %}}
{{% /expand %}}

{{% expand "> The images from the cameras are blurry. "%}}
You can use the autofocus available in reachy-sdk.
{{% /expand %}}

{{% expand "> Where can I find examples on how to use the Edge TPU device? "%}}
Edge TPU Coral device uses the [pycroal](https://github.com/google-coral/pycoral) python library. We use this device everytime we need AI in one of our applications, for example to [classify objects for TicTacToe](https://github.com/pollen-robotics/reachy-2019-tutorials/blob/master/custom_classifier/Tuto_classification.ipynb).
{{% /expand %}}

{{% expand "> Can I control Orbita's fan? "%}}
Orbita's fan is managed automatically based on temperatures limits set for Orbita in Reachy's software. You can't control it using Reachy's SDK.
{{% /expand %}}

{{% expand "> Got '_InactiveRpcError' when I try to use ReachySDK from Python SDK. "%}}
It's very likely that you have a problem with reachy_sdk_server, the server running Reachy's software.
{{% /expand %}}

{{% expand "> Reachy's head is not looking straight forward when it's supposed to." %}}
You might need to redefine the zero position of Orbita. Check the dedicated [Notion page](https://www.notion.so/82b8e6b4e4744809b79dffc9385258f1).
{{% /expand %}}

{{% expand "> Can you explain a bit Reachy's software?" %}}
{{% /expand %}}

{{% expand "> I connected a computer screen to Reachy, but I can't see any image." %}}
There is probably a problem with the HDMI connection. You can check the dedicated [Notion page](https://www.notion.so/70ebaaa10a0b4577a936fcd2e5488085).
{{% /expand %}}
