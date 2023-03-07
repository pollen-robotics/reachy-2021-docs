---
title: "Face Tracking"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  sdk:
    parent: "application"
weight: 410
toc: true
---

## What is this application

The face tracking project is an autonomous application in which Reachy will detect faces in its field of view and track the detected face that is closet to it.

This can be used as is to make demo with the robot, show the capabilities of the [Orbita actuator](http://localhost:1313/sdk/first-moves/head/#reachys-neck-orbita-actuator) or serve as a brick to build more complex and interactive applications.

The source code can be found in the [reachy-face-tracking](https://github.com/pollen-robotics/reachy-face-tracking) GitHub repository.

## How to install and run the application

### Install

Clone the repository and install it on your Reachy with pip.

```bash
cd ~/dev
git clone https://github.com/pollen-robotics/reachy-face-tracking.git
cd reachy-face-tracking
pip3 install -e .
```

### Run the application
You can run the application directly with Python.
```bash
cd ~/dev/reachy-face-tracking
python3 -m reachy-face-tracking.face_tracking_launcher
```

Or call ***launch.bash***

```bash
cd ~/dev/reachy-face-tracking
bash launch.bash
```

What this bash file does is just making sure that [reachy_sdk_server.service](https://docs.pollen-robotics.com/advanced/services/available/#reachy_sdk_serverservice) (Reachy’s core code) is started and calling the application with the Python command given above.

### Define service
You can also setup a service to start the application automatically at boot or to control the application directly with the [dashboard](https://docs.pollen-robotics.com/dashboard/introduction/introduction/).

To do that, just use the provided bash file.
```bash
cd ~/dev/reachy-face-tracking
bash setup-service.bash
```
However be careful if you start the application automatically at boot, make sure that someone is still around in case the head makes an unexpected movements.

**We recommend to play a few times with the application using the Python calling before using the service, to be familiar with the face tracking.**

## Good practice

- **Don't let it run for hours**. With time, the neck motors will heat. A break from time to time (at least 10 min each hour) to let the motors cool down a bit will help them.
- **Use the face detection tester script** to check if the system can correctly detect faces.

## How it is working

To explain briefly how the application is working. 

The application is basically a loop composed of three steps:

1. We grab Reachy’s last frame available from the right camera
2. For this frame, we use Reachy’s Edge TPU to infer if there are faces or not, using a face detection model [provided by Google](https://coral.ai/models/object-detection/).
3. If no faces are detected in the frame, then the head does nothing. </br>
  If faces are actually detected, we check the size of the window for each face. If the size is less than the *tracking_threshold*, then we ignore the face. This prevent from tracking people too far. You can check what how the *tracking_threshold* applies With the face detection tester script.
  For the remaining faces, we pick the one whose detection window is the biggest and we control Orbita (Reachy’s neck) so that the center of the face gets in the center of the image.