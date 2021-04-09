---
title: "Teleoperate Reachy"
description: ""
lead: "How to use the VR teleoperation application"
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  VR:
    parent: "use-teleop"
weight: 30
toc: true
---

## In brief

### Start teleoperating Reachy

1. Make sure the robot is turned on, connected to the network and that all the robot's services are running before launching the teleoperation application.

2. Enter your robot's IP address **on the computer** at the launch of the app.

3. Turn the motors **stiff** in the menu for the robot to be able to move.

4. After having clicked "Validate my choices", **look straight ahead, with your body in the same orientation as your head while pressing A.** *The initial head position is used to determine the coordinate system giving your VR controllers position.* 

{{< alert icon="👉" text="<b>Warning:</b> you <b>cannot move</b> anymore after this step. The position of your VR controllers to master the robot arms are calculated depending on the position you had while pressing A." >}}
<br></br>

5. Come back any time to menu by pressing A. Teleoperation of the robot is automatically paused if the menu is open. You can move to another place in menu.

### Stop teleoperation

1. Come back to the **menu** to pause the teleoperation.  

2. Leave the app by clicking "**Quit**".  

You can switch the motors into compliant mode before turning the app off. If you do so, make sure the arm are close enough to the lowest position they can reach to avoid them falling or hitting something.  

In case you need an immediate and definitive stop with more control on the options for the arms release, use the [emergency stop option]({{< ref "stop" >}}).

## Step-by-step starting
1. Prepare your VR equipment to be VR ready: turn on all VR device, make sure they are correctly detected by SteamVR.  
  *For Oculus Quest users:*
  You need to launch the Oculus application before starting the teleoperation application.  

2. Make sure the robot is turned on, connected to the network and that all the robot services are running. *By default, if you haven't modified anything, all services should be automatically launched on start of the **full/starter kit** robots.*

3. Launch the application .exe file

4. **On your computer:**
Connect to your Reachy IP: you need to add or select an IP address to connect to your Reachy robot
{{< img alt="Select IP" src="select-ip.PNG" width="600px" >}}
5. Equip yourself with your headset, make sure you can see both controllers and that the scene is moving correctly in accordance with your head movements.

6. Press A to enter the Menu
{{< img alt="Enter app" src="enter-teleop.PNG" width="600px" >}}
7. Make sure the connection status in the top right of the menu is indicating "You are connected to a remote Reachy".
{{< img alt="Start robot" src="menu-connected.PNG" width="600px" >}}
8. Choose the mode and view you want. 

9. Turn the motors **stiff**, then click “Validate my choices”

10. Choose the place you want to teleoperate Reachy from, position your hand in the posture you want to begin with.
**Look straight ahead, with your body in the same orientation as your head while pressing A.** The initial head position is used to determine the coordinate system giving your VR controllers position.  
{{< img alt="Start robot" src="start-robot.PNG" width="600px" >}}

{{< alert icon="👉" text="<b>Warning:</b> you <b>cannot move</b> anymore after this step. The position of your VR controllers to master the robot arms are calculated depending on the position you had while pressing A." >}}
<br></br>

11. Come back any time to menu by pressing A. Teleoperation of the robot is automatically paused if the menu is open. You can move to another place until you validate a position.
