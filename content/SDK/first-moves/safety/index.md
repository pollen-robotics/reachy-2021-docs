---
title: "Safety first"
description: "What you need to be aware of as a user to prevent Reachy from getting damaged and you from getting hurt."
lead: "Before showing you how to control each part of the robot, let's talk a bit about safety, both for you and the robot."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  SDK:
    parent: "first-moves"
weight: 220
toc: true
---

First, make sure that you followed the instructions from the section detailing [how to attach your robot]({{< ref "docs/getting-started/attach" >}}).

Especially, the screws in the Reachy's back and the ones fixatings its metal support should be well tightened.

## Turning on/off the motors

If at anytime when you're working with Reachy you feel that you're losing control of the robot's movements, don't hesitate to turn the motors off. Use the switch button placed in its back. 

<p align="center">
  <img src="power_button.jpeg" alt="drawing" width="50%"/>
</p>

Also, don't forget to turn the motors off when you're done working with the robot.

## Don't harm yourself...

Even though there is little chance that you get hurt using Reachy, you might get surprised by its movements, especially the first times. 

We recommend that you move both Reachy's arms with your hands before you start programing it. The goal is that you get a sense of Reachy's working space, the positions it can reach so that you won't get hit when you actually send it commands.

## and don't harm Reachy!

There are a few things you need to know to make sure that your Reachy doesn't get damaged when using it.

### Don't stay in stiff mode if you're not moving the robot

Each Reachy's motor can be in one of two compliance modes:
* **compliant**: the motor is soft and can be freely turned by hand. It cannot be controlled, setting a new target position will have no effect. Yet you can still read the motor position.
* **stiff**: the motor is hard and cannot be moved by hand. It can be controlled by setting new target position. In this mode, the motor use its maximum torque to maintain its present position until a target position is sent.

You can change the compliance mode of a joint with its *compliant* attribute.

```python
reachy.r_arm.r_gripper.compliant = False # stiff mode

reachy.r_arm.r_gripper.compliant = True # compliant mode
```

or if you prefer to change the compliance of all the joints in a part of Reachy (left/right arm or the head), you can use the *turn_on()* and *turn_off()* methods. 

*turn_on()* puts all the joints of the requested part in stiff mode whereas *turn_off()* put them in compliant mode.

```python
reachy.turn_on('r_arm')
```
Try this on your robot to feel the resistance applied by the right arm's motors in stiff mode. You can compare with the left arm which should be in compliant mode. You should hear a small noise coming from the right arm's motors, especially if you try to move them with your hands, it's totally normal when they are in stiff mode.

If you want to the right arm's motors back to compliant mode:
```python
reachy.turn_off('r_arm')
```

> #### What you need to keep in mind
> **You must be careful not to let the joints in stiff mode when you're not using the robot**. This mode can be really demanding for a motor, letting a motor in stiff mode will damage it after some time.
>
> If an arm is lifted or if the neck is lowered, maintaining the position in stiff mode will be exhausting because the motors would have to compensate the gravity and they could get damaged.
> You can make the analogy with a human. If we ask you to keep stretched out arms, after a certain time it will be painful. So is the case for the joints of the robot.

### Be aware of obstacles

When you are sending movements instructions to Reachy, be careful to obstacles that you could block Reachy during its movements.

For example, when you are asking to an arm to go between two positions, it will try to do it as hard as it can, whether or not there is something on its way. Also when you are moving both arms simultaneously, there are no safety measures implemented to prevent them from hitting each other.
Nothing will also prevent Reachy's arms from hitting its chest if you ask them to.
If situations like these happen, don't hesitate to turn off the motors so that Reachy's motors will stop trying to reach a position they can't get.

### Check the temperatures

Reachy's motors will heat when you are using its joints so you should manage the motors temperatures.
The temperatures of each motor can be accessed using ReachySDK.

There are two important temperature constants you need to know, their values depend on Reachy's part:
* **fan trigger temperature**: temperature at which the motor will start to get hot and the matching fan will be turned on. The fans allow to work longer with hot joints but enventually the temperature will keep rising if the joints keep being sollicitated. On Reachy's arms: 45°C.
* **shutdown temperature**: when this temperature is reached, the motor will normally shutdown and stop working until it has cooled down. This is a precaution measure to protect the motor. On Reachy's arms: 55°C.
