---
title: "Assemble mobile base + Reachy"
description: "Unpack safely and attach your robot correctly."
lead: "How to unpack your mobile base and attach Reachy"
date: 2022-07-16T13:59:39+01:00
lastmod: 2022-07-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "getting-started"
weight: 190
toc: true
---
## Assembly tools

You will need hex keys of size 3, 6 and 8. A mallet and a spring clip can be useful.


<!-- 
| You will need hex keys of size 3, 6 and 8            | A mallet and a spring clip can be useful              |
| ---------------------------------------------------- | ----------------------------------------------------- |
| {{< img alt="Hex keys" src="hex.jpg" width="30%" >}} | {{< img alt="Mallet" src="mallet.jpg" width="30%" >}} |
-->



## Unpacking your mobile base
The mobile base is shipped in a custom box with its battery inside. The rest of the elements can be found in Reachy's Box (including the poles and the battery charger).
> :warning: **WARNING!** :warning: To unpack the mobile base, remove the wood lid and use the internal handles as shown below. Using other methods to lift the mobile base could create injuries or damage the mobile base.

<p align="center">
    <video controls="controls" width="100%" muted>
    <source type="video/mp4" src="1-unboxing.mp4"></source>
    </video>
    <br>
</p>
 
:bulb: Notice how we made **contact with the battery twice?** This is intentional and it's important that you do the same. What often happens on the first contact is that the internal capacitors will draw a lot of current and the BMS of the battery will shutdown the battery for safety. This only happens on the first contact as the internal capacitors will get charged very quickly and won't draw current on the second contact. A spark might occur when you connect the battery, this is normal.

:bulb: If the BMS shutdowns the battery, the battery voltage will typically be around 6V to 8V instead of ~24V and the mobile base screen will not turn on. If this happens, just unplug and replug the '+' connector of the battery as shown in the above video.

> :warning: **WARNING!** :warning: The battery contains a lot of energy. Be careful and avoid all risks of creating a short-circuit.

Put the lid back on as shown on this video:
<p align="center">
    <video controls="controls" width="100% muted">
    <source type="video/mp4" src="2-lid_back_on.mp4"></source>
    </video>
    <br>
</p>

## Assemble the pole and slide the cables in
In reachy's box you should find two poles, two assembly pieces and the emergency button holder. Assemble them so that they are aligned together as follows:
{{< img alt="Hex keys" src="pole1.jpg" width="100%" >}}
{{< img alt="Hex keys" src="pole2.jpg" width="100%" >}}
Then push the cables through the pole. The bolt and the fisher's wire are there to help this step. This is easier done with two people:
<p align="center">
    <video controls="controls" width="100%" muted>
    <source type="video/mp4" src="3-cables_in_pole.mp4"></source>
    </video>
    <br>
</p>

## Attach the pole to the mobile base
Put the pole into the mobile base and lift up the wood lid as follows:
<p align="center">
    <video controls="controls" width="100%" muted>
    <source type="video/mp4" src="4-temp_pole.mp4"></source>
    </video>
    <br>
</p>
Sometimes the mounting part is very tight, even when the screw is loose. You can use a mallet if needed:
<p align="center">
    <video controls="controls" width="100%" muted>
    <source type="video/mp4" src="5-final_pole.mp4"></source>
    </video>
    <br>
</p>
Then, tighten the screws:
<p align="center">
    <video controls="controls" width="100%" muted>
    <source type="video/mp4" src="6-screw.mp4"></source>
    </video>
    <br>
</p>

## Attach Reachy
This step requires two people. Cut the fisher's wire but make sure that the cables don't fall back into the pole. Use the four bolts to attach Reachy to its mounting part. The connect the cables and the emergency button as follows:
<p align="center">
    <video controls="controls" width="100%" muted>
    <source type="video/mp4" src="7-attach_reachy.mp4"></source>
    </video>
    <br>
</p>

:bulb: Make sure the mounting part is fully inside Reachy's socket. It's a mistake so common, we did it ourselves on the above video :) It should look like this:
{{< img alt="Mounting part" src="good_practice.jpg" width="100%" >}}

## Turn on your robot
To power up the robot, release the emergency button and press the mobile base button. The mobile base's screen should turn on, indicating the current state of the battery (% remaining, current flow, etc). Then, to power up the arms and head, turn on the switch near its right shoulder.
Finally, to turn on the computer, press the button near its left shoulder. 
<p align="center">
    <video controls="controls" width="100%" muted>
    <source type="video/mp4" src="8-turn_on.mp4"></source>
    </video>
    <br>
</p>

## Understanding the power buttons and battery life good practices
The mobile base uses the 24V battery to power the wheels directly. DC-DC converters are used to generate 5V (emergency button power, USB HUB power and relay logic) and 12V for the upper body.
The 5V converter draws almost 100mA when idle and is necessary for the emergency button logic.

The emergency button and the mobile base button both need to be ON to turn on the power relay that shares the 24V with the rest of the robot. However, the mobile base button is the only one that, when turned OFF, shuts down the 5V converter.


> :warning: **WARNING!** :warning: When turning off the robot, always turn off the mobile base button to minimize the idle current consumption. If you turn off the robot with the emergency button and didn't press the mobile base button before storing your robot, the battery will deplate faster.

:bulb: Even with the mobile base button OFF, the battery screen will be powered (low consumption at around ~1mA). If you plan to store the robot for more than a month, we recommend unplugging one of the wires of the battery (like when you received the robot).


|                Configuration                | Storage time before depleting a full battery |
| :-----------------------------------------: | :------------------------------------------: |
| Mobile base button ON, emergency button OFF |                  A few days                  |
|           Mobile base button OFF            |                 A few months                 |
|           Unplugging the battery            |                 A few years                  |

