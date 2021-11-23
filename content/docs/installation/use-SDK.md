---
title: "Use Reachy SDK"
description: "Control the robot from any computer using the SDK."
lead: "Control the robot from any computer using the SDK."
date: 2021-03-16T10:46:05+01:00
lastmod: 2021-03-16T10:46:05+01:00
draft: false
images: []
menu:
  docs:
    parent: "installation"
weight: 110
toc: true
---

If you want to control Reachy using its **Python SDK**, you only need to install it on the computer you want to use. The SDK is a pure Python library so it can be easily installed on any computer running **Python >= 3.6**.

```python
from reachy_sdk import ReachySDK

reachy = ReachySDK(host='reachy.IP.address')
```

**Ready to start using the Python SDK? Check out the [Python SDK documentation](https://pollen-robotics.github.io/reachy-2021-docs/sdk/getting-started/introduction/)!**  

{{< my-button-new-page link="https://pollen-robotics.github.io/reachy-2021-docs/sdk/getting-started/introduction/" label="Getting started with Reachy Python SDK" >}}
