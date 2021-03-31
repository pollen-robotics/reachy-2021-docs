---
title: "Which packages to use?"
description: "The robot offers several levels of services. Depending on your use case, you may prefer interacting with different layers of the robot software."
lead: "The robot offers several levels of services. Depending on your use case, you may prefer interacting with different layers of the robot software."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  advanced:
    parent: "ros2"
weight: 720
toc: true
---

If you have a **Full kit**, `reachy_sdk_server.service` is enabled by default, which means that all Reachy ROS2 packages are automatically launched when you start the robot (see section [Using services]({{< ref "services" >}}) for more information on the services).

## What is running?
You can check all ROS2 topics/services running on Reachy with:
```bash
ros2 topic list
```  
and 
```bash
ros2 service list
```  

If you want finer control of which packages should run on your Reachy, see the section [Using services]({{< ref "services" >}}).

## Launch kinematics services

Kinematics services are available to provide inverse and forward kinematics services for the arms, as well as inverse kinematics for Orbita.  

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

## Launch controllers services
Controllers services enable to control joints, fans and cameras.

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

To launch **all** nodes related to the **cameras** ROS services:
```bash
ros2 launch reachy_controllers camera_controller.launch.py
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

Use `reachy_msgs` to interact with the services. Examples are available in `reachy_ws/src/reachy_controllers/examples`, or following the link: [https://github.com/pollen-robotics/reachy_controllers/tree/master/examples](https://github.com/pollen-robotics/reachy_controllers/tree/master/examples).

{{< alert icon="💡" text="At this level, joints angles are handled in radians." >}}


## SDK API Server

A layer above ROS, you can interact with **Reachy SDK API**. Reachy offers a gRPC (Remote Procedure Call) interface to communicate with the SDK.  
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

Note: For the servers to work, the required ROS services must be already launched. `reachy_sdk_server` requires all kinematics and controllers ROS nodes (for joints and cameras). 


{{< alert icon="💡" text="At this level, joints angles are handled in radians." >}}

