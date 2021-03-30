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

The last required step before actually programing your Reachy is to find its IP address. 

## Working directly on Reachy

You can run the SDK directly on Reachy's computer. In this case, the IP is the *localhost* address: '127.0.0.1'. You can thus directly use:

```python
from reachy_sdk import ReachySDK

reachy = ReachySDK(host='127.0.0.1')
```

Using the SDK locally also avoids network potential latency or bandwidth issue. Yet, it may not be as conveninent as working directly from your usual laptop. You need to plug a screen, keyboard and mouse directly on Reachy's computer.

## Via the network

First, you need to make sure that both Reachy and the computer you want to use for the SDK, are on the same network. We recommend using an ethernet connection to make sure the latency is as small as possible. It also works on WiFi but for precise and high-frequency control, you should privilege wired option.

We assume you've already configured the network on Reachy as described in the [Setup Reachy]({{< relref "/docs/overview/full-kit" >}}) section. What you need now is to find Reachy's IP on your network.

### ifconfig

If you have access to Reachy directly (by connecting a screen and keyboard), you can run the ifconfig command. The image below show you where to find the IP from the result of the command:

{{< img src="ifconfig.png" alt="Square" class="border-0" >}}

In our case, connecting to the robot can then be done via:

```python
from reachy_sdk import ReachySDK

reachy = ReachySDK(host='192.168.86.56')
```

### Multicast DNS

If your network and OS support [mDNS](https://en.wikipedia.org/wiki/Multicast_DNS), you should also be able to connect to Reachy via:

```python
from reachy_sdk import ReachySDK

# On Windows replace *.local by *.lan
reachy = ReachySDK(host='reachy.local') 
```

### Using a smartphone

The [Fing app](https://www.fing.com/products/fing-app) let you scan IPs directly from your smartphone. It also needs to be connected on the same network.