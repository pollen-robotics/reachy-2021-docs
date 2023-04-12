---
title: "Hello World App"
description: "The Hello World application defines an idle mode for Reachy which can run autonomously."
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  sdk:
    parent: "application"
weight: 400
toc: true
---

## What is this application

The hello world application defines an idle mode for Reachy which can run autonomously.

This project has been thought to:

- be able to make Reachy move immediately after the robot setup, without having to do any code
- start to elaborate a way to define behaviors for human-robot
interaction, making independant components that can be reused and
integrated in more complex programs. The idea is to be able to integrate this idle mode in any project requiring such a state, without having to re-code this behavior again and again.

The source can be found in the <a href="https://github.com/pollen-robotics/hello-world" target="_blank">hello-world</a> GitHub repository.

## How to install and run the application

### Install

Clone the repository and install with pip.

```bash
cd ~/dev
git clone https://github.com/pollen-robotics/hello-world.git
cd hello-world
pip3 install -e .
```

### Run the application
You can run the application directly with Python.
```bash
cd ~/dev/hello-world
python3 -m hello_world.hello
```

Or call ***launch.bash***

```bash
cd ~/dev/hello-world
bash launch.bash
```

What this bash file does is just making sure that [reachy_sdk_server.service]({{< ref "advanced/services/available#reachy_sdk_serverservice" >}}) (Reachy’s core code) is started and calling the application with the Python command given above.

### Define service
You can also setup a service to start the application automatically at boot or to control the application directly with the [dashboard]({{< ref "dashboard/introduction/introduction" >}}).

To do that, just use the provided bash file.
```bash
cd ~/dev/hello-world
bash setup-service.bash
```
However be careful if you start the application automatically at boot, you need to make sure that the robot is in place and that nothing could enter in collision with it while it is moving.

**We recommend to play a few times with the application using the Python calling before using the service, to be familiar with the hello world.**

## Good practice
It is important to give Reachy enough space to move, for the robot and for the people around.

- First, the robot needs to be able to have its arms straight along its body. This means for example that there cannot be a table in front of Reachy, or objects that you could block the trajectory of its movements.
- We recommend using the behavior player to play each behavior independently first, to get a sense of what each movement is doing. This will show you what space the robot needs to run the application safely. See the behaviors section to learn how to use the behavior player.

### Safety first

- You need to understand that no intelligence has been put in the playing of the behaviors, meaning that the movements are hard-coded. So if during its movements, someone or something comes in the way of Reachy, the robot will not stop its movement.
- Make sure that no one will be in the movement area of Reachy when the application is running.
- Always have someone around the robot when the application is running, don’t let the robot alone.

## Behaviors
The application is a composition of implemented behaviors. Here we will present each behavior independently.

### Existing behaviors

Currently nine behaviors are implemented:

- ***asleep***: Reachy moves just a bit its arm along its body as if it was breathing, with the head looking down.
- ***look_hand***: Reachy moves its gripper and look at it.
- ***lonely***: Reachy looks around and act sad at the end.
- ***scratch***: Reachy scratches its forearm.
- ***tshirt***: Reachy grabs its T-shirt, and put it back in place.
- ***sweat_head***: Reachy touches wipe its head as if it was too hot.
- ***sneeze***: Reachy sneezes with a head movement.
- ***whistle***: Reachy whistles a tune cheerfully.
- ***hello***: Reachy waves its hand to say hello.

To play any of these behaviors without having to use the app, you can use the <a href="https://github.com/pollen-robotics/hello-world/tree/main/hello_world/behavior_player.py" target="_blank">behavior_player script</a>.

For example, to play ***sneeze***:

```bash
cd ~/dev/hello-world
python3 -m hello_world.behavior_player sneeze
```

### Idle

The <a href="https://github.com/pollen-robotics/hello-world/tree/main/hello_world/behaviors/idle.py" target="_blank">idle behavior</a> is the behavior played by the application in the <a href="https://github.com/pollen-robotics/hello-world/tree/main/hello_world/hello.py" target="_blank">hello</a> script (you can consider hello to be the main file for the application). Idle is composed of sub-behaviors, each of them being the behaviors presented above.

