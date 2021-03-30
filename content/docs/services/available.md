---
title: "Available services"
description: "Teleoperate Reachy through the VR teleoperation application."
lead: "Discover the services provided to automatically launch the suitable nodes."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "services"
weight: 1010
toc: true
---

Services are available on the robot to automatically launch on start the most commonly used features of the robot. Nevertheless, you may want to use Reachy differently and deactivate them.  

Several services are available on your robot:
* `reachy_kinematics.service`
* `reachy_controllers.service`
* `reachy_sdk_server.service`

The services are stored in `etc/systemd/system`.

If you have a **Full kit**, `reachy_sdk_server.service` is enabled by default, which means that the service is launched automatically when you start the robot.  

This service launch the following nodes:  
* from reachy_kinematics:
  * robot_state_publisher (description)
  * orbita_kinematics_service *(full/starter kit only)*
  * arm_kinematics_service
* from reachy_controllers:
  * joint_state_controller
  * camera_publisher *(full/starter kit only)*
  * camera_zoom_service *(full/starter kit only)*
* from reachy_sdk_server:
  * reachy_sdk_server
  * camera_server *(full/starter kit only)*

Activating `reachy_kinematics.service` will launch the nodes from *reachy_kinematics*.
Activating `reachy_controllers.service` will launch the nodes from *reachy_controllers*.  

For more information on the nodes, please refer to section [What is running/What can I run on my robot]({{< ref "running" >}}).
