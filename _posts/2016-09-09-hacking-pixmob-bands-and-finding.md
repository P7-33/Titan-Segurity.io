---
title: 'Hacking Pixmob Bands And Finding A Toolchain'
date: 2019-10-15T12:05:00+01:00
draft: false
---

The Pixmob band is an LED wrist strap, of the type often used at big concerts or other public events. Many have tinkered with the device, but as of yet, nobody was running custom code. It wouldn’t be easy, [but \[Adrian\] got down to work.](http://jg.sn.sg/ndp-pixmob-1/)

![](https://hackaday.com/wp-content/uploads/2019/10/pixmobseseees-1.jpg?w=400)

The wristbands are given out to concertgoers to create synchronized light shows in the crowd.

A teardown of a 2016 device revealed it consisted of an RGB LED, an IR sensor, a small EEPROM and a coin cell, which were all common parts. Unfortunately, the ABOV MC81F4204 microcontroller was a little more obscure. It’s a part that’s quite hard to find, and uses a proprietary programmer and an ancient IDE.

Searches online proved fruitless, and a working programmer remained outside \[Adrian\]’s grasp. Undeterred, he decided to simply walk into the company’s Korean headquarters and ask for help. As the part was end-of-life, they were unable to supply a programming device, but happily provided documentation for the chip that wasn’t publicly available. With this in hand, it was possible for \[Adrian\] to build his own programmer instead.

Booting up a copy of the ABOV IDE, with his newly-built programmer in hand, it was relatively easy to get the chip running custom code. Going the extra mile, \[Adrian\] even hacked the Arduino IDE to be partially compatible with the platform! A silicon error in the MC81F4204 design bricks the chips after only a few flash rewrites, so its never going to be the most useful platform, but it works nonetheless.

The Pixmob hardware has continued to evolve, and it’s unlikely modern units still use the same chip. Despite this, it’s a great example of what can be achieved by a little sleuthing and asking the right people the right questions. Others have attempted to hack similar products before, found at [Disneyland](https://hackaday.com/2012/06/22/hackaday-links-june-22-2012/) and [Coldplay concerts.](https://hackaday.com/2012/02/19/ask-hackaday-did-you-catch-the-grammys/) You won’t catch this author at either, but if you’ve hacked something similar, [be sure to reach out on the tip line!](http://hackaday.com/submit-a-tip)

  
  
from Hackaday https://ift.tt/2oJlzLI  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)