Here is the implementation of Idle, taken from <a href="https://github.com/pollen-robotics/hello-world/tree/main/hello_world/behaviors/idle.py" target="_blank">idle.py</a>:

```python
class Idle(Behavior):
    """Idle class."""

    def __init__(self, name: str, reachy, sub_behavior: bool = False) -> None:
        """Initialize the behavior."""
        super().__init__(name, reachy=reachy, sub_behavior=sub_behavior)

        logging.basicConfig(level=logging.INFO)
        self._logger = logging.getLogger()

        self.reachy = reachy
        self.asleep_behavior = Asleep(name='asleep', reachy=self.reachy, sub_behavior=True)
        self.behaviors = {
            'look_hand': LookHand(name='look_hand', reachy=self.reachy, sub_behavior=True),
            'lonely': Lonely(name='lonely', reachy=self.reachy, sub_behavior=True),
            'scratch': Scratch(name='scratch', reachy=self.reachy, sub_behavior=True),
            'tshirt': Tshirt(name='tshirt', reachy=self.reachy, sub_behavior=True),
            'sweat_head': SweatHead(name='sweat_head', reachy=self.reachy, sub_behavior=True),
            'sneeze': Sneeze(name='sneeze', reachy=self.reachy, sub_behavior=True),
            'whistle': Whistle(name='whistle', reachy=self.reachy, sub_behavior=True),
            'hello': Hello(name='hello', reachy=self.reachy, sub_behavior=True)
        }
		async def run(self):
        """Implement the behavior."""
        while True:
            asleep = await self.asleep_behavior.start()
            self._logger.info('Playing asleep behavior.')
            await asleep
            self.reachy.turn_on('reachy')

            random_sub_behavior = np.random.choice(list(self.behaviors.keys()))
            self._logger.info(f'Playing sub behavior {random_sub_behavior}')
	            await self.behaviors[random_sub_behavior]._run()
```

You can see in the *init* that the nine behaviors presented before are imported and defined as sub behaviors. 

What the idle behavior is actually doing is defined in the **run** method: when doing idle, Reachy will alternate between the asleep behavior and one of the other eight behavior, picked randomly.

If you want to remove a behavior from idle, just comment it in the definition of **self.behaviors**.

### Implement your own behavior

It is also possible for you to implement your own behavior and to add it to the idle behavior.

What you need to know is that your class defining your new behavior should inherit from the <a href="https://github.com/pollen-robotics/hello-world/tree/main/hello_world/behaviors/__init__.py" target="_blank">Behavior class</a>, define an \_\_init\_\_, a run and a terdown method. More info on the README of the <a href="https://github.com/pollen-robotics/hello-world#add-new-behaviors" target="_blank">hello-world repository</a>.

Each existing behavior have been implemented only using [Reachy’s Python SDK]({{< ref "sdk/getting-started/introduction" >}}), whether it was by using [goto]({{< ref "sdk/first-moves/arm#goto-function" >}}) or [look_at]({{< ref "sdk/first-moves/head#orbita-look_at-method" >}}), or by [recording and replaying movements]({{< ref "sdk/first-moves/record" >}}). Take a look at how the behaviors have been implemented to get some inspiration.

## Other
### Run the application on any computer
Since all the application has been developed using *[reachy-sdk]({{< ref "sdk/getting-started/introduction" >}})*, it is not mandatory to run the application directly on Reachy’s computer. As long as reachy-sdk is installed on your machine, you can run the application locally on your computer by changing <a href="https://github.com/pollen-robotics/hello-world/blob/dc13915fddf366077797f42cad8d97119697706c/hello_world/hello.py#L18" target="_blank">Reachy_IP variable</a> in the hello file.

### Sound

As you will notice, when playing the behaviors, some of them also play sounds simultaneously! This is the case of asleep, sneeze and whistle. Feel free to add sounds to your behaviors or the existing ones using the <a href="https://github.com/pollen-robotics/hello-world/tree/main/hello_world/behaviors/player.py" target="_blank">playsound tool</a> in the project.