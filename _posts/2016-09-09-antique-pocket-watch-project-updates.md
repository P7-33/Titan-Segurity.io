---
title: 'Antique Pocket Watch Project Updates Antique Pocket Watch'
date: 2019-12-09T07:32:00+01:00
draft: false
---

Here at Hackaday we have a bit of a preoccupation with timepieces. Maybe it’s the deeply personal connection to an object you wear on your body, or the need for ultimate reliability. Perhaps it’s just a fascination with the notion of time itself. Whatever the case, we don’t seem to be alone as there is a constant stream of time-related projects coming through our virtual doors. For this article we’ve unearthed the [LED Pocketwatch 1.0 by \[Dr. Paul Pounds\]](https://web.archive.org/web/20160322025932/http://www.eng.yale.edu/pep5/pocket_watch.html) from way back in 2009 (ironically via a [post about a wristwatch](https://hackaday.com/2018/07/05/leds-make-an-analog-wristwatch/) from last year!). Fortunately for us the Internet Archive has saved this heirloom nouveau from the internet dustbin so we can appreciate the craftsmanship involved in \[Dr. Pounds\]’ work.

![](https://hackaday.com/wp-content/uploads/2019/11/led_pw_v1.0_pcb_back.jpg)

Check out the wonderful, spiral routing!

My how far we’ve come; a decade after this project was posted a hacker might choose to 3d print a case for a new wearable, but in 2009 that would have been an entire project by itself! \[Dr. Pounds\] chose to use the casing from an antique [Elgin pocket watch](https://en.wikipedia.org/wiki/Elgin_National_Watch_Company). Even through the mists of a grainy demo video we can imagine how soft the well-worn casing must be from heavy use. This particular unit was chosen because it was a hefty 50mm in diameter, leaving plenty of room inside for a 44mm double sided PCBA with 133 0603 LEDs (60 seconds, 60 minutes, 12 hours), a PIC 16F946, an [ERM](https://www.precisionmicrodrives.com/vibration-motors/eccentric-rotating-mass-vibration-motors-erms/), and a 110mAh LiPo. But what really sets the LED Pocketwatch 1.0 apart is the user interface.

The ERM is attached directly to the rear of the case in order to best conduct vibration to the outside world. For maximum authenticity it blips on the second, to give a sense that the digital watch is mechanically ticking like the original. The original pocket watch was designed with a closing lid which is released when the stem is pressed. \[Dr. Pounds\] integrated a button and encoder with the end of the stem (on the PCBA) so the device can be aware of this interaction; on lid open it wakes the device to display the time on the LEDs. The real pièce de résistance is that he _also _integrated a minuscule rotary encoder, so when the stem is pressed you can rotate it to set the time. It’s all quite elegantly integrated and imminently usable.

![](https://hackaday.com/wp-content/uploads/2019/11/led_pocketwatch_v1.0_iso-e1575135683267.jpg?w=800)

At this point we’d love to link to sources, detailed drawings, or CAD files, but unfortunately we haven’t found any. If this has you inspired check out some of the [other](https://hackaday.com/2016/09/15/hackaday-prize-entry-neopixel-pocket-watch/) [pocket watches](https://hackaday.com/2012/11/30/led-pocket-watch-2/) we’ve posted about in the past. If you’re interested in a live demo of the LED Pocketwatch 1.0, check out the original video after the break.

  
  
from Hackaday https://ift.tt/2P0Mc9g  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)