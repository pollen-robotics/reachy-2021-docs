---
title : "FAQ"
description: "FAQ"
lead: ""
date: 2020-10-06T08:48:23+00:00
lastmod: 2020-10-06T08:48:23+00:00
draft: false
images: []
menu:
  help:
    parent: help
weight: 1
toc: true
---

{{% expand "> How to find the IP of my robot?" %}}
Check the [Find my IP section]({{< ref "sdk/getting-started/finding-ip" >}}).
{{% /expand %}}

{{% expand "> The SDK server is not starting." %}}
Check the [Debug section]({{< ref "docs/debug/debug-method" >}}).
{{% /expand %}}

{{% expand "> One of Reachy's motor red led is blinking" %}}
This means the motor has overheat and needs to cooldown. Turn the robot off, wait for it to cooldown and turn it on again.
{{% /expand %}}

{{% expand "> One of Reachy's module blue led is blinking" %}}
This means the module encounter an issue (safety shutdown, incorrect instruction, etc.). You need to turn the robot off and on again to restart the module. If the issue persists check the logs to get more information on the source of the issue.
{{% /expand %}}

{{% expand "> Reachy's head doesn't look straight when asked." %}}
You need to start the robot with the head in a position close to straight when starting the robot. Indeed, orbita's position encoder only covers part of the whole motion range. We use this starting position to recalibrate the absolute position.
{{% /expand %}}