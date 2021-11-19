---
title: "Overall presentation"
description: "Presentation of the different components of Reachy's software and how they interact."
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  advanced:
    parent: "software"
weight: 300
toc: true
---

Reachy's software is composed of three main parts:

- **a HAL** (Hardware Abstraction Layer) handling the communication with some of Reachy's sensors i.e. the Dynamixel motors in the arms, fans, force sensors and Orbita actuator,
- **ROS packages:** this is the core of the software. We are using ROS (Robotics Operating System), more precisely the **ROS2 Foxy distribution**, to interact with the HAL, to compute the kinematics for Reachy's arms and Orbita,  to get the camera feed and to manage the autofocus on Reachy's motorised zooms.   
A ROS package is also used, along with gRPC, to create a server interacting with the different ROS nodes and services made for Reachy and allowing remote control on the robot without being physically connected to it.
    
- **gRPC client:** the strength of using the gRPC framework is that we can have a remote control to the robot and create clients in any programming language (Python, C++, C#, ...). So knowing how to use ROS is not needed to work with Reachy.

## Packages

The packages developed for Reachy 2021 are divided into two categories: the ROS packages and non-ROS packages.

### ROS 

(installed in ~/reachy_ws folder of Reachy's computer)

- [**reachy_description**](https://github.com/pollen-robotics/reachy_description): publishes the robot's URDF, needed by the kinematics package and by the different ROS simulation tools (rviz, gazebo, ...)
- [**reachy_kinematics**](https://github.com/pollen-robotics/reachy_kinematics): computes the forward / inverse kinematics of Reachy's arms and the inverse kinematics of Orbita
- [**reachy_controllers**](https://github.com/pollen-robotics/reachy_controllers): communicates with the HAL, the cameras and the zooms
- [**reachy_sdk_server**](https://github.com/pollen-robotics/reachy_sdk_server): creates two gRPC servers, *camera_server* to get the camera's images and control the motorised zooms and *reachy_sdk_server* for the joints, load sensors, fans et Orbita
- [**reachy_msgs:**](https://github.com/pollen-robotics/reachy_msgs): custom ROS messages for the different ROS services and topics
- [**reachy_focus**](https://github.com/pollen-robotics/reachy_focus): communicates with *zoom_kurokesu* to perform autofocus

### Non-ROS 

(installed in ~/dev folder of Reachy's computer)

- [**reachy_sdk_api**](https://github.com/pollen-robotics/reachy-sdk-api): services and messages for the gRPC servers
- [**reachy_sdk**](https://github.com/pollen-robotics/reachy-sdk): SDK Python to control Reachy to develop applications
- [**zoom_kurokesu**](https://github.com/pollen-robotics/zoom_kurokesu): Python library to control Reachy's motorized zooms
- [**reachy_pyluos_hal**](https://github.com/pollen-robotics/reachy_pyluos_hal): HAL as described in the first section

## gRPC clients

As explained, the gRPC clients permits to communicate with the gRPC server without being physically connected on the robot. The gRPC clients can be installed on another machine and have few requisites, there is no need for the machine to have ROS installed on it.

gRPC clients can be in different programming languages. Currently, two different clients have been developed:

- [**reachy_sdk**](https://github.com/pollen-robotics/reachy-sdk): as described above, SDK Python to control Reachy. This is the library that we use when we want to develop an app on Reachy or test a new robot
- **reachy_unity**: SDK C#. The teleoperation application has been developed using it.

<br/>

:bulb: **To learn more on the packages content and usage, please refer to README.md files of each directory.** 

<br/>

{{< alert icon="👉" text="Want to get the latest software updates?</br><b><a href=\"https://pollen-robotics.github.io/reachy-2021-docs/docs/update/\" target=\"_blank\" rel=\"noopener noreferrer\">Check how to do it here!</a></b>" >}}

## Sum up

The diagram below sums up what has been described in this page.

{{< img alt="Packages interactions" src="Diagramme Reachy.jpg" >}}