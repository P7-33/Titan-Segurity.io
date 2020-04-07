---
title: 'FET based Motor Driver is Better than L298N'
date: 2019-12-29T10:26:00+01:00
draft: false
---

If you want to build a small robot with a motor, you are likely to reach for an L298N to interface your microcontroller to the motor, probably in an H-bridge configuration. \[Dronebot\] has used L298N chips like this many times. In the video below, he uses a TB6612FNG instead, taking advantage of the device’s use of MOSFETs. The TB6612 may be a little more expensive, but it’s clearly worth it.

You can get breakout boards for the tiny chips. \[DroneBot\] looks at several ready-to-go breakout boards. They are not drop-in compatible, though. For example, the L298N can operate motors from 4.5 to 46V while the TB6612 can go from 2.5 to 13.5V on the motor voltage. The L298N also handles more current. However, because of its relatively low efficiency, it needs a heat sink. The TB6612 boasts up to 95% efficiency and also has a low current standby mode. Of course, the TB6612 drops much less voltage which is great if you are using low voltage motor.

Assuming the new device is suitable for your hardware, the software isn’t really very different from L298N programs. If you know how to use the L298N, you can probably just snag a break out board, download the library, and be off to the races — no pun intended.

If you want more [basics on the h-bridge](https://hackaday.com/2014/04/25/a-h-bridge-motor-controller-tutorial-makes-it-simple-to-understand/), we’ve covered it many times. Of course, you can always use [relays](https://hackaday.com/2011/04/14/reversible-relay-based-motor-controller/) if you want real old school.

  
  
from Hackaday https://ift.tt/2SB9HYw  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)