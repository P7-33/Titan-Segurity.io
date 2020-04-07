---
title: 'Bask In The Glory Of This 336 LED Digit Display'
date: 2020-01-18T22:14:00+01:00
draft: false
---

\[Chris Combs\] recently took the wraps off of [an incredible art piece that he calls _Road Ahead_](http://chriscombs.net/2019/12/29/the-road-ahead/index.html) which uses 336 seven segment LED digits to create an absolutely gorgeous display. With a piece of smoked acrylic to slightly diffuse the orange glow of the LEDs, the end result has a distinctively retro look that we’d gladly spend all day staring at.

For those looking to dig a bit deeper, \[Chris\] has put together [some very impressive documentation over on Hackaday.io](https://hackaday.io/project/169244-336-digit-7-segment-display-with-per-segment-pwm) that goes into plenty of detail on how he designed and built this beauty. From the design of the PCBs that carry all of the 0.3″ SMD displays to the custom software running on the Raspberry Pi 3 that powers it, there’s no technical stone left unturned.

[![](https://hackaday.com/wp-content/uploads/2019/12/roadahead_detail2.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/12/roadahead_detail2.jpg)According to the build log, this is the second version of the display. The first one was housed in a rather attractive wooden enclosure, but as \[Chris\] explains, that was precisely the problem. He wanted something that looked cold and unfeeling as the nearly 340 digits flashed away with potentially ominous intent. So he ditched the wooden case for a powder coated steel one that looks more like the front panel of a mainframe than something you’d pick up at the craft store.

Another interesting point explained in the write-up is how the Python software is designed to treat the hardware as a contiguous graphical display rather than just an array of independent digits. Grayscale images can be reproduced on the by using PWM to adjust the brightness of each segment’s corresponding “pixel”; though admittedly it takes a bit of imagination to see the intended image with a resolution this low.

This project reminds us of the [incredible LED hexdump display we saw not that long ago](https://hackaday.com/2019/12/20/movie-style-hacking-with-a-wall-of-glowing-hex/), down to the PWM trickery for squeezing “graphics” out of these exceptionally non-graphical elements. With any luck, perhaps these are the opening shots in an arms race to see who can build the largest array of multi-segment LED displays.

  
  
from Hackaday https://ift.tt/2v2voap  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)