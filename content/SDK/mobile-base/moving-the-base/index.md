---
title: "Moving the mobile base"
description: "Presentation of the different functions available to make the mobile base move"
date: 2021-03-30T09:54:59+02:00
lastmod: 2021-03-30T09:54:59+02:00
draft: false
images: []
menu:
  SDK:
    parent: "mobile-base"
weight: 310
toc: true
---


WIP
goto
set_speed
odometric frame
(add drawing)

goto example : https://github.com/pollen-robotics/mobile-base-sdk/blob/main/mobile_base_sdk/examples/notebooks/goto.ipynb

set_speed example : https://github.com/pollen-robotics/mobile-base-sdk/blob/main/mobile_base_sdk/examples/scripts/joy_controller.py



advanced: the difference between cmd_vel (the HAL listens to a topic and applies the commands, with some smoothing) vs speed (the HAL controls the time during which the speed command is applyied)