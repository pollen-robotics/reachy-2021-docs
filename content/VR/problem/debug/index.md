---
title: "Debug"
description: ""
lead: "Debugging teleoperation problems"
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  VR:
    parent: "problem"
weight: 650
toc: true
---

## Check the info on the app!
Access the help menu to get more information on the connection status and the status of the robot.
{{< img alt="Help menu button" src="help-menu.png" width="600px" >}}
{{< img alt="Help menu" src="check-state.png" width="600px" >}}

The connection status give you information about the communication with the robot. Existing connection status are the following:
* You are connected to a remote Reachy
* Connected to a remote Reachy. No restart available
* Unable to connect to server

You can also check which services are available:
* Camera stream
* Joints data stream
* Mobility services
* Restart service

## The app doesn't connect to the robot

If you are not connected to the robot, the reason can be one of the following:
* you are not connected to the right IP address
* the robot is not connected to the network
* the services are not working on the robot (either not launched or crashed)
* your computer is not connected to the network
* the connection is not stable enough for the app to stay connected to the robot

## Reachy never comes to be ready

First of all, check that the application managed to connect to the robot.  
The connection status with the robot is indicated at the top of the menu.
Functionalities are disabled on the interface.  
See  if you are not connected to the robot.  

|Connected to the robot|Unable to connect to the robot|
|----------------------|------------------------------|
|{{< img alt="Robot connected" src="click-here-to-start.png" width="600px" >}}|{{< img alt="Unable to connect" src="unable-to-connect.png" width="600px" >}}|



## The robot doesn't move properly
**Reachy movements are shifted from my real movements**  
Your head was probably not correctly aligned with your body when you fixed your position, or you moved since the validation step.  
Come back to menu and validate your choices again to be able to fix a new position.  

**Reachy movements are jerky**  
The connection is not fast enough between the robot and your computer, or another program may be alterating the reactivity.  

{{< my-button link="/vr/problem/old-debug/" label="See legacy debug section" >}}