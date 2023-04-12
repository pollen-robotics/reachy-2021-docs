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
weight: 642
toc: true
---

{{< warning icon="👉🏾" text="Before starting teleoperating Reachy, please make sure you read the  <b><a href=\"https://docs.pollen-robotics.com/vr/use-teleop/best-practice/\">Best Practice</a></b>" >}}

## In brief

### Start teleoperating Reachy

1. Make sure the robot is turned on, connected to the network and that all the robot's services are running before launching the teleoperation application.

2. Select the robot you want to teleoperate (or create a new one), and click on "Connect".

3. When the robot is ready, click on "Click here to start", then **look straight ahead, with your body in the same orientation as your head while pressing A** to start the teleoperation. *The initial head position is used to determine the coordinate system giving your VR controllers position.* 

{{< alert icon="👉" text="<b>Warning:</b> you <b>cannot move</b> anymore after this step. The position of your VR controllers to master the robot arms are calculated depending on the position you had while pressing A." >}}

{{< warning icon="🚨" text="<b>Important:</b> even if Reachy is bio-inspired, it cannot reproduce exactly all your movements. There are <b>positions that cannot be reached</b> by the robot. Please <b>avoid unusual movements</b> and do not persist in trying to reach a position if you see that the robot is stuck before it." >}}

5. Come back any time to menu by **pressing A**. Teleoperation of the robot is automatically paused if the menu is open. You can move to another place in menu.

{{< alert icon="👉" text="Please <b>stop teleoperation before removing your headset</b> (go back to menu or quit the app). If you do not, Reachy will continue following your controllers and headset orientation, and this can cause damages to the robot." >}}

### Stop teleoperation

1. Come back to the **menu** to pause the teleoperation by **pressing A** at any time during teleoperation.  

2. Leave the app by clicking "**Quit**" in the menu and continue with "Yes, leave.".  

The motors are automatically turned into compliant mode when not teleoperated. Please make sure the arms are close enough to the lowest position they can reach when coming back to the menu to avoid them falling or hitting something.  


## Step-by-step starting
1. Prepare your VR equipment to be VR ready: turn on all VR device, make sure they are correctly detected by SteamVR.  
  *For Oculus Quest users:*
  You need to launch the Oculus application before starting the teleoperation application.  

2. Make sure the robot is turned on, connected to the network and that all the robot services are running. *By default, if you haven't modified anything, all services should be automatically launched on start of the **full/starter kit** robots.*

3. Launch the application .exe file

4. Equip yourself with your headset, make sure you can see both controllers and that the scene is moving correctly in accordance with your head movements.

5. Choose the robot you want to connect to: you can select a robot with its IP address, or add a new one to the list of available robots.

{{< img alt="Change robot to connect" src="choose-robot.png" width="600px" >}}
{{< img alt="Select robot to connect" src="select-robot.png" width="600px" >}}

6. Press *Connect* to initiate the communication with the robot.

{{< img alt="Connect to a robot" src="connect.png" width="600px" >}}

7. Make sure the connection status in the top right of the menu is indicating "You are connected to a remote Reachy".

8. When Reachy is ready, click on "Click here to start".

{{< img alt="Start teleoperation" src="click-here-to-start.png" width="600px" >}}

9. Choose the place you want to teleoperate Reachy from, position your hand in the posture you want to begin with. C
**Look straight ahead, with your body in the same orientation as your head while pressing A.** The initial head position is used to determine the coordinate system giving your VR controllers position.  

{{< img alt="Validate position before starting" src="ready-to-start.png" width="600px" >}}

{{< alert icon="👉" text="<b>Warning:</b> you <b>cannot move</b> anymore after this step. The position of your VR controllers to master the robot arms are calculated depending on the position you had while pressing A." >}}

10. Come back any time to menu by **pressing A**. Teleoperation of the robot is automatically paused if the menu is open. You can move to another place until you validate a position.


## Application features

{{% expand "> Add a new robot" %}}
Click on the robot to select to open the panel of all saved robots:
{{< img alt="Select robot" src="choose-robot.png" width="600px" >}}
Then click on "Add new robot +" at the bottom right of the page:
{{< img alt="Add robot button" src="add-robot-button.png" width="600px" >}}
Enter a robot name and the IP address of the robot (if the headset is connected on a computer, use the computer keyboard), and save your robot card:  
*The IP address is mandatory. If no name is given to the new robot, it will be called @Reachy by default*
{{< img alt="Add robot panel" src="add-robot-card.png" width="600px" >}}
{{% /expand %}}

{{% expand "> Modify an existing robot"%}}
Click on the robot to select to open the panel of all saved robots:
{{< img alt="Select robot" src="choose-robot.png" width="600px" >}}
Then click on the pencil icon of the robot you want to modify:
{{< img alt="Modify robot button" src="modify-robot-button.png" width="600px" >}}
Modify the info on the robot card and save the card:
{{< img alt="Modify robot panel" src="modify-robot-panel.png" width="600px" >}}
{{% /expand %}}

{{% expand "> Delete a saved robot"%}}
Click on the robot to select to open the panel of all saved robots:
{{< img alt="Select robot" src="choose-robot.png" width="600px" >}}
Then click on the bin icon of the robot you want to delete:
{{< img alt="Delete robot button" src="delete-robot-button.png" width="600px" >}}
Validate the deletion:
{{< img alt="Delete robot panel" src="delete-robot-panel.png" width="600px" >}}
{{% /expand %}}

{{% expand "> Check the gRPC ports"%}}
Click on "Ports information" in the connection menu, below the Connect button.
{{< img alt="Connect page" src="connect-page.png" width="600px" >}}
Find there the info of all the gRPC ports used. You can also modify then if you made changed on your robot:
{{< img alt="Check ports information" src="port-info.png" width="600px" >}}
{{% /expand %}}

{{% expand "> Disable the automatic best practice display"%}}
Disable the "Always show on start" toggle at the bottom of the best practice page:
{{< img alt="Disable automatic best practice" src="best-practice.png" width="600px" >}}
{{% /expand %}}

{{% expand "> Refer back to the best practice"%}}
Click on the guide at the top right of the menu:
{{< img alt="Access best practice" src="guide-button.png" width="600px" >}}
{{% /expand %}}

{{% expand "> Disable the use of mobility"%}}
Go to the help menu:
{{< img alt="Access best practice" src="help-menu.png" width="600px" >}}
Switch mobility to off on the button located at the bottom left  
{{< img alt="Mobility button" src="mobility-button.png" width="600px" >}}
{{% /expand %}}
