---
title: "Commands (legacy version)"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
weight: 640
toc: true
hidden: true
---

## Controllers input

|Input|  |  |Action|
|-----------------|--|--|------|
|**Valve Index**|**HTC Vive**|**Oculus Touch**||
|Controllers positions|Controllers positions|Controllers positions|**Reachy's end effectors positions**|
|Trigger (squeeze)|Trigger (squeeze)|Index Trigger (squeeze)|**Open/Close adaptative gripper**|
|Trigger (press)|Trigger (press)|Trigger (press)|**Interact with UI**|
|Grip (squeeze)| / |Hand Trigger (squeeze)|**Open/Close adaptative gripper**|
|Right thumb stick (press)|Right trackpad (press)|Right thumb stick (press)|**Change commands type**|
|Right thumb stick (direction)|Right trackpad (direction)|Right thumb stick (direction)|**Select corresponding command**|
|A button (press)|Menu button (press)|A/X button (press)|**Click when required by the interface**|
|Both A buttons (press)|Both menu buttons (press)|Both A/X buttons (press)|**Emergency stop**|

**Thumb stick available command types:**
* antennas emotion using the emoji panel control (by default)
* cameras zoom/dezoom using zoom panel control *(only in 2D and 3D Views)*

|Direction|Emoji panel control|Zoom panel control|
|:--------|:-----------------:|:----------------:|
||{{< img alt="App menu" src="emoji.JPG" width="600px" >}}|{{< img alt="App menu" src="zoom.JPG" width="600px" >}}|
|**Up**|Happy|Zoom|
|**Right**|Thinking|/|
|**Down**|Sad|Dezoom|
|**Left**|Angry|/|

## Menu options

{{< img alt="App menu" src="menu-connected.png" width="600px" >}}

### Mode
**See Reachy:** The 3D-robot model is either:  
* fixed in a immovable position on its support in the basic scene
* not visible if you see Reachy's view (2D or 3D View)  

{{< img alt="See Reachy" src="view-scene-only.PNG" width="600px" >}}

**Be reachy:** set 3D-robot model as your own body  
{{< img alt="Be Reachy" src="be-reachy.PNG" width="600px" >}}

**Use no headset:** deactivate the headset tracking so that Reachy’s head won’t follow your head movements  

### View
**2D View:** display Reachy’s left camera on a screen in the headset  

{{< img alt="Be Reachy" src="image-emoji.PNG" width="600px" >}}

**3D View (experimental):** display Reachy’s stereoscopic view in the headset

**Mirror view:** display mirrors in front of the 3D-robot model  
{{< img alt="Be Reachy" src="mirror.PNG" width="600px" >}}

**Scene only:** basic scene (by default)

### Motors compliance
**Compliant:** set robot’s motors compliant, which means that they can be manually moved. **Warning:** you won’t be able to teleoperate Reachy with motors in compliant mode.  

**Stiff:** set robot’s motors stiff, which means that they cannot be manually moved anymore. Motors need to be in stiff mode to teleoperate Reachy.  

{{< alert icon="👉" text="Motors need to be in <b>stiff</b> mode to teleoperate Reachy." >}}

### Haptics on/off (experimental)

## Emergency stop

Activate emergency stop by clicking on:
* both A buttons at the same time for Valve Index controllers
* both menu buttons for Vive controllers
* both A/X buttons for Oculus Touch.  


{{< img alt="Emergence stop menu" src="security-stop.PNG" width="600px" >}}

The following options are available:
* **Open grippers:** immediately open the gripper as much as possible to enable the release of any object.
* **Reduce torque:** reduce the resistance of the arms motors. The arms will slighty fall down.
* **Set motors compliant:** switch all arms and neck motors into compliant mode.
* **Restart application:** come back to the very beginning of the application (select IP from interface)
