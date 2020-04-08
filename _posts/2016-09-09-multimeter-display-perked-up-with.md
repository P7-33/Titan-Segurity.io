---
title: 'Multimeter Display Perked Up With Nixies, LEDs, And Neon Tubes'
date: 2019-10-31T03:02:00+01:00
draft: false
---

Just because something is newer than something else doesn’t automatically make it better. Of course the opposite is also true, but when it comes to displays on bench multimeters, a fancy LCD display is no guarantee of legibility. Take the Hewlett Packard HP 3478A multimeter; the stock transflective display with its 14-segment characters is so hard to read that people usually have to add a backlight to use it.

That wasn’t good enough for \[cyclotronboy\], though, who chose to [completely replace the stock 3478A display with Nixie tubes](https://www.eevblog.com/forum/testgear/nixie-display-for-hp3478a/). He noticed that with a little modification, six IN-17 tubes just fit in the window vacated by the LCD. He sniffed out the serial data stream going to the display with a collection of XOR gates and flip-flops, which let him write the code for a PIC18F4550. The finished display adds a trio of rectangular LEDs for the + and – indicators, and an HDLO-1414 four-character alphanumeric display to indicate units and the like. And the decimal points? Tiny neon bulbs. It already looks miles better than the stock display, and with the addition of a red filter, it should look even better.

If you’re stuck with a lame LCD multimeter but Nixies don’t quite do it for you, worry not – [an LED conversion](https://hackaday.com/2017/11/15/leds-give-hp-3457a-ddms-lcd-display-the-boot/) is possible too.

  
  
from Hackaday https://ift.tt/2WulFDa  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)