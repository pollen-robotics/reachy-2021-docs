---
title : "Quick Debug"
description: "Quick Debug"
lead: ""
date: 2020-10-06T08:48:23+00:00
lastmod: 2020-10-06T08:48:23+00:00
draft: false
images: []
menu:
  help:
    parent: help
weight: 100
toc: true
---

## A few checks you can go through

### Check the service status
*If you are using one of the system.d service only:*  
{{< alert icon="💡" text="Note: By default, reachy_sdk_server.service should be running." >}}  


Open a terminal on the computer, and enter:
```bash
sudo systemctl status <name_of_the_service>.service
```

The service should indicate ⬤ active (running) as shown below:
If the service is not active, start it with:
```bash
sudo systemctl start <name_of_the_service>.service
```
Get [more information on Reachy system.d services here](https://docs.pollen-robotics.com/advanced/services/)
An error may be indicated in the terminal.

### Check ROS topics
Open a terminal on the computer, and enter:
```bash
ros2 topic list
```

If all services are launched, you should see the following list:  

**Full/Starter kit topic list:**
```bash
/fan_states
/force_sensors
/joint_goals
/joint_states
/joint_temperatures
/left_image
/parameters_events
/right_image
/robot_description
/rosout
/tf
/tf_static
```

**Arm kit topic list:**
```bash
/fan_states
/force_sensors
/joint_goals
/joint_states
/joint_temperatures
/parameters_events
/robot_description
/rosout
/tf
/tf_static
```

### Check the topics are correctly updated
Open a terminal on the computer, and enter:
```bash
ros2 topic echo <topic_name>
```

Check the topic is updated: it should print new logs at given frequencies.

Note: the list of topics names is available using `ros2 topic list`

### Check ROS logs
Everytime you use ROS nodes, the logs are saved.
In `~/.ros/log`, you can find the files containing all logs of your sessions.

You can see if you got an error with one of your ROS nodes.

## Check all the robots elements are well detected
If during your previous check you detected anything that seem anormal (you saw fewer topics than expected), it may happen that a wire got unplugged. 

To check which motors are detected:
1. You need to stop the service which is running. Open a terminal and enter:
```bash
sudo systemctl stop reachy_sdk_service.service
```
2. You need to make a discovery to see which parts of Reachy a detected:
```bash
cd ~/dev/reachy_pyluos_hal
python3 -m reachy_pyluos_hal.discovery
```

You should see the following elements:
* 1 gate
* *if your robot has a right arm*:
  * 8 dxl motors from id 10 to 17
  * 1 force sensor with id ??
* *if your robot has a left arm*:
  * 8 dxl motors from id 20 to 27
  * 1 force sensor with id ??
* *if your robot has a head*:
  * 2 dxl motors of id 30 and 31

In case an element which should appear is missing, it is very likely you got a wire unplugged. Check the connections of the cables around the part where all elements are not detected.

3. If you managed to plug back an element you found unplugged, relaunch the discovery described in point 2 to check it is correctly detected now.

4. Restart the sevice:
```bash
sudo systemctl start reachy_sdk_service.service
```