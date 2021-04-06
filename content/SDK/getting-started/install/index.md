---
title: "Installation"
description: "How to install the Python SDK, either from PyPi or directly from sources."
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  SDK:
    parent: "getting-started"
weight: 110
toc: true
---

## How to install the Python SDK

The Python SDK is a pure Python library. The installation should thus be rather straightforward. It supports Python >= 3.6 (older versions may work but are not officially supported). It works on Windows/Mac/Linux.

We recommend to use [virtual environment](https://docs.python.org/3/tutorial/venv.html) for your development. They make the installation simple and avoid compatibility issues. They also come with their [pip](https://pip.pypa.io/en/stable/) command.

### From PyPi

```bash
pip3 install reachy-sdk
```

### From the source

```bash
git clone https://github.com/pollen-robotics/reachy-sdk
pip3 install -e reachy-sdk
```

## Dependencies

The SDK relies on a few third-party Python packages:

* [numpy](https://numpy.org) - mostly for trajectory computation
* [opencv](https://opencv.org) - for camera frame access
* [grpc](https://grpc.io) - to connect to the robot

They will be installed automatically when you install the SDK.
