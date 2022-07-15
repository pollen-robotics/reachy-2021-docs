---
title: "Anti-collision safety"
description: "LIDAR based anti-collision behaviour"
date: 2021-03-30T09:54:59+02:00
lastmod: 2021-03-30T09:54:59+02:00
draft: false
images: []
menu:
  SDK:
    parent: "mobile-base"
weight: 330
toc: true
---
## Overview
The basic idea is that the LIDAR is used to detect surrounding obstacles and reduce or nullify speed commands that would create a collision with the mobile base.

<p align="center">
    <video controls="controls" width="100%" autoplay once>
    <source type="video/mp4" src="lidar_safety_human.mp4"></source>
    </video>
    <br>
</p>

The safety is active regardless of how you command the mobile base (teleop, controller, goto and set_speed).

:warning: The safety only works with obstacles that can be seen by the LIDAR. Small obstacles that are below the LIDAR won't be seen. Similarly, the LIDAR will see the legs of a table, but not the table top. 

:bulb: We recommend that you get a feel of how this safety works by moving around with the controller see [(getting started)]({{< ref "sdk/mobile-base/getting-started">}}). Drive slowly into a wall, the mobile base should slow down and then stop. The safety should prevent the collision even when driving into the wall at full speed, which we do not recommend though :).

## Detailed behaviour
<p align="center">
    <video controls="controls" width="100%" >
    <source type="video/mp4" src="lidar_safety_360.mp4"></source>
    </video>
    <br>
</p>

- If an obstacle is present inside of the critical distance boundary, then the speed of the mobile base is reduced in all directions, and nullified in the direction that would cause a collision. Rotations are slowed down but are still allowed. 
- Otherwise, if an obstacle is present inside of the safety distance boundary, then the speed of the mobile base is reduced only in the directions that would eventually cause a collision. Rotations are unchanged.
- Obstacles that are further away than the safety distance do not trigger the safety in any way
  
{{< img alt="safety_drawing" src="safety_drawing1.png" >}}

:bulb: Reachy's design allows the LIDAR to see close to 360° around it, but not entirely because of the metal bar: this creates a small blind spot. Even if a collision would be very unlikely (you'd have to e.g. drive backwards onto a perfectly aligned pole), any speed command that could create an unseen collision are slowed down.

:warning: Do not obstruct the LIDAR by placing an objet on top of the mobile base as it will be considered as an obstacle.

:warning: If the LIDAR disconnects during usage or if its controller crashes, then the mobile base will stop and will reject commands.

## Advanced tuning

The mobile base's Hardware Abstraction Layer runs with the anti-collision behaviour active by default. Currently, disabling/enabling the safety is the only configuration you can make using the SDK. If you need to fine tune the behaviour, you'll have to interact with the world of ROS and change the [HAL parameters](https://github.com/pollen-robotics/zuuu_hal/blob/main/config/params.yaml) (you'll have to recompile the package for the changes to take effect).

The code can be accessed [here.](https://github.com/pollen-robotics/zuuu_hal/blob/main/zuuu_hal/lidar_safety.py)

