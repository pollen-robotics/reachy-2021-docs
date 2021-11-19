---
title: "Reachy packages"
description: "Which packages are available and where they are stored."
lead: "Which packages are available and where they are stored."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  advanced:
    parent: "software"
weight: 310
toc: true
---

Reachy runs on **ROS 2 version Foxy**, which should now be installed and configured on your computer.  

You have 2 main folders that contain all the packages you need to control Reachy.

## *reachy_ws/src* folder
This folder contains all the ROS packages used with Reachy:  
* reachy_msgs: [https://github.com/pollen-robotics/reachy_msgs](https://github.com/pollen-robotics/reachy_msgs)  
* reachy_sdk_server: [https://github.com/pollen-robotics/reachy_sdk_server](https://github.com/pollen-robotics/reachy_sdk_server)  
* reachy_controllers: [https://github.com/pollen-robotics/reachy_controllers](https://github.com/pollen-robotics/reachy_controllers)  
* reachy_kinematics: [https://github.com/pollen-robotics/reachy_kinematics](https://github.com/pollen-robotics/reachy_kinematics)  

*Added in latest versions:*
* reachy_description: [https://github.com/pollen-robotics/reachy_description](https://github.com/pollen-robotics/reachy_description)
* reachy_focus: [https://github.com/pollen-robotics/reachy_focus](https://github.com/pollen-robotics/reachy_focus)  

## *dev* folder
This folder contains all the packages used with Reachy that are not based on ROS:  
* reachy_pyluos_hal: [https://github.com/pollen-robotics/reachy_pyluos_hal](https://github.com/pollen-robotics/reachy_pyluos_hal)  
* reachy-sdk-api: [https://github.com/pollen-robotics/reachy-sdk-api](https://github.com/pollen-robotics/reachy-sdk-api)  
* reachy-sdk: [https://github.com/pollen-robotics/reachy-sdk](https://github.com/pollen-robotics/reachy-sdk)  
* zoom_kurokesu *(full/starter kit only)*: [https://github.com/pollen-robotics/zoom_kurokesu](https://github.com/pollen-robotics/zoom_kurokesu)  


***To learn more on the packages content and usage, please refer to README.md files of each directory.***  

{{< alert icon="👉" text="Want to get the latest software updates?</br><b><a href=\"https://pollen-robotics.github.io/reachy-2021-docs/docs/update/\" target=\"_blank\" rel=\"noopener noreferrer\">Check how to do it here!</a></b>" >}}

## Packages interactions

{{< img alt="Packages interactions" src="Diagramme Reachy.jpg" >}}