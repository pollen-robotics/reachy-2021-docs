---
title: "Working with ROS2 Humble"
description: "Working at the ROS level of the robot. What are the different nodes available."
lead: "Working at the ROS level for low-level control."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  advanced:
    parent: "software"
weight: 410
toc: true
---

Even if [gRPC clients]({{< ref "/advanced/software/presentation#grpc-clients" >}}) are available to control Reachy without knowing how to use ROS, you may want to work at the ROS level to implement new things for Reachy or use the tools provided by ROS. In this page, we will describe how to use the specfic ROS2 packages for Reachy.

Reachy runs natively on [ROS2 Foxy](https://docs.ros.org/en/foxy/index.html). ROS stands for Robotic Operating System, it offers a huge variety of compatible algorithms and hardware drivers.

The embedded NUC computer comes with ROS2 and Reachy specific packages already installed and running. They provide full access to Reachy. You can:
- get the */joint_state* and publish joint goals
- use *Rviz*
- subscribe to various sensor topic (camera, force sensor, etc)
- access client for IK/FK

> NOTE: If you don't know how to use ROS but still want to do it on Reachy, you should check the [official ROS documentation](https://docs.ros.org/en/foxy/index.html), espcecially the [tutorials](https://docs.ros.org/en/foxy/Tutorials.html) showing examples and presenting the different key notions introduced by ROS.

## What is runnning by default

If you have a **Full kit** or a **Starter kit**, `reachy_sdk_server.service` is enabled by default, meaninig that all Reachy ROS2 packages presented in the [Overall presentation]({{< ref "/advanced/software/presentation" >}}) are automatically launched when you start the robot.

If you have a **Reachy mobile**, `reachy_mobile_base.service` is enabled along with `reachy_sdk_server.service`. 

See section [Using services]({{< ref "/advanced/services" >}}) for more information on the services). 

You can check all ROS2 topics/services running on Reachy with:
```bash
ros2 topic list
```  
and 
```bash
ros2 service list
```  

## Launching nodes individually
The following presents what launch files can be launched, if you don't whant to use the service.
If you want to learn more about what is run by each launch file, check the README of the corresponding package.

## Controllers nodes

To control joints, fans and cameras.

### Cameras nodes
*Cameras nodes are available for full/starter kit only:*  

To launch the **camera view** node ROS services:
```bash
ros2 launch reachy_controllers camera_publisher.launch.py
```
To launch the **camera zoom** node ROS services:
```bash
ros2 launch reachy_controllers camera_zoom_service.launch.py
```

To launch **all reachy_controllers** nodes related to the **cameras** ROS services:
```bash
ros2 launch reachy_controllers camera_controller.launch.py
```

To launch the **camera focus** node ROS services:
```bash
ros2 launch reachy_focus camera_focus.launch.py
```

### Joints nodes
To launch the node related to the **motors** and **fans** ROS services:
```bash
ros2 launch reachy_controllers joint_state_controller.launch.py
```

### All controllers nodes
To launch **all** controllers nodes related to ROS services at once:
```bash
ros2 launch reachy_controllers reachy_controllers.launch.py
```

Use `reachy_msgs` to interact with the services. Examples are available [here](https://github.com/pollen-robotics/reachy_controllers/tree/master/examples).

{{< alert icon="💡" text="At this level, joints angles are handled in radians." >}}


## Kinematics nodes

Kinematics services are available to provide inverse and forward kinematics services for the arms, as well as inverse kinematics for Orbita, the spherical joint used in Reachy's neck.  

Launch files are available to start the ROS services you need:  

To launch **description** service with URDF (required by the kinematics services):
```bash
ros2 launch reachy_kinematics description.launch.py
```

To launch **arms** ROS services:
```bash
ros2 launch reachy_kinematics arm_kinematics.launch.py
```

To launch **orbita** ROS services *(full/starter kit only)*:
```bash
ros2 launch reachy_kinematics orbita_kinematics_service.launch.py
```

To launch **all** kinematics ROS services at once:
```bash
ros2 launch reachy_kinematics kinematics.launch.py
```

## Mobile base

To launch the mobile base Hardware Abstraction Layer node:
```bash
ros2 launch zuuu_hal hal.launch.py
```
Many parameters on the mobile base like the maximum velocity can only be tuned at the ROS level. Check the [mobile base's HAL README](https://github.com/pollen-robotics/zuuu_hal) to learn about what you can do with the mobile base at the ROS level. 

## SDK server nodes

A layer above ROS, you can interact with **Reachy SDK API**. The Python SDK offers a gRPC (Remote Procedure Call) interface to communicate with the server.  
To communicate with Reachy through the SDK, you need to launch server nodes that handle gRPC services.  

To launch the node for the **joints, fans and kinematics** gRPC services:
```bash
ros2 launch reachy_sdk_server reachy_sdk_server.launch.py
```

To launch the node for the **cameras view and zoom** gRPC services *(full/starter kit only)*:
```bash
ros2 launch reachy_sdk_server camera_server.launch.py
```

To launch **all** nodes for gRPC services:
```bash
ros2 launch reachy_sdk_server reachy_camera_sdk_server.launch.py
```

> Note: For the servers to work, the required ROS services must be already launched. `reachy_sdk_server` requires all kinematics and controllers ROS nodes (for joints and cameras). 

{{< alert icon="💡" text="At this level, joints angles are handled in radians." >}}

To launch the node for the **mobile base** gRPC services *(mobile kit only)*:
```bash
ros2 launch mobile_base_sdk_server mobile_base_sdk_server.launch.py
```