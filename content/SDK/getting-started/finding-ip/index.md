---
title: "Finding Reachy's IP"
description: ""
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
menu:
  SDK:
    parent: "getting-started"
weight: 120
toc: true
---

The last required step before actually programing your Reachy is to find its IP address. A dedicated [Find my IP section]({{< ref "help/system/find-my-ip" >}}) will give you more details on how to do that.

> Note: Using the SDK locally also avoids network potential latency or bandwidth issue. Yet, it may not be as convenient as working directly from your usual laptop. You need to plug a screen, keyboard and mouse directly on Reachy's computer.

You can check that everything is working as expected by running the following Python code:

```python
from reachy_sdk import ReachySDK

# Replace with the actual IP you've found.
reachy = ReachySDK(host='the.reachy.ip.found.')
```