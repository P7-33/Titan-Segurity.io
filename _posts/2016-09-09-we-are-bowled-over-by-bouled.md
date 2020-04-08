---
title: 'We Are Bowled Over by the BouLED'
date: 2019-11-09T04:06:00+01:00
draft: false
---

We’ve seen a lot of cubic LED creations recently, but this one takes it a bit further. The [BouLED is a work-in-progress icosahedric LED display](https://rose.telecom-paristech.fr/2019/bouled), a globe-like sphere made of 20 flat triangular LED-lit faces. When combined with sensors inside the display, it will be able to stabilize the image. In other words: you can pick it up and rotate it, but the image will stay steady. It is created as part of their degree work by \[Matthias Rabault\], \[Lucas Lebailly\] and \[Hichem Ghandri\] who are students at the Télécom Paris school.

The [prototype the team has put together so far](https://hackaday.io/project/168026-bouled) is a thing of beauty that seems to work pretty well. Each of the triangles is basically a long string of LEDs, and the panels connect to the STM32H7 controller that runs the whole thing. There is also an ESP32 that connects the device to WiFi.

It is also worth reading over the various stages to see how the project developed, from their initial design to the first running prototype that they have now. The team did a lot of iterative design, including trying 3D printing and laser cutting, before they came up with a final PCB design for the triangular surface and started building it out. One of the interesting choices they made was to put a lot of work into writing a simulator, as they realized that this could be used to both finalize the algorithms that translate the image onto the display and to drive the final version.

![BouLED1](https://hackaday.com/wp-content/uploads/2019/10/BouLED1.gif)

  
  
from Hackaday https://ift.tt/33CmEnW  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)