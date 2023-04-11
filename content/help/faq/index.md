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

{{% expand "> Got '_InactiveRpcError' when I try to use ReachySDK from Python SDK. "%}}
It's very likely that you have a problem with reachy_sdk_server, the server running Reachy's software. Check the [Quick debug]({{< ref "help/debug" >}}) section.
{{% /expand %}}

{{% expand "> Reachy SDK Server is not running." %}}
Check the [Quick debug]({{< ref "help/debug" >}}) section.
{{% /expand %}}

{{% expand "> One of Reachy's motor red led is blinking" %}}
This means the motor has overheat and needs to cooldown. Turn the robot off, wait for it to cooldown and turn it on again.
{{% /expand %}}

{{% expand "> Reachy's head doesn't look straight when asked." %}}
You need to start the robot with the head in a position close to straight when starting the robot. Indeed, Orbita's position encoder only covers part of the whole motion range. We use this starting position to recalibrate the absolute position.
{{% /expand %}}

{{% expand "> Why can't Reachy's computer be turned on?" %}}
Check the page [Reachy's computer is not running]({{< ref "help/system/computer-not-running" >}}) explaining why you couldn't have Reachy's computer on.
{{% /expand %}}

{{% expand "> How can I view the camera feed?" %}}
- If the SDK server is running, check [Reachy's cameras]({{< ref "sdk/first-moves/cameras#video-stream" >}}) from the Python SDK documentation.

- If not, you will need to have a computer screen plugged to Reachy using an HDMI cable. 
To view the left camera, in a terminal in Reachy's computer:
```bash
python3 ~/reachy_ws/src/reachy_2023/camera_controllers/examples/view_cam.py left open_cv
```
{{% /expand %}}

{{% expand "> The images from the cameras are blurry. "%}}
You can use the autofocus available in reachy-sdk.
For example, if you want to start the autofocus for the left camera, use:
```python
reachy.left_camera.start_autofocus()
```

If the autofocus did not work, you can learn how to perform the focus manually with [this page]({{< ref "help/system/manual-focus" >}}).
{{% /expand %}}

{{% expand "> I connected a computer screen to Reachy, but I can't see any image." %}}
There might be a problem with the HDMI connection or Reachy's computer is actually not turned on. You can check the page [Reachy's computer is not running]({{< ref "help/system/computer-not-running" >}}).
{{% /expand %}}

{{% expand "> Where can I find examples on how to use the Edge TPU device? "%}}
Edge TPU Coral device uses the [pycroal](https://github.com/google-coral/pycoral) python library. We use this device everytime we need AI in one of our applications, for example to [classify objects for TicTacToe](https://github.com/pollen-robotics/reachy-2019-tutorials/blob/master/custom_classifier/Tuto_classification.ipynb).
{{% /expand %}}

{{% expand "> Can you explain a bit Reachy's software?" %}}
Check the [Overall presentation]({{< ref "advanced/software/presentation" >}}) of the Software section.
{{% /expand %}}

{{% expand "> Does Reachy Mobile come with an autonomous navigation stack?" %}}
The current release does not come with an autonomous navigation stack. However, we have an internal (experimental) version where [nav2](https://navigation.ros.org/) runs. If this is of interest to you, please let us know.
{{% /expand %}}
