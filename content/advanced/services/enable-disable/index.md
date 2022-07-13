---
title: "Enable or disable a service"
description: "Teleoperate Reachy through the VR teleoperation application."
lead: "How to manage services automatically."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  advanced:
    parent: "services"
weight: 520
toc: true
---

By enabling or disabling a service, you make it start or not automatically when turning on the robot.  

If you enable a service, the service won’t be active until you reboot your robot or manually start the service.  
If you disable a service, the service will stay active until you reboot your robot or manually stop the service.  

To **enable** a service:
```bash
sudo systemctl enable <name_of_the_service>.service
```

To **disable** a service:
```bash
sudo systemctl disable <name_of_the_service>.service
```
