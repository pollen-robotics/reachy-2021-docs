---
title: "Full/Starter kit services"
description: "One page summary of how to start a new Doks project."
lead: "One page summary of how to start a new Doks project."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "running"
weight: 710
toc: true
---

Reachy runs on **ROS 2 version Foxy**, which you should have installed and configured on your computer.  

You have 2 main folders that contain all the packages you need to control Reachy.

## `reachy_ws/src` folder
This folder contains all the ROS packages used with Reachy:  
[https://github.com/pollen-robotics/reachy_msgs](https://github.com/pollen-robotics/reachy_msgs)  
[https://github.com/pollen-robotics/reachy_sdk_server](https://github.com/pollen-robotics/reachy_sdk_server)  
[https://github.com/pollen-robotics/reachy_controllers](https://github.com/pollen-robotics/reachy_controllers)  
[https://github.com/pollen-robotics/reachy_kinematics](https://github.com/pollen-robotics/reachy_kinematics)  

## `dev` folder
This folder contains all the packages used with Reachy that are not based on ROS:  
[https://github.com/pollen-robotics/reachy_pyluos_hal](https://github.com/pollen-robotics/reachy_pyluos_hal)  
[https://github.com/pollen-robotics/reachy-sdk-api](https://github.com/pollen-robotics/reachy-sdk-api)  
[https://github.com/pollen-robotics/reachy-sdk](https://github.com/pollen-robotics/reachy-sdk)  
[https://github.com/pollen-robotics/zoom_kurokesu](https://github.com/pollen-robotics/zoom_kurokesu)  


***To learn more on the packages content and usage, please refer to README.md files of each directory.***


{{< alert icon="💡" text="Reachy’s services communicate on port 50050 to 50060." >}}
