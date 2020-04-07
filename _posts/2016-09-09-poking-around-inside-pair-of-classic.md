---
title: 'Poking Around Inside A Pair of Classic Gaming Gifts'
date: 2020-01-08T07:13:00+01:00
draft: false
---

Retro gaming is huge right now, and like probably millions of other people, \[wrongbaud\] found himself taking possession of a couple faux-classic gaming gadgets over the holidays. But _unlike_ most people, who are now using said devices to replay games from their youth, [he decided to tear into his new toys to see how they work](https://wrongbaud.github.io/Holiday-Teardown/).

The first to get pulled apart is a handheld _The Oregon Trail_ game, which Hackaday readers may recall from [a teardown we did back when it was first released](https://hackaday.com/2018/03/14/teardown-the-oregon-trail-handheld/). His work continues right where our teardown left off, by pulling the game’s two EEPROM chips out and dumping their contents. As expected, \[wrongbaud\] found that the I2C connected chip contained the game save information, and the SPI flash chip stored the actual game files.

[![](https://hackaday.com/wp-content/uploads/2020/01/retrogifts_detail.jpg?w=300)](https://hackaday.com/wp-content/uploads/2020/01/retrogifts_detail.jpg)Next up was an HDMI “stick” from Bandai Namco that allows the user to play a selection of NES games. Here again \[wrongbaud\] liberates the flash chip and dumps it for examination, this time using an ESP32 tool of his own creation. Inside the firmware image he’s able to identify several elements with the help of `binwalk`, such as splash screen graphics and text strings.

But perhaps most interestingly, he found that `binwalk` was able to automatically extract the NES ROMs themselves. After verifying they were standard ROMs with an NES emulator, he theorizes that repacking the firmware with different ROMs should be possible should anyone feel so inclined.

Both of these hacks are fantastic examples of how you can reverse engineer a device’s firmware with low cost hardware, open source tools, and a healthy dose of patience. Even if you aren’t interested in fiddling with _The Oregon Trail_ or swapping out the _Mappy_ ROM for _Contra_, this write-up is an invaluable resource for anyone looking to do their own firmware analysis.

This isn’t the first time \[wrongbaud\] has hacked around inside these extremely popular retro games, either. Just last month we covered some of his [previous exploits with the re-released versions of _Rampage_ and _Mortal Kombat_](https://hackaday.com/2019/12/06/swapping-the-roms-in-mini-arcade-cabinets/).

  
  
from Hackaday https://ift.tt/35AnUb0  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)