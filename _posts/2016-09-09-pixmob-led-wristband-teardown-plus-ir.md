---
title: 'PixMob LED Wristband Teardown (Plus IR Emitters and How To Spot Them)'
date: 2019-11-26T13:04:00+01:00
draft: false
---

PixMob units are wearable LED devices intended for crowds of attendees at events like concerts. These devices allow synchronized LED effects throughout the crowd. \[yeokm1\] [did a teardown](http://yeokhengmeng.com/2019/08/teardown-of-ndp2019-led-wristband/) of one obtained from a preview for the 2019 Singapore National Day Parade (NDP), and in the process learned about the devices and their infrastructure.

![](https://hackaday.com/wp-content/uploads/2019/11/PixMob-Suspected-IR-Emitter.jpg?w=400)

Suspected IR emitter for the PixMob units, mounted on a lighting tower (marked here in white).

PixMob hardware has been known to change over time. This version has two RGB LEDs (an earlier version had only one), an unmarked EEPROM, an unmarked microcontroller (suspected to be the Abov MC81F4104), and an IR receiver module. Two CR1632 coin cells in series power the device. \[yeokm1\] has made the schematic and other source files available [on the teardown’s GitHub repository](https://github.com/yeokm1/ndp2019-wristband-teardown) for anyone interested in a closer look.

One interesting thing that \[yeokm1\] discovered during the event was the apparent source of the infrared emitter controlling the devices. Knowing what to look for and reasoning that such an emitter would be mounted with a good view of the crowd, \[yeokm1\] suspected that the IR transmitter was mounted on a lighting tower. Viewing the tower through a smartphone’s camera revealed a purplish glow not visible to the naked eye, which is exactly the way one would expect an IR emitter to look.

Sadly, there wasn’t any opportunity to record or otherwise analyze the IR signals for later analysis but it’s possible that the IR protocol might be made public at some point. After all, [running custom code on an earlier PixMob board was made possible](https://hackaday.com/2019/10/15/hacking-pixmob-bands-and-finding-a-toolchain/) in part by asking the right people for help.

  
  
from Hackaday https://ift.tt/2sliFOR  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)