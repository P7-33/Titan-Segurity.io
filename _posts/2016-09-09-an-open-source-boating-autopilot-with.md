---
title: 'An Open Source Boating Autopilot With Some Custom Tweaks'
date: 2019-12-18T01:27:00+01:00
draft: false
---

Piloting a boat is all well and good, but can get dull when you’d rather be reclining on the deck with a cold beverage in hand. For \[Timo Birnschein\], this simply wouldn’t do. [He began to gather parts to put together an autopilot to keep his boat on the straight and narrow](https://hackaday.io/project/168592-opencpn-chart-plotter-w-autopilot-and-waypoints).

The build is based around OpenPlotter, which uses a battery of marine-ready software to handle routing charts, autopiloting, and providing a compass heading for navigation. Naturally, it all runs on a Raspberry Pi. In combination with PyPilot, it can be used to let the vessel drive itself around a series of waypoints, allowing you to soak up the atmosphere on the water without having to constantly steer the craft.

\[Timo\] ran into some issues, however, with the hardware side of things. Existing implementations for motor control to drive the rudder weren’t quite cutting it, so the system was reworked to run with a robust H-bridge and some fresh Arduino code. This was combined with a custom rudder sensor built with a potentiometer and some 3D printed gears. Future work aims to double up the rudder sensors for redundancy, [something we should all consider at times.](https://hackaday.com/2019/03/14/mcas-and-the-737-when-small-changes-have-huge-consequences/)

Overall, the system is starting to come together, and \[Timo\]’s enjoying letting his boat think for itself. He notes that it’s very important to keep an eye on the boat while operating in this condition, lest it veer off course – many a boat has been lost this way. [We’re always supporters of a mature attitude towards autonomous vehicle operations!](https://hackaday.com/2019/11/07/teslas-smart-summon-gimmick-or-greatness/)

  
  
from Hackaday https://ift.tt/2ttXpXE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)