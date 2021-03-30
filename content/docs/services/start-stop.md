---
title: "Start/restart or stop a service"
description: "Teleoperate Reachy through the VR teleoperation application."
lead: "Teleoperate Reachy through the VR teleoperation application."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "services"
weight: 1020
toc: true
---

You can decide to start or stop at any time a service.  

If you start a service which is disabled, the service won’t be active anymore after you turn off the robot.  
If you stop a service which is enabled, the service will be active the next time you turn on the robot.  

To **start** a service:
```bash
sudo systemctl start <name_of_the_service>.service
```
To **restart** a service that was previously launched:
```bash
sudo systemctl restart <name_of_the_service>.service
```

To **stop** a service:
```bash
sudo systemctl stop <name_of_the_service>.service
```
