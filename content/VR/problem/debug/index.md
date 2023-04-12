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
* **Connected to a remote Reachy** *(green)*: everything seems to be working fine
* **Connected to a remote Reachy. No restart available** *(yellow)*: you do not have access to the restart service, but can use normally teleoperation
* **Connected to a remote Reachy. Mobile base unavailable** *(purple)*: the configuration of your robot declares a mobile base, but no mobility service is available. You can still teleoperate the robot with no mobility.
* **Trying to connect** *(blue)*: the app is looking for the connection with the robot
* **Robot connection failed** *(orange)*: you are connected to a remote robot, but either the camera feed or the data stream failed. Teleoperation is not possible
* **Unable to connect to remote server** *(red)*: no robot or service is detected after trying to connect

You can also check which services are available:
* **Camera stream**: camera service from the cameras. ***Mandatory for teleoperation (except for single arm configuration)***
* **Joints data stream**: joints services for sending and receiving data from the robot's joints. ***Mandatory for teleoperation***
* **Mobility services**: services to control the mobile base, available only on robots equipped with a mobile base
* **Restart service**: service to ask for a restart of the camera and joints services on the robot

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

## The mobile base doesn't move
Several elements can make the mobile base unreactive to your inputs.  
* If you are too close to a wall or object, the LIDAR anti-collision safety unables the mobile base to go closer to the obstacle. The mobile base will therefore not move in this direction, but you can still go in other directions. [More information on the anti-collision safety](https://docs.pollen-robotics.com/sdk/mobile-base/safety/)
* The mobility button has been disabled: to check the status of the mobility button, go in the help panel in the menu (welcome page). Set the mobility to ON.
{{< img alt="Mobility button" src="mobility-button.png" width="600px" >}}
* The mobility services are unavailable: check the status of the service in the help panel of the menu. The status of the mobility services is displayed in the Connection Status section. 
* The configuration of your robot does not declare a mobile base, therefore the teleoperation application does not provide any mobility service. Check if a mobile base is expected in the Robot detected configuration section.
|Mobile base is declared and mobility services are available|No mobile base is declared|
|----------------------|------------------------------|
|{{< img alt="Mobile base services on" src="mobile-base.png" width="600px" >}}|{{< img alt="No mobile base" src="check-state.png" width="600px" >}}|
