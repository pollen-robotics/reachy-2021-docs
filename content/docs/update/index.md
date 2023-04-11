---
title : "Update packages"
description: "Update Reachy"
lead: "Get latest version of Reachy software"
date: 2020-10-06T08:48:45+00:00
lastmod: 2020-10-06T08:48:45+00:00
draft: false
images: []
menu:
  docs:
    parent: "update"
weight: 300
toc: true
---

## Fetch repositories on Github Desktop

All the Github repositories of Reachy's packages are cloned on Github Desktop. 
Simply find it on Reachy's computer, select one by one the repositories and fetch to check if there are updates. Pull the changes in case updates are found.  

The list of all Reachy's packages which may require updates is available here:  

{{< my-button-new-page link="/advanced/software/presentation#packages" label="Find Reachy packages list" >}}

{{< alert icon="👉" text="In case of <b>major Reachy updates</b>, it may happen some packages of the list are not cloned on your robot. Clone them from Github Desktop in the correct folder (<i>reachy_ws/src</i> or <i>dev</i> depending of the nature of the package).">}}

## Rebuild ROS packages

To make sure the updates have been taken into account, build ROS packages after having pulled them.
```
cd ~/reachy_ws
colcon build --symlink-install
source ~/.bashrc
```