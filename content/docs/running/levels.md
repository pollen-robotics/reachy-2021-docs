---
title: "Levels of services"
description: "The robot offers several levels of services. Depending on your use case, you may prefer interacting with different layers of the robot software."
lead: "The robot offers several levels of services. Depending on your use case, you may prefer interacting with different layers of the robot software."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "running"
weight: 720
toc: true
---

If you have a **Full kit**, `reachy_sdk_server.service` is enabled by default, which means that all services and levels of services are automatically available when you start the robot (see section [Using services]({{< ref "services" >}}) for more information on the services).

## ROS level
The robot is based on **ROS 2 version Foxy**, which is used as the base of all our other services.
You can see all ROS2 running services with:
```bash
ros2 service list
```  

### Launch kinematics services
Kinematics services are available to provide inverse and forward kinematics services for the arms, as well as inverse kinematics for Orbita.  

Launch files are available to start the ROS services you need:  

To launch **arms** ROS services:
```bash
ros2 launch reachy_kinematics description.launch.py
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

### Launch controllers services
Controllers services enable to control joints, fans and cameras.

#### Cameras nodes
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

#### Joints nodes
To launch the node related to the **motors** and **fans** ROS services:
```bash
ros2 launch reachy_controllers joint_state_controller.launch.py
```

#### All controllers nodes
To launch **all** controllers nodes related to ROS services at once:
```bash
ros2 launch reachy_controllers reachy_controllers.launch.py
```

Use `reachy_msgs` to interact with the services. Examples are available in `reachy_ws/src/reachy_controllers/examples`, or following the link: [https://github.com/pollen-robotics/reachy_controllers/tree/master/examples](https://github.com/pollen-robotics/reachy_controllers/tree/master/examples).

{{< alert icon="💡" text="At this level, joints angles are handled in radians." >}}


## SDK API
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



## Python SDK
The highest level of interaction is through **Reachy Python SDK**. Everything is handled in a simple and understandable way to interact with the different features of Reachy.

From any computer, connect to Reachy in a simple line:
```python
from reachy_sdk import ReachySDK

reachy = ReachySDK(host=’192.168.86.20’) # use your own IP
```


Access to all parts and functionalities of Reachy using our custom commands.  
Examples of use are available in `dev/reachy-sdk/notebooks` or following the link: [https://github.com/pollen-robotics/reachy-sdk/](https://github.com/pollen-robotics/reachy-sdk/).


{{< alert icon="💡" text="At this level, joints angles are handled in degrees." >}}

**Ready to start using the Python SDK? Check out [Reachy Python SDK documentation](https://pollen-robotics.github.io/reachy-2021-docs/sdk/getting-started/introduction/)!**  

*Haven’t installed all the required packages on your remote computer? See section [Use Reachy SDK]({{< ref "use-sdk" >}}) for the details.*
