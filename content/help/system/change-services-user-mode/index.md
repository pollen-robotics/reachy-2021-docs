---
title: "Change Reachy's services from sudo to user mode"
description: ""
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
toc: true
hidden: true
---

As of July 2021, [Reachy's services]({{< ref "/advanced/services/available" >}}) have been changed from sudo mode to user mode. If your Reachy has been produced after July 2021, this change should be already effective in your robot. If your robot is older and you want change that, for example to use the [dashboard]({{< ref "/dashboard/introduction/introduction" >}}), here is what you need to do for the service [reachy_sdk_server.service]({{< ref "/advanced/services/available#reachy_sdk_serverservice" >}}).

1. **Remove the service from the sudo services** 
```bash
sudo systemctl disable reachy_sdk_server.service
sudo rm /etc/systemd/system/reachy_sdk_server.service
```

2. **Generate the service file in user mode and install it**
Pull the latest version of [reachy_sdk_server](https://github.com/pollen-robotics/reachy_sdk_server) and generate the new service file.

```bash
cd ~/reachy_ws/src/reachy_sdk_server
git pull
bash generate-service-file.bash
```
A new file reachy_sdk_server.service should have been created in *~/reachy_ws/src/reachy_sdk_server*. 

Move this file in the correct service folder
```bash
mv ~/reachy_ws/src/reachy_sdk_server/reachy_sdk_server.service ~/.config/systemd/user
```

Finally enable the service
```bash
systemctl --user enable reachy_sdk_server.service
```

More info on what you can do with the service is available in [Reachy's service documentation page]({{< ref "/advanced/services/manage-services" >}}).