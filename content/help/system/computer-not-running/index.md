---
title: "Reachy's computer is not running"
description: ""
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
toc: true
hidden: true
---

## Reachy's computer is off, even after pressing the on button

When you power your robot and turn on both the motors and Reachy's computer, you might have Reachy's computer still not turned on. 

There are two ways to check this:

- check Reachy's computer power button

<p align="center">
  <img src="button-a.png" alt="drawing" width="50%"/>
</p>

![button-a.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/74ea1a35-483f-48d7-a692-cc9feb0f6d45/button-a.png)

If the computer is turned on, there should be a round white led around the button brighting.

- check if the computer fan is running

To do that, first lower Reachy's tee-shirt, on the front side you should see something like this:

<p align="center">
  <img src="torso.png" alt="drawing" width="60%"/>
</p>

![torso.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a405f594-9668-43e6-824f-b0208e772282/torso.png)

The fan is the blue piece on the photo. If you can see the fan blades, it means that the computer is not running. If not, it probably means that the fan is running and it is just too fast for the blades to be seen.

So if you checked that Reachy's computer is off, even after pressing the on button, this probably means that the cable powering it is disconnected.

<p align="center">
  <img src="plug_power_switch.png" alt="drawing" width="60%"/>
</p>

![plug_power_switch.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0212f95f-6009-47a3-be02-fd30b614e5e4/plug_power_switch.png)

If it actually is, you should plug the cable back, according to the pin schematic shown in the photo above. This should solve the problem.

## Reachy's computer is on, but nothing is displayed

If you can see that Reachy's computer is running (either by seeing the round led in the button brighting or by checking if the computer's fan running) but still can't see any image with a computer screen plugged to the robot, it probably means that there is an issue with the hdmi connection.

First of all, check that that the computer screen is actually powered and that the hdmi cable is well plugged. A defective hdmi cable can also cause bad connections.

<br>

{{< alert icon="💡" text="You should have the screen already plugged to the computer before starting it. We know that there might be issues when the hdmi cable is plugged the computer being turned on." >}}

<br>

Sometimes, just restarting the computer solves the problem.