---
title: "Use the mobile base properly"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  advanced:
    parent: "safety"
weight: 310
toc: true
---

## Basic mouvements

We recommend that you get a feel for the inertia of the robot by holding on to the metal pole and pushing and pulling it. 


Block a wheel with your foot and try to gently tilt the robot.


Then use the controller to move around the robot as explained in [Moving the mobile base]({{< ref "sdk/mobile-base/moving-the-base" >}})
<p align="center">
    <video controls="controls" width="100%" autoplay once>
    <source type="video/mp4" src="controller_mouvement.mp4"></source>
    </video>
    <br>
</p>

## Common risks and advice
Even though the mobile base is programmed to move relatively slowly, it is important to try to avoid any potential collisions. The mobile base is designed to be used indoors on a flat surface.

:bulb: The arms and any grasped objects should ideally be in the vertical projection of the mobile base. The idea here is that the robot should always be able to rotate in place safely. Also, keeping the arms tugged in reduces the risk of tipping.

A low level collision avoidance safety always runs in the background, but it can only prevent collisions seen by the LIDAR. Read more about it in [Anti-collision safety]({{< ref "sdk/mobile-base/safety" >}}). A non exaustive list of cases where the safety can't work:
* Stairwells. There are no cliff sensors so the robot has no practical way of knowing it's near downward stairs.
* A table. The LIDAR can see the legs but not the table top. 
* A large clean bay window migh be invisible to the LIDAR. 
* Small obstacles that fit below the LIDAR won't be seen.

Another risk is the robot tipping. Avoid rapid variations in acceleration. Also, we don't recommend using the robot on a slope above 10°.


## Battery management
We chose a high end battery for the mobile base. The Life4PO technology and the overal grade of the equipement (BMS, charger, monitoring system, certified UN 38.3, 5 years warranty), should make this one of the safest choices available on the market.
However, the battery can hold a large amount of energy (832 Wh) and should always be treated carefully.

:warning: Only use the dedicated charger to charge the battery

:bulb: When stocking the battery for long periods, aim for at least 60% charge

:bulb: Use the monitoring system (small screen on the mobile base) to recharge the battery before reaching 0% and relying on the BMS to shutdown the battery.

## Dynamic capabilities
The wheel motors are **very** potent. In their default configuration, they are used at 20% of their maximum capabilities.
You can, at your own risk, modify this limit in the [configuration of the HAL](https://github.com/pollen-robotics/zuuu_hal).
