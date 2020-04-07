---
title: 'OpenDog: Adding Force Sensitive Feet'
date: 2020-01-04T13:06:00+01:00
draft: false
---

\[James Bruton\] OpenDog remains one of the most impressive home-built robotics projects we’ve seen here on Hackaday, and it’s a gift that just keeps on giving. This time he’s working on adding [force sensing capabilities](https://www.youtube.com/watch?v=-asp12aovNs) to OpenDog’s legs to allow for more dynamic movement control.

The actuators in the legs are three-phase outrunner motors that drive ball-screws via a belt. This configuration is non-backdrivable, meaning the legs cannot be moved when an external force is, which could lead to mechanical failures. He as tested other backdrivable leg configurations with [other robots](https://hackaday.com/2019/11/08/making-a-robotic-dog-better-by-adding-springiness-without-springs/), but did not want to rebuild OpenDog completely. The solution \[James\] went with is a redesigned foot with an inbuilt switch, to confirm that the foot is touching the ground, and a load cell attached in the middle of the bottom leg segment. The load cell is bolted rigidly onto the leg segment, which allows it to sense when the leg is carrying load, without damaging the load cell itself.

Unfortunately all the serial ports on OpenDog’s main Teensy 3.6 controller are already used, so he converted the signal from the load cell to PWM, to allow it to be read by a normal GPIO pin. This works well in isolation, but when \[James\] switches on the motors, the PWM signal from the load sensor gets flooded by interference, making it unreadable. To solve this problem, he wants to implement a CAN bus, which will allow for more inputs and outputs and hopefully solve the interference problem. However, \[James\] has no experience with the CAN protocol, so learning to use it is going to be a project on its own.

[OpenDog](https://hackaday.com/2018/06/11/james-bruton-is-making-a-dog-opendog-project/) is turning into a very lengthy, time-consuming project, \[James\] says that the lessons learned from it have been invaluable for a number of other projects. This is something to keep in mind with everything we tackle. Choose projects were the experience gained and/or relationships developed are worth it on their own, even when the project fails in a conventional sense. This way you can never really lose.

  
  
from Hackaday https://ift.tt/35pQgEQ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)