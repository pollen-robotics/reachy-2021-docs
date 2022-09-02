---
title : "🆕 Check the dashboard"
description: ""
lead: "Find debug info on the dashboard"
date: 2020-10-06T08:48:23+00:00
lastmod: 2020-10-06T08:48:23+00:00
draft: false
images: []
menu:
  help:
    parent: help
weight: 50
toc: true
---

The [dashboard's debug page]({{< ref "/dashboard/content/debug" >}}) will indicate you basic debug info like if one of Reachy's motor or force sensor is disconnected or if you forgot to turn on Reachy's motors before booting its computer.

You can also check the status of [reachy_sdk_server.service]({{< ref "/advanced/services/available#reachy_sdk_serverservice" >}}) in the [dashboard's services page]({{< ref "/dashboard/content/services" >}}) to get error messages.

## Access the dashboard

**From the robot:**  
Access the dashboard at `127.0.0.1:3972`

**From any other device on the same network as the robot:**  
Access the dashboard at `<robot-ip>:3972`
