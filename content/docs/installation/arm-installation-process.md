---
title: "Arm kit installation process"
description: "Arm kit installation process."
lead: "How to install your Arm kit."
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "installation"
weight: 510
toc: true
---

You decided to buy an **Arm kit**, you have a few things to install on your computer.
Don’t worry, we will go step by step to guide you through the installation process!

## What do I need?
To program and control your robot, you have two main options:  
* Directly control it via **ROS2 Foxy**: this gives you lower level access to the robot and full interoperability with ROS. Yet ROS can be complex, so if you are not familiar with it, that’s probably not what you are looking for.
* Use our specific **Python SDK**: simple Python’s API to let you quickly start controlling your robot. It gives you access to all main robot features. If you are not familiar with ROS, we advise you to use our SDK first.  

In the following, we will show you how to install everything needed to start programming your robot. If you want to only use ROS2, we will tell you which steps can be skipped.  

The low-level software used to control the robot has been developed to work on **Linux Ubuntu 20.04**. While it should work on other OS, we strongly recommend using the same version.  


Reachy runs on **ROS 2 Foxy**. So first of all, you need to install it.  
For more information on ROS2 and how to install it, please refer to the official documentation: [https://index.ros.org/doc/ros2/Installation/Foxy/Linux-Install-Debians/](https://index.ros.org/doc/ros2/Installation/Foxy/Linux-Install-Debians/)

## Create a ROS workspace for Reachy
*Note:* If you are familiar with ROS2, please feel free to use your custom installation.  

Now that you have installed ROS, you need a ROS workspace to install the specific ROS packages for Reachy.
Create it in your $HOME folder:
```bash
mkdir -p ~/reachy_ws/src
```

Then, open .bashrc:
```bash
nano ~/.bashrc
```

And add the following lines:
```bash
source /opt/ros/foxy/setup.bash
source $HOME/reachy_ws/install/setup.bash
``` 
Finally, source your bashrc file:
```bash
source ~/.bashrc
```


To learn more on the creation of workspaces for ROS 2 Foxy:
[https://docs.ros.org/en/foxy/Tutorials/Workspace/Creating-A-Workspace.html](https://docs.ros.org/en/foxy/Tutorials/Workspace/Creating-A-Workspace.html)


## Clone the requested ROS repositories from GitHub

In `~/reachy_ws/src`, clone the following repositories (see [https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository) if you are not familiar with git):

To use Reachy directly with ROS:  
* reachy_msgs: [https://github.com/pollen-robotics/reachy_msgs](https://github.com/pollen-robotics/reachy_msgs)  
* reachy_controllers: [https://github.com/pollen-robotics/reachy_controllers](https://github.com/pollen-robotics/reachy_controllers)  
* reachy_kinematics: [https://github.com/pollen-robotics/reachy_kinematics](https://github.com/pollen-robotics/reachy_kinematics)  

To use Reachy through the SDK:  
* reachy_sdk_server: [https://github.com/pollen-robotics/reachy_sdk_server](https://github.com/pollen-robotics/reachy_sdk_server)

When everything is cloned in your directory, build the packages:
```bash
cd ~/reachy_ws
colcon build
```

## Open ports for serial use
By default, on a Ubuntu install, when using serial, users do not have the right to access the ports. Give rights to open `/dev/ttyUSB` ports:
```bash
sudo usermod -a -G tty <usr_name>
sudo usermod -a -G dialout <usr_name>
```

## Clone the other requested repositories from Github
Create another folder dev that will contain all the packages used with Reachy that are not based on ROS. In this folder, clone the following repositories:  

Requested in all cases:  
* reachy_pyluos_hal: [https://github.com/pollen-robotics/reachy_pyluos_hal](https://github.com/pollen-robotics/reachy_pyluos_hal)  

To use Reachy through the SDK:  
* reachy_sdk_api: [https://github.com/pollen-robotics/reachy-sdk-api](https://github.com/pollen-robotics/reachy-sdk-api)  
  Then install the sdk-api:
  ```bash
  cd ~/dev/reachy-sdk-api
  pip3 install -e python
  ```

* reachy-sdk: [https://github.com/pollen-robotics/reachy-sdk](https://github.com/pollen-robotics/reachy-sdk)  

***To learn more on the repositories content and usage, please refer to README.md files in each repository.***

## Install the dependencies
Some Python dependencies need to be installed as extra.  
**Dependencies:** numpy, scipy, pyquaternion, zoom_kurokesu, pykdl  

If one of them is missing:  
* Using pip install:
```bash
pip3 install numpy
pip3 install scipy
pip3 install pyquaternion
pip3 install zoom_kurokesu
```
* Using apt install:
```bash
sudo apt install python3-pykdl
```

## Set the correct configuration file
As Reachy software is meant to work with different robot configurations. Several configuration files are available.  

By default, the configuration is set to a **full robot**. You need to modify it to your own configuration.  

Open .bashrc: 
```bash
nano ~/.bashrc
```

And add an environment variable REACHY_MODEL that designates your model.  
For example, to configure only a right arm:
```bash
export REACHY_MODEL=”reachy_right_arm”
```

Make sure to source your bashrc file to take the modification into account:
```bash
source ~/.bashrc
```

To use other methods to change your configuration, please read `~/dev/reachy_pyluos_hal/reachy_pyluos_hal/tools/reachy_identify_model.py` or go to [https://github.com/pollen-robotics/reachy_pyluos_hal/blob/main/reachy_pyluos_hal/tools/reachy_identify_model.py](https://github.com/pollen-robotics/reachy_pyluos_hal/blob/main/reachy_pyluos_hal/tools/reachy_identify_model.py).

## Start everything up
If you are using ROS, you will find launch files in each of our ROS packages to set them up.
In particular, you can run:  
```bash
ros2 launch reachy_kinematics kinematics.launch.py  
# (for description and kinematics)
```

```bash
ros2 launch reachy_controllers joint_state_controller.launch.py  
# (for joint_state, joint_goals, fans, sensors, etc.) 
```
 

If you want to use the SDK, we provide a specific launcher file that starts everything (including the above mentioned ROS packages) at once:  
```bash
ros2 launch reachy_sdk_server reachy_sdk_server.launch.py
```

## Generate a system.d file for auto-startup
If you want the reachy_sdk_server launch file to be started automatically when your computer starts, you can use our systemd file:
```bash
cd ~/reachy_ws/src/reachy_sdk_server
bash generate-service-file.bash
```

This command should have created a file called *reachy_sdk_server.service*. To activate this service, you need to copy it to `systemd`:
```bash
sudo scp reachy_sdk_server.service /etc/systemd/system
```

Enable it for the service to be launched automatically when you restart your computer:
```bash
sudo systemctl enable reachy_sdk_server.service
```
You can manually start it doing:
```bash
sudo systemctl start reachy_sdk_server.service
```
*Note:* You need to connect the arm to your computer before starting a service. If you enabled the service, connect your arm to your computer before turning it on.  

*For more information on the services, please refer to section [Using services]({{< ref "services" >}}).*
