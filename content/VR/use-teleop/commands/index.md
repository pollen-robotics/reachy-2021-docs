---
title: "Controllers inputs"
description: ""
lead: "Mappings between the VR controllers and the app"
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  VR:
    parent: "use-teleop"
weight: 640
toc: true
hidden: true
---

## Oculus Quest

{{< img alt="Oculus Quest controller mapping" src="oculus-mapping.png" width="600px" >}}

|Name|Feature description |
|----|--------------------|
|**(A)**|**At robot teleoperation start:** Validate position and start robot teleoperation|
|       |**During teleoperation:** Return to menu|
|**(B)**|**At robot teleoperation start:** Cancel and return to menu|
|**(X)**|**At robot teleoperation start:** Validate position and start robot teleoperation|
|       |**During teleoperation:** Return to menu|
|**(Y)**|**At robot teleoperation start:** Cancel and return to menu|
|       |**During teleoperation:** Show/Hide state panel (control of robot's temperature)|
|**Joystick left**|**During teleoperation:** Control mobile base direction|
|**Joystick right**|**During teleoperation:** Control antennas' emotion|
|**Index Trigger left**|**In menu:** Select button|
|                      |**During teleoperation:** Control left gripper|
|**Index Trigger right**|**In menu:** Select button|
|                       |**During teleoperation:** Control right gripper|
|**Middle finger Trigger left**|**During teleoperation:** Use translation mode for mobility|
|**Controller left position / orientation**|**During teleoperation:** Reachy's left arm end effector position / orientation|
|**Controller right position / orientation**|**During teleoperation:** Reachy's right arm end effector position / orientation|
|**Headset orientation**|**During teleoperation:** Reachy's head orientation|


## Valve Index

{{< img alt="Valve Index controller mapping" src="valve-mapping.png" width="600px" >}}

|Name|Feature description |
|----|--------------------|
|**(A)**|**At robot teleoperation start:** Validate position and start robot teleoperation|
|       |**During teleoperation:** Return to menu|
|**(B)**|**At robot teleoperation start:** Cancel and return to menu|
|*left (B) only*|**During teleoperation:** Show/Hide state panel (control of robot's temperature)|
|**Joystick left**|**During teleoperation:** Control mobile base direction|
|**Joystick right**|**During teleoperation:** Control antennas' emotion|
|**Index Trigger left**|**In menu:** Select button|
|                      |**During teleoperation:** Control left gripper|
|**Index Trigger right**|**In menu:** Select button|
|                       |**During teleoperation:** Control right gripper|
|**Controller left position / orientation**|**During teleoperation:** Reachy's left arm end effector position / orientation|
|**Controller right position / orientation**|**During teleoperation:** Reachy's right arm end effector position / orientation|
|**Headset orientation**|**During teleoperation:** Reachy's head orientation|
