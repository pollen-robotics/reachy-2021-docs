---
title: "🚨 Best practice"
description: "Towards a good usage of the VR teleoperation app"
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
menu:
  VR:
    parent: "use-teleop"
weight: 600
toc: true
---

{{< warning icon="👉🏾" text="This page contains really important information about the use of the teleoperation app. <b>Please make sure you read it carefully before teleoperating Reachy.</b>" >}}

## Avoid movements discontinuities
Reachy doesn't have the exact same degrees of freedom as you have, neither the same range for each joints. When a position cannot be reached, either because of the position or the orientation, the inverse kinematics gives the closest arm configuration found. The closest configuration found for the next position may be:

- the same as the previous one, so the arm won't move and you have the impression Reachy is not following your movements anymore
- quite different from the previous one, which will lead to sudden changes of the arm position

All this contribute to give movements that seem incontrollable, due to discontinuities in the arm's inverse kinematics.

**To avoid this situation:**

- Avoid using extreme joints orientations while teleoperating Reachy
- Avoid unusual arm positions, there are probably in Reachy's joints limits
- The most limiting joint is the elbow: avoid working to close to your chest, the elbow will be at the limit of its range of motion
- If the robot seems to stop following your movements, do not continue to move in this direction, you have already reached its workspace limit. Go back to a position you know can be reached.

## Avoid damaging motors
Reachy's arms have been thought to manipulate object at a table level and nearby.
Some positions away from this nominal area can require a lot of effort from the motors to be maintained, and cause fast overheating of them. Moreover, manipulating objects requires more effort from the motors.

**To avoid damaging motors:**

- Avoid doing movements above your head
- Avoid keeping your arms straight ahead horizontally to the floor, where the shoulders motors have to carry all the weight of the arms in a static position
- Do not let the motors in stiff mode when you are in the menu if you are not going to teleoperate the robot soon
- Do not try to lift objects that are above Reachy's capabilities

## Avoid damaging 3D parts
Hitting Reachy's arms on objects can damage the painting or even break 3D parts of the robot. It may happen even if the arms crash into something at moderate speed.

**To avoid damaging 3D parts:**
- Check the environment surrounding the robot before starting the teleoperation. Make sure you have enough space around the robot and that there is no object to be hit by the robot (this may also save your object from being broken...)
- Stop teleoperation close to the position which will be reached when the motors will be compliant, so that the arms won't fall from high.

## Familiarize yourself with the robot
- Before trying to make application or to achieve anything using teleoperation with the robot, familiarize yourself with its movements, its workspace and its joints limits.
- Stay near the robot for your first trials: listen to the motors sounds, be aware of your workspace and field of view in a environment you know, try to manipulate light objects
- Explore your own workspace with small and quite slow movements to see how the robot reacts and better understand the relation between your movements and its.


{{< alert icon="💡" text="You may feel like being in a video game at some point, but never forget your movements are reproduced in real life!" >}}
