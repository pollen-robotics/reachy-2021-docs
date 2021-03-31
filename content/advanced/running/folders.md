---
title: "Installed packages"
description: "One page summary of how to start a new Doks project."
lead: "Which packages are available and where they are stored."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  advanced:
    parent: "running"
weight: 710
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

## *dev* folder
This folder contains all the packages used with Reachy that are not based on ROS:  
* reachy_pyluos_hal: [https://github.com/pollen-robotics/reachy_pyluos_hal](https://github.com/pollen-robotics/reachy_pyluos_hal)  
* reachy-sdk-api: [https://github.com/pollen-robotics/reachy-sdk-api](https://github.com/pollen-robotics/reachy-sdk-api)  
* reachy-sdk: [https://github.com/pollen-robotics/reachy-sdk](https://github.com/pollen-robotics/reachy-sdk)  
* zoom_kurokesu *(full/starter kit only)*: [https://github.com/pollen-robotics/zoom_kurokesu](https://github.com/pollen-robotics/zoom_kurokesu)  


***To learn more on the packages content and usage, please refer to README.md files of each directory.***


{{< alert icon="💡" text="Reachy’s services communicate on port <b>50050 to 50060</b>." >}}
