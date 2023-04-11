---
title: "Manage Reachy's services"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  advanced:
    parent: "services"
weight: 510
toc: true
---
The following commands are taken from [systemd documentation](https://www.freedesktop.org/wiki/Software/systemd/). For more details, don't hesitate to check the documentation directly.

## Start, restart or stop a service
Eachy Reachy's services can be started, stopped or restarted by hand. It can be useful for situations where for example you turned Reachy's computer on but forgot to turn on its motors. By restarting *reachy_sdk_server.service*, you would not have to reboot Reachy's computer.

To start a specific service like [*reachy_sdk_server.service*]({{< ref "/advanced/services/available#reachy_sdk_serverservice" >}}), type the following command in a terminal:
```bash
systemctl --user start reachy_sdk_server.service
```

Similarly, you can stop or restart a specific service by replacing the start keyword by either stop or restart.
For example, to restart reachy_sdk_server.service, the command is:
```bash
systemctl --user restart reachy_sdk_server.service
```

> Note: if you stop a service, it will start again automatically at the next boot of Reachy's computer. If you would prefer to always have the service stopped, you will have to [disable]({{< ref "/advanced/services/manage-services#enable-or-disable-a-service" >}}) it.

## Get a service status
Having a service's status can be really useful for debugging. With it you can know whether the service is active or not and especially, you can have access to the latest logs of the service. For example if you can't connect to your Reachy or the mobile base with the Python SDK, there is probably a message in the service explaining why the code has crashed.

To get the status of a service like *reachy_sdk_server.service*, use

```bash
systemctl --user status reachy_sdk_server.service
```

## Enable or disable a service
There are situations when you would prefer to disable a service completely so that it is never started when Reachy's computer is booting. It might be for example because you would prefer to start Reachy's ROS code by hand to have a finer control on it.

If that is the case, you can disable a service like *reachy_sdk_server.service* with

```bash
systemctl --user disable reachy_sdk_server.service
```

At any time, if you prefer to work with the service again, you can enable it.

```bash
systemctl --user enable reachy_sdk_server.service
```
