---
title: "Using the mobile base without Reachy"
description: "How to use the mobile base without a Reachy"
date: 2021-03-30T09:54:59+02:00
lastmod: 2021-03-30T09:54:59+02:00
draft: false
images: []
menu:
  SDK:
    parent: "mobile-base"
weight: 340
toc: true
---

There is no need to instanciate the entire Reachy stack to interact with the mobile base. 
Instanciating the *mobile-base-sdk* alone is very fast and easy:
```python
from mobile_base_sdk import MobileBaseSDK

mobile_base = MobileBaseSDK('your-reachy-ip')
```
This will work even if the upper body is not powered (the computer has to be powered though).

Once the object 'mobile_base' is implemented the syntax is the same to what has been covered in the rest of the documentation, just remove the "reachy." keyword. For example, to read the odometry just type:

```python
mobile_base.odometry
```

You can use this [Jupyter Notebook](https://github.com/pollen-robotics/mobile-base-sdk/blob/main/mobile_base_sdk/examples/notebooks/getting-started.ipynb) example to test this.