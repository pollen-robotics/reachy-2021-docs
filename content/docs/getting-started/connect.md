---
title: "Connect to your robot"
description: "How to connect to your robot."
lead: "How to connect to your robot."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "getting-started"
weight: 640
toc: true
---

## Connect to the embedded computer

**For Full/Starter kit only:**  
Connect a screen, a mouse and a keyboard to Reachy.

{{< alert icon="👉" text="<b>Password: reachy</b>" >}}


You can also access it via ssh. You will first need to know Reachy’s IP on your network.
Then, using your own *reachy-ip* you can access it via:
```bash
ssh nuc@<reachy-ip>
```

## Check ROS is providing access to the topics
Open a terminal on the computer, and enter:
```bash
ros2 topic list
```

### Full/Starter kit topic list
You should see the following list:
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

### Arm kit topic list
You should see the following list:
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
On a terminal on the computer, and enter:
```bash
ros2 topic echo /joint_states
```

The logs correspond to the motors positions in radians.
Try to move an arm to check they are correctly updated.


## Launch demo programs
In `~/dev/reachy-sdk/notebooks`, you can find examples of use for reachy-sdk.

Try them using jupyter:
```bash
cd ~/dev/reachy-sdk/notebooks
jupyter notebook
```

If you want to launch the notebooks while connected via ssh:
```bash
jupyter notebook --ip=0.0.0.0
```
