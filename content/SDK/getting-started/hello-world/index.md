---
title: "Hello World"
description: ""
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
menu:
  SDK:
    parent: "getting-started"
weight: 130
toc: true
---

Now you should be able to connect to your Reachy and check that everything is ok. As we spoiled in the previous section, to connect to your robot, you simply need to run the following code:

```python
from reachy_sdk import ReachySDK

# Replace with the actual IP you've found.
reachy = ReachySDK(host='the.reachy.ip.found.')
```

Before diving into the next chapters that will guide you in the depth of what you can do with the Reachy SDK, here is a quick preview.

## Getting joints state

To make sure everything is working fine, let's check the position of its joints. We won't go into details here as we will detail everything later.

To get the state of a joint, you can access the *joints* attribute that contains all joints and iterate over its content:

```python
for name, joint in reachy.joints.items(): 
    print(f'Joint "{name}" is at pos {joint.present_position} degree.') 
```

Will show something like:
```python
Joint "l_shoulder_pitch" is at pos -3.6 degree.
Joint "l_shoulder_roll" is at pos 1.5 degree.
Joint "l_arm_yaw" is at pos -3.1 degree.
Joint "l_elbow_pitch" is at pos 2.0 degree.
Joint "l_forearm_yaw" is at pos -54.4 degree.
Joint "l_wrist_pitch" is at pos -0.9 degree.
Joint "l_wrist_roll" is at pos -20.7 degree.
Joint "l_gripper" is at pos 43.0 degree.
Joint "r_shoulder_pitch" is at pos 0.8 degree.
Joint "r_shoulder_roll" is at pos 0.5 degree.
Joint "r_arm_yaw" is at pos 1.2 degree.
Joint "r_elbow_pitch" is at pos 0.1 degree.
Joint "r_forearm_yaw" is at pos 0.1 degree.
Joint "r_wrist_pitch" is at pos 1.1 degree.
Joint "r_wrist_roll" is at pos 4.5 degree.
Joint "r_gripper" is at pos -0.7 degree.
Joint "l_antenna" is at pos -1.9 degree.
Joint "r_antenna" is at pos -3.7 degree.
Joint "neck_roll" is at pos -20.1 degree.
Joint "neck_pitch" is at pos -14.1 degree.
Joint "neck_yaw" is at pos -48.0 degree.
```

Note that we have accessed the attribute *present_position* to get the joint actual position. You can access the position of a specific joint by using its full name (meaning the part it is attached to plus its name). For instance, to get the position of the 'left shoulder pitch':

```python
>>> print(reachy.l_arm.l_shoulder_pitch.present_position)
-3.6
```

You can also get a resume of the joint state by doing:
```python
>>> print(reachy.l_arm.l_shoulder_pitch)
<Joint name="l_shoulder_pitch" pos="-3.58" mode="compliant">
```

If you did not run anything else, your robot should be compliant (meaning you can freely move it). You can try to move it and re-run the code above. You should see that without doing anything specific, the positions are automatically updated.

## Seeing what Reachy sees

Assuming, you are still connected (otherwise, simply reconnect), we will now display what Reachy sees as an [OpenCV window](https://opencv.org). 

```python
import cv2 as cv

while True:
    # This let you access the last frame grabbed by Reachy left eye
    # It's always the most up-to-date image
    left_image = reachy.left_camera.last_frame

    cv.imshow('left image', left_image)
    cv.waitKey(30)
```

You should now see what Reachy sees!

To stop the code, press Ctrl-C.

