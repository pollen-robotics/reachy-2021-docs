---
title: "Arm kit software installation"
description: "Arm kit software installation"
lead: "How to install Reachy's Arm kit software."
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
toc: true
hidden: true
---

You decided to buy an **Arm kit**, you have a few things to install on your computer.
Don’t worry, we will go step by step to guide you through the installation process!

## Prerequisites
The low-level software used to control the robot has been developed to work on **Linux Ubuntu 22.04**. While it should work on other OS, we strongly recommend using the same version.  

## Presentation
Reachy's software installation is divided into two main parts:
- installing ROS2 Humble and the ROS2 packages developped for Reachy
- installing the Python packages developped for Reachy

If you are not familiar with [ROS](https://www.ros.org), it stands for Robotics Operating System and is basically a set of software libraries and tools that help build robot applications. It is commonly used in Robotics. You don't need to know how to use ROS to work with Reachy thanks to the [Python SDK](https://github.com/pollen-robotics/reachy-sdk) that we developped but if you want to learn about ROS, we suggest taking a look at their great [tutorials](https://docs.ros.org/en/humble/Tutorials.html).

Also, you can check [this page]({{< ref "advanced/software/presentation" >}}) to know more about how Reachy's software is organised.

Now back to the installation!

## Install ROS2 Humble
As explained above, Reachy's software runs on **ROS 2 Humble** so first of all, you need to install it on your computer. 
Based on the [official ROS2 documentation](https://index.ros.org/doc/ros2/Installation/Humble/Linux-Install-Debians/), here are the steps to do the installation.
In a terminal, in your computer:
```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

sudo apt update
sudo apt upgrade

sudo apt install ros-foxy-humble
sudo apt install ros-dev-tools
```
### Check that the installation went well
To make sure that ROS2 Humble has been successfully installed, you can run the test example from ROS2 Humble. 
Taken from the [ROS2 Humble documentation](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html#try-some-examples).

## Install Reachy's ROS2 packages
### Create a dedicated workspace
Now that you have installed ROS, you need to [create a ROS workspace](https://docs.ros.org/en/humble/Tutorials/Workspace/Creating-A-Workspace.html) to install the specific ROS packages for Reachy.

Create it in your $HOME folder:
```bash
mkdir -p ~/reachy_ws/src
```

Build your empty workspace once to set everything up.
```bash
cd ~/reachy_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install
```

Once done, add commands to your *.bashrc* file so that you won't have to type them in each new terminal. 

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
echo "source /home/reachy/reachy_ws/install/setup.bash" >> ~/.bashrc
echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
echo "export _colcon_cd_root=~/ros2_install" >> ~/.bashrc
```
In the seconde line, replace the *reachy* in */home/reachy/reachy_ws/install/setup.bash* with your username.

Finally, source your *.bashrc* file:
```bash
source ~/.bashrc
```

### Clone Reachy's ROS2 packages
Now you're ready to install Reachy's ROS2 packages in the workspace you just created.
* [reachy_2023](https://github.com/pollen-robotics/reachy_2023)

```bash
cd ~/reachy_ws/src
git clone https://github.com/pollen-robotics/reachy_2023.git
```

Once everything cloned in your ROS2 workspace, install the dependencies and build the packages:
```bash
cd ~/reachy_ws
bash ./src/reachy_2023/dependencies.sh
pip3 install -r ./src/reachy_2023/requirements.txt
colcon build --symlink-install
```

## Install Reachy's Python packages

### Other ependencies
Some of Reachy's Python packages have dependencies that you should install. The dependencies are *numpy, scipy, pyquaternion, sklearn, pykdl*.
* Using pip install:
```bash
pip3 install numpy
pip3 install scipy
pip3 install pyquaternion
pip3 install sklearn
```

We also recommend to install the *jupyter* and *matplotlib* libraries.
```bash
pip3 install jupyter
pip3 install matplotlib
```

### Cloning the Python packages
Create another folder *dev* that will contain all the packages used with Reachy that are not based on ROS.

```bash
mkdir ~/dev
```

In this folder you will need the following repositories:  

* [reachy_sdk_api](https://github.com/pollen-robotics/reachy-sdk-api)  
* [reachy-sdk](https://github.com/pollen-robotics/reachy-sdk)  

```bash
cd ~/dev
git clone https://github.com/pollen-robotics/reachy-sdk-api.git
git clone https://github.com/pollen-robotics/reachy-sdk.git
```

Install the packages after the cloning.
```bash
cd ~/dev/reachy-sdk-api
pip3 install -e python

cd ~/dev/reachy-sdk
pip3 install -e .
```

***To learn more on the repositories content and usage, please refer to README.md files in each repository.***

## Other
### Open ports for serial use
By default, on a Ubuntu install, when using serial, users do not have the right to access the ports. Give rights to open `/dev/ttyUSB` ports:
```bash
sudo usermod -a -G tty <usr_name>
sudo usermod -a -G dialout <usr_name>
```
### Set the correct configuration file
As Reachy software is meant to work with different robot configurations. Several configuration files are available.  

By default, the configuration is set to a **full robot**. You need to modify it to your own configuration.  

Open .bashrc: 
```bash
nano ~/.bashrc
```

And add an config file with your model as *~/.reachy.yaml*.  
For example, to configure only a right arm:
```bash
generation: 2023
model: robotic_right_arm_kit
zuuu_version: None
neck_orbita_zero:
    top: 0.0
    middle: 0.0
    bottom: 0.0
camera_parameters:
    left:
        fx: 0.0
        fy: 0.0
        cx: 0.0
        cy: 0.0
        k1: 0.0
        k2: 0.0
        k3: 0.0
        p1: 0.0
        p2: 0.0
    right:
        fx: 0.0
        fy: 0.0
        cx: 0.0
        cy: 0.0
        k1: 0.0
        k2: 0.0
        k3: 0.0
        p1: 0.0
        p2: 0.0
```

Make sure to source your *.bashrc* file to take the modification into account:
```bash
source ~/.bashrc
```

## If you want to work directly at the ROS level

If you prefer using the ROS2 packages instead of the Python SDK, you can find bring up launch file to set your robot up.
In particular, you can run:  
```bash
ros2 launch reachy_bringup reachy.launch.py  
```


If you want to use the SDK, we provide a specific argument that starts everything (including the above mentioned ROS packages) at once:  
```bash
ros2 launch reachy_bringup reachy.launch.py start_sdk_server:=true
```

For more information, check the page [Working with ROS2 Humble]({{< ref "advanced/software/ros2-level" >}})

## Final checking

Everything should now be installed and running on your computer to start working with Reachy! Let's check this out.


{{< alert icon="💡" text="Before launching it, the arm should be powered and the <a href=\"/advanced/overview/arm-kit#reachys-arm\">USB to serial board</a> connected to your computer." >}}

The output in the terminal should look like this:
<p align="center">
<img src="ros_launch_all.png" alt="drawing" width="80%"/>
</p>

Especially, you should see the line: ***SDK ready to be served!***.

Finally you can check that you can connect to the arm using Reachy's Python SDK.

In a python terminal:
```python
>>> from reachy_sdk import ReachySDK

>>> reachy = ReachySDK(host='localhost')

>>>reachy
```
For a robotic right arm, the outputs should look like this:
<p align="center">
<img src="robotic_arm_connect_sdk.png" alt="drawing" width="80%"/>
</p>

If both of these are ok the arm's software installation should have went well!
