---
title: "Available system services"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  advanced:
    parent: "services"
weight: 500
toc: true
---

System services are available on the robot to automatically launch at boot the most commonly used features of the robot. It is useful when you just want to use [our Python SDK]({{< ref "sdk/getting-started/introduction" >}}) without having to worry about running by hand [Reachy's core ROS code]({{< ref "advanced/software/presentation#ros" >}}). Nevertheless, you may want to use Reachy differently and deactivate them.

We use system.d to handle the services. If you are not familiar with this system, you should refer to the [official documentation](https://www.freedesktop.org/wiki/Software/systemd/).

> :bulb: **If your Reachy has been produced before or not been upgraded since July 2022**, the services are stored in `etc/systemd/system`, else there are in `~/.config/systemd/user`

## Services available

### reachy_sdk_server.service

For each Reachy's configuration except for the Arm kit (i.e. Full, Starter and Mobile kit), the service `reachy_sdk_server.service` is available and enabled by default.

You can see how the service is defined on [reachy_sdk_server repository](https://github.com/pollen-robotics/reachy_sdk_serverblob/master/generate-service-file.bash) but basically what this service does is executing a bash file which itself executes the ROS command:

```bash
ros2 launch reachy_sdk_server run_everything.launch.py
```

if the configuration of your Reachy has a head or 

```bash
ros2 launch reachy_sdk_server run_everything_no_head.launch.py
```

if not.

The launch file will start each useful Reachy's ROS node like a node to handle the joints, one for the kinematics, another for the cameras (if Reachy's configuration has a head), ...

For the complete list of the ros nodes launched by the service, check [run_everything.launch.py file](https://github.com/pollen-robotics/reachy_sdk_server/blob/master/launch/run_everything.launch.py) or [run_everything_no_head.launch.py](https://github.com/pollen-robotics/reachy_sdk_server/blob/master/launch/run_everything_no_head.launch.py).

### mobile_base_sdk_server.service

If your Reachy is equipped with a mobile base, the service `mobile_base_sdk_server.service` is also available and enabled by default. Having separate services for Reachy and the mobile base allows to work separately with the mobile base or Reachy when you have a Reachy Mobile.

As `reachy_sdk_server.service`, `mobile_base_sdk_server.service` defined on [mobile_base_sdk_server repository](https://github.com/pollen-robotics/mobile_base_sdk_server/blob/main/genereate_service_file.bash) executes a bash file which itself executes the ROS command:

```bash
ros2 launch mobile_base_sdk_server run_mobile_base_sdk_server_and_hal.launch.py
```

if a mobile base version is specified in Reachy's configuration file.

The launch file launched will start the ROS nodes for the HAL of the mobile base and the node to start the gRPC SDK server to use the [mobile base Python SDK](https://github.com/pollen-robotics/mobile-base-sdk).

For the complete list of the ros nodes launched by the service, check [run_mobile_base_sdk_server_and_hal.launch.py](https://github.com/pollen-robotics/mobile_base_sdk_server/blob/main/launch/run_mobile_base_sdk_server_and_hal.launch.py).

## What if I don't want to use services
If you don't want to use the default services, you can simply [disable them]({{< ref "advanced/services/manage-services#enable-or-disable-a-service" >}}) so that they won't start when booting the robot and launch [Reachy's ROS launch files]({{< ref "advanced/software/ros2-level" >}}) by hand.
