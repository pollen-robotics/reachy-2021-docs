---
title: "Use Reachy properly"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  advanced:
    parent: "safety"
weight: 300
toc: true
---

## Don't harm yourself...

Even though there is little chance that you get hurt using Reachy, you might get surprised by its movements, especially the first times. 

We recommend that you move both Reachy's arms with your hands before you start programming it. The goal is that you get a sense of Reachy's working space, the positions it can reach so that you won't get hit when you actually send it commands.

<p align="center">
    <video controls="controls" width="30%" autoplay loop>
    <source type="video/mp4" src="movement_compliant.mp4"></source>
    <source type="video/webm" src="movement_compliant.webm"></source>
    </video>
    <br>
    Try it yourself!
</p>


## and don't harm Reachy!

There are a few things you need to know to make sure that your Reachy doesn't get damaged when using it.

### Don't stay in stiff mode if you're not moving the robot

Each Reachy's motor can be in one of two compliance modes:
* **compliant**: the motor is soft and can be freely turned by hand as in the video above.
It cannot be controlled with code, setting a new target position will have no effect. Yet you can still read the motor position.
* **stiff**: the motor is hard and cannot be moved by hand. It can be controlled by setting new target position. In this mode, the motor use its maximum torque to maintain its present position until a target position is sent. You should hear a small noise coming from a motor in stiff mode, especially if you try to move it with your hands, it's totally normal.

<p align="center">
    <video controls="controls" width="30%" autoplay loop>
    <source type="video/mp4" src="stiff.mp4"></source>
    <source type="video/webm" src="stiff.webm"></source>
    </video>
    <br>
    Reachy's right arm motors resisting in stiff mode
</p>

Check out the [Python SDK section](https://docs.pollen-robotics.com/sdk/first-moves/arm/#from-the-joints) on how to switch between the two modes.


> #### :rotating_light: What you need to keep in mind
> **You must be careful not to let the joints in stiff mode when you're not using the robot**. This mode can be really demanding for a motor, letting a motor in stiff mode will damage it after some time.
>
> If an arm is lifted or if the neck is lowered, maintaining the position in stiff mode will be exhausting because the motors would have to compensate the gravity and they could get damaged.
> You can make the analogy with a human. If we ask you to keep stretched out arms, after a certain time it will be painful. So is the case for the joints of the robot.

### Be aware of obstacles

When you are sending movements instructions to Reachy, mind the obstacles that could block Reachy during its movements.

For example, when you are asking to an arm to go between two positions, it will try to do it as hard as it can, whether or not there is something on its way. Also when you are moving both arms simultaneously, there are no safety measures implemented to prevent them from hitting each other.
Nothing will also prevent Reachy's arms from hitting its chest if you ask them to.
If situations like these happen, don't hesitate to use the motor's switch in Reachy's back to **immediately turn off** the motors so that Reachy's motors will stop trying to reach a position they can't get.

### Check the temperatures

Reachy's motors will heat when you are using its joints so you should manage the motors temperatures.
The temperatures of each motor can be accessed using ReachySDK.

There are two important temperature constants you need to know, their values depend on Reachy's part:
* **fan trigger temperature**: temperature at which the motor will start to get hot and the matching fan should be turned on automatically. The fans allow to work longer with hot joints but enventually the temperature will keep rising if the joints keep being sollicitated. On Reachy's arms: 45°C.
* **shutdown temperature**: when this temperature is reached, the motor will normally shutdown and stop working until it has cooled down. This is a precaution measure to protect the motor. On Reachy's arms: 55°C.


## Good practices
Here is a non-exhaustive list of things to remember when you are using your Reachy, in order to make it last as long as possible.

- Make sure that the robot is turned off and that the power supply is disconnected when you are not using it.
- Remember not to let the motors in stiff mode if you don't plan to make them move. Even letting the arms on a table and in stiff mode for quite some time might damage them. 
- Check that no obstacles will be on Reachy's way when it will try to move. Sending commands to Reachy's arms with an obstacle on the way will make the motors force as much as they can. Being in this kind of situation might happen but when this does, remember to turn off the motors immediately using the switch button in Reachy's back.