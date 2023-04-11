---
title: "Disconnected force sensor"
description: ""
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
toc: true
hidden: true
---

TODO: update

Each arm of Reachy is equipped with a load sensor to measure how much force is applied by the gripper to the object. It allows to know when the gripper is holding an object.

The load sensor is in two part: the sensor itself and an electronic board reading its values and connected to Reachy's internal computer.

<p align="center">
  <img src="load_sensor_full.jpg" alt="drawing" width="60%"/>
</p>

The sensor is placed between the two 3D printed pieces composing Reachy's gripper.

<p align="center">
  <img src="sensor_in_gripper.jpg" alt="drawing" width="60%"/>
</p>

The electronic board is placed between the gripper and wrist_roll motors of the arms.

<p align="center">
  <img src="load_sensor_schematic.png" alt="drawing" width="60%"/>
</p>

<p align="center">
  <img src="load_sensor_views.png" alt="drawing" width="70%"/>
</p>

The board is connected to Reachy's computer by a long 8 black wires cable plugged by the back.

When we refer in the documentations as the load sensor being disconnected, we refer to the cable between the board and Reachy's computer as disconnected. It's usually the case, the wires between the sensor and the board are rarely desoldered.

You can check an example of the disconnected cable below.

<p align="center">
  <img src="load_sensor_disconnected.jpg" alt="drawing" width="50%"/>
</p>

Be aware that there is a way for the connector. On the cable there is a short and a long side. 

<p align="center">
  <img src="module_views.png" alt="drawing" width="90%"/>
</p>
