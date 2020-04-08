---
title: 'Behind the Scenes of the 2019 Superconference Badge'
date: 2019-11-17T04:03:00+01:00
draft: false
---

If you count yourself among the several hundred of our closest friends that have joined us at Supplyframe HQ for the 2019 Hackaday Superconference, then by now you’ll have your hands on [one of this year’s incredible FPGA badges](https://hackaday.com/2019/11/04/gigantic-fpga-in-a-game-boy-form-factor-2019-supercon-badge-is-a-hardware-siren-song/). It should come as no surprise that an incredible amount of time and effort went into developing and manufacturing this exceptionally unique piece of hardware; the slick gadget in your hands today took nearly an entire year to develop, and work continued on it until very literally the last possible moment.

[![](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_thumb.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_thumb.jpg)Badge designer Jeroen Domburg (aka Sprite\_TM), Hackaday staff, and a team of dedicated volunteers were still putting the final touches on these ambitious devices less than 24 hours before they were distributed to the first wave of Superconference attendees. Naturally, that’s not _exactly_ how things were supposed to go. But when you’ve got a group of people that want to push the envelope and build something truly incredible, convincing them to actually stop working can be a challenge in itself.

In fact, [development of the badge is still ongoing](https://github.com/Spritetm/hadbadge2019_fpgasoc). Fixes and improvements are being made to the software even as you read this, and if you haven’t already, you should upgrade your badge to make sure you’ve got the latest and greatest from our international team of wizards. We all know that conference badges have an unfortunate habit of languishing on the shelf and collecting dust, but the 2019 Superconference badge was built to challenge you for longer than just one weekend. Consider yourself warned: for every Supercon badge that gets tossed in a drawer come Monday, Sprite\_TM will shed a single tear.

After the break, come along as we turn back the clock and take a look at the last minute dash to get 500+ badges programmed and ready to go before the doors opened for the 2019 Hackaday Superconference.

Some Assembly Required
----------------------

[![](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_boxes.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_boxes.jpg)It certainly sounded easy enough. The assembled badges had already arrived at Supplyframe HQ, they just needed to be unpacked, get a fresh set of batteries installed, go through a quick hardware check, and then finally get programmed. Unwrapping each badge and slotting a pair of AA batteries in it wasn’t difficult work of course, but it was enough to keep a few volunteers busy for a good chunk of the morning.

Then we started running into issues. On some badges the display was only partially operable, but we quickly found that re-seating the ribbon cable seemed to resolve the issue. The battery holders on some badges were installed upside down, several dodgy power switches were discovered, and a few simply wouldn’t power on. Pretty soon there was a box full of badges that needed further diagnostics, and by the time Supercon kicked off, there were still a handful of badges that hadn’t been revived. But in the end we managed to get approximately 95% of them to pass our initial QC.

[![](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_unpacking.jpg?w=800)](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_unpacking.jpg)

While the badges were getting powered up and checked out, a separate group of workers had the unenviable task of removing the blank “cartridge” and tiny speaker from their respective shipping packages and combining them in their own ESD bag. Not wanting to force such mind-numbing work on anyone else, this particularly loathsome task was handled largely by the Hackaday Editors. So the next time you see an article you dislike on the site, just take a few deep breaths and imagine us plucking hundreds of tiny speakers out of their foam packing trays you can see to the left side of this photo.

The Flash Cart Shuffle
----------------------

[![](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_flashing.jpg?w=396)](https://hackaday.com/wp-content/uploads/2019/11/badgebuilding_flashing.jpg)

The three stages of badge flashing.

In a perfect world, the software for the badges would have been pre-installed when the hardware was assembled. But from critical issues like image artifacts when connecting the badge to HDMI displays to making the LEDs flash when you clear a line in the built-in _Tetris_ clone, there were a myriad of changes still being made even as the badges were all lined up and ready to get flashed. Once everyone was satisfied with where their respective software components were, we immediately started programming.

Being a technical audience, you’re probably wondering how we manually flashed all of these badges. JTAG? USB? No, Sprite\_TM had a better idea than that. His vision was always to allow the badge to be updated from a specially prepared “flash cart”. With one of these cartridges slotted in, the badge simply needed to be turned on to begin the flashing process. No wires to connect, no computer required. Each person on the assembly line was given two of these magic cartridges and a box of badges to work their way through, and once you got the rhythm down, you’d have the first badge flashed and bagged up just as the second one was ready to go.

Now It’s Your Turn
------------------

With the knowledge that the 2019 Superconference badge in your possession was literally passed around by a large chunk of the Hackaday staff before it ended up in your stylish black tote, we hope you’ll do us proud. [The badge was specifically designed](https://www.youtube.com/watch?v=X39nnPWmkvA) to make the exciting world of FPGAs as approachable as possible, and there’s no shortage of folks wandering the halls of Supercon (staff or otherwise) who will be happy to get you started. Even if you can’t finish your project this weekend, the [official Supercon chat has turned into a hive mind of ambitious badge hackers](https://hackaday.io/messages/room/280647) that will be more than happy to welcome a few new members to the fold after we all begin heading for home come Monday.

But no matter what you do, just remember to have fun and keep an open mind. The badge in your hand is without question the shape of things to come, and more than anything else, we hope it proves to be a useful tool as you tackle the next generation of electronic hacking.

  
  
from Hackaday https://ift.tt/2OwN307  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)