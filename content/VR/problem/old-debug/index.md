---
title: "Legacy Debug"
description: ""
lead: "Debugging teleoperation problems"
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
weight: 650
toc: true
hidden: true
---

## The app doesn't connect to the robot
{{< img alt="App menu" src="menu-not-connected.PNG" width="600px" >}}
If you are not connected to the robot, the reason can be one of the following:
* you are not connected to the right IP address
* the robot is not connected to the network
* the services are not working on the robot (either not launched or crashed)
* your computer is not connected to the network
* the connection is not stable enough for the app to stay connected to the robot

## The robot doesn't move at all
**Check if the app is connected to the robot**  
First of all, check that the application managed to connect to the robot.  
The connection status with the robot is indicated at the top of the menu.
Functionalities are disabled on the interface.  
See [previous section]({{< ref "vr/problem/debug#the-app#doesnt-connect-to-the-robot" >}}) if you are not connected to the robot.  

|Connected to the robot|Unable to connect to the robot|
|----------------------|------------------------------|
|{{< img alt="App menu" src="menu-connected.PNG" width="600px" >}}|{{< img alt="App menu" src="menu-not-connected.PNG" width="600px" >}}|


**Check you turned the motors into stiff mode**  
You cannot teleoperate the robot if the motors are compliant.  
Make sure you have correctly turned the motors stiff in the menu.  
{{< img alt="Stiff mode" src="stiff-mode.PNG" width="600px" >}}

## The robot doesn't move properly
**Reachy movements are shifted from my real movements**  
Your head was probably not correctly aligned with your body when you fixed your position, or you moved since the validation step.  
Come back to menu and validate your choices again to be able to fix a new position.  

**Reachy movements are jerky**  
The connection is not fast enough between the robot and your computer, or another program may be alterating the reactivity.

## I have no image in 2D or 3D view
The camera services may not be working on the robot. Launch the corresponding services on the robot side if necessary.  