---
title: "Focus a camera manually"
description: ""
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
toc: true
hidden: true
---

If for some reason the autofocus implemented in Reachy did not work (due to dust in the lens for example), it is possible to focus the camera by hand. To do that, first connect to Reachy using reachy-sdk:

```python
from reachy_sdk import ReachySDK

reachy = ReachySDK('your-reachy-ip-address')
```

## Changing the focus with the PythonSDK

Once connected, let's say you want to make the focus of the left camera. You will need to change the focus value by hand. You can have access to it with:

```python
reachy.left_camera.focus
```

The returned value will be between 0 and 500.  You can also set the focus with the same attribute. For example to set the focus to 300:

```python
reachy.left_camera.focus = 300
```

As for the zoom value of the camera, it is between 0 and 600 and can be accessed similarly:

```python
reachy.left_camera.zoom
```

There is an empirical relationship between the focus value needed to have a clear image and the zoom value of the camera (270 by default). The focus value is inversely proportional with the zoom, meaning that when you set a high zoom value (e.g. 500), the focus value required to have a clear image will be low (between 0 and ~100).

The procedure to make the autofocus by hand is to visualize the image from the left camera and change the focus value at the same time with the PythonSDK until the image looks clear enough. The image from the left camera can be visualized using *view_cam_sdk.py*:

```bash
cd ~/dev/reachy-sdk/reachy_sdk/examples
python3 view_cam_sdk.py left --ip_address='your-reachy-ip-address'
```
(you can exit the window opened by this script by pressing 'q')

## Disabling autofocus at boot

TODO: update ?

Once the focus correctly made, we suggest to remove the autofocus from being done automatically everytime you boot Reachy, if this is not already the case. This is done by commenting the lines 25 to 27 of the file *camera_zoom_service.py* of reachy_controllers 

```python
# for side in ('left', 'right'):
    # self.controller.homing(side)
    # self.controller.set_zoom_level(side, default_zoom_level)
```
and line 204 of the same file:

```python
# zoom_controller_service.start_autofocus()
```

Don't forget to rebuild the ROS package so that the changes are taken into account:

```bash
cd ~/reachy_ws
colcon build --symlink-install
source ~/.bashrc
```