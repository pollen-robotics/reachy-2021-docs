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
weight: 220
toc: true
---

## Connect to the embedded computer

**For Full/Starter kit only:**  
Connect a screen, a mouse and a keyboard to Reachy.

{{< alert icon="👉" text="<b>Password: reachy</b>" >}}


You can also access it via ssh. You will first need to know Reachy’s IP on your network.
Then, using your own *reachy-ip* you can access it via:
```bash
ssh reachy@<reachy-ip>
```

*Don't know what is your reachy-ip? Check out [how to find the Reachy's IP]({{< ref "help/system/find-my-ip" >}}).*  


## Check ROS is providing access to the topics
Open a terminal on the computer, and enter:
```bash
ros2 topic list
```

### Full/Starter kit topic list
You should see the following list:
```bash
/antenna_forward_position_controller/commands
/antenna_forward_position_controller/transition_event
/diagnostics
/dynamic_joint_commands
/dynamic_joint_states
/forward_fan_controller/commands
/forward_fan_controller/transition_event
/forward_pid_controller/commands
/forward_pid_controller/transition_event
/forward_speed_limit_controller/commands
/forward_speed_limit_controller/transition_event
/forward_torque_controller/commands
/forward_torque_controller/transition_event
/forward_torque_limit_controller/commands
/forward_torque_limit_controller/transition_event
/gripper_forward_position_controller/commands
/gripper_forward_position_controller/transition_event
/grippers/commands
/head/averaged_target_pose
/head/target_pose
/joint_commands
/joint_state_broadcaster/transition_event
/joint_states
/kinematics/transition_event
/l_arm/averaged_target_pose
/l_arm/target_pose
/l_arm_forward_position_controller/commands
/l_arm_forward_position_controller/transition_event
/left_image/image_raw/compressed
/neck_forward_position_controller/commands
/neck_forward_position_controller/transition_event
/parameter_events
/r_arm/averaged_target_pose
/r_arm/target_pose
/r_arm_forward_position_controller/commands
/r_arm_forward_position_controller/transition_event
/right_image/image_raw/compressed
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
