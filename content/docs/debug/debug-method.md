---
title: "Debugging"
description: "Something is not working: how to debug it."
lead: "Something is not working: how to debug it."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "debug"
weight: 900
toc: true
---

## Check the service status
If you are using one of the system.d service only:

Open a terminal on the computer, and enter:
```bash
sudo systemctl status <name_of_the_service>.service
```

Note: Default running service is reachy_sdk_server.service.

An error may be indicated in the terminal.

## Check ROS topics
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

## Check the topics are correctly updated
Open a terminal on the computer, and enter:
```bash
ros2 topic echo <topic_name>
```

Check the topic is updated: it should print new logs at given frequencies.

Note: the list of topics names is available using `ros2 topic list`

## Check ROS logs
Everytime you use ROS nodes, the logs are saved.
In `~/.ros/log`, you can find the files containing all logs of your sessions.

You can see if you got an error with one of your ROS nodes.
