---
title: 'Little Hex Tricks Make Little Displays a Little Easier'
date: 2020-01-25T04:08:00+01:00
draft: false
---

Depending on the device in hand and one’s temperament, bringing up a new part can be a frolic through the verdant fields of discovery or an endless slog through the grey marshes of defeat. One of the reasons we find ourselves sticking with tried and true parts we know well is that interminable process of _configuration_. Once a new display controller is mostly working, writing convenience functions to make it easier to use can be very satisfying, but the very first thing is figuring out how to make it do anything at all. Friend of Hackaday \[Dan Hienzsch\] put together a post describing [how to use a particular LED controller](https://rheingoldheavy.com/i2c-display-v2-tutorial-02-displaying-patterns/) which serves as a nice walkthrough of figuring out the right bitmath to make things work, and includes a neat trick or two.

The bulk of the post is dedicated to describing the way \[Dan\] went about putting together his libraries for a 7-segment display demo board he makes. At its heart the board uses the IS31FL3728 matrix driver from ISSI. We love these ISSI LED controllers because they give you many channels of control for relatively low cost, but even with their relative simplicity you still need to do some bit twiddling to light the diodes you need. \[Dan\]’s post talks about some strategies for making this easier like preconfigured lookup tables with convenient offsets and masking bits to control RGB LEDs.

![](https://hackaday.com/wp-content/uploads/2020/01/ENSZp0sUcAEQB6I.png)

There’s one more trick which we think is the hidden star of the show; a spreadsheet which calculates register values based on “GUI” input! Computing the bit math required to control a display can be an exercise in frustration, especially if the logical display doesn’t fit conveniently in the physical register map of the controller. A spreadsheet like this may not be particularly sexy but it gets the job done; exactly the kind of hack we’re huge fans of here. We’ve [mirrored the spreadsheet](https://docs.google.com/spreadsheets/d/1QnVJqyZd8T29Ften13fpkoY8iB3mTpD5iG5B_KSwkqA/edit?usp=sharing) so you can peek at the formulas inside, and the original Excel document is available on his blog.

  
  
from Hackaday https://ift.tt/2RIOVnW  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)