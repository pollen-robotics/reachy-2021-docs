---
title: "Best practice"
description: "Towards a good usage of the VR teleoperation app"
date: 2021-03-30T13:05:22+02:00
lastmod: 2021-03-30T13:05:22+02:00
draft: false
images: []
menu:
  VR:
    parent: "use-teleop"
weight: 600
toc: true
---

Reachy doesn't have the exact same degrees of freedom as you have, neither the same range for each joints. When a position cannot be reached, either because of the position or the orientation, the inverse kinematics gives the closest arm configuration found. The closest configuration found for the next position may be:

- the same as the previous one, so the arm won't move and you have the impression Reachy is not following your movements anymore
- quite different from the previous one, which will lead to sudden changes of the arm position

All this contribute to give movements that seem incontrollable, due to discontinuities in the arm's inverse kinematics.

**To avoid this situation:**

- Avoid using extreme joints orientations while teleoperating Reachy
- The most limiting joint is the elbow: avoid working to close to your chest, the elbow will be at the limit of its range of motion
- If the robot seems to stop following your movements, do not continue to move in this direction, you have already reached its workspace limit. Go back to a position you know can be reached.