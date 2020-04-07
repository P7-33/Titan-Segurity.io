---
title: 'Porting Quake to an iPod classic is no Easy Task'
date: 2020-01-26T01:38:00+01:00
draft: false
---

We didn’t think we’d see another hack involving the aging iPod Classic here on Hackaday again, yet \[Franklin Wei\] surprises us with [a brand new port of Quake for the sixth-generation iPod](https://www.fwei.tk/blog/adieu-quake.html) released some thirteen years ago. Is Quake the new 90s FPS that’ll get put into every device hackers can get their hands on?

The port works on top of RockBox, a custom firmware for the iPod and other portable media players. This isn’t the first game on the device. A source port of Doom has been available for years. \[Franklin\] decided to use [Simple DirectMedia Layer (SDL)](https://en.wikipedia.org/wiki/Simple_DirectMedia_Layer) to make his job easier. That doesn’t mean this was an easy task though, as \[Franklin\] describes very interesting bugs that kept him from finishing his work for about two years.

The first problem was that the GCC compiler he was using was apparently not optimizing time-critical sound mixing routines. \[Franklin\] decided enough was enough and dug into ARM assembly to re-write those parts of the code by hand. He managed to squeeze out a speed increase of about 60%. Even better, he ran into a prime example of a bug that would get triggered by a very specific sound sample length running through his code. Thankfully, with all of that sorted, the port is now released and we can all enjoy cramping our hands around tiny screens to frag some low-poly monsters.

If you need to repair your sixth-generation iPod before you can do that though, no need to worry since [they seem to not be so hard to service by yourself](https://hackaday.com/2018/03/30/giving-a-6th-generation-ipod-a-new-lease-on-life/). And if the battery life and disk space aren’t quite what they used to be, there’s also the option to [bulk it up for winter](https://hackaday.com/2016/07/02/the-2000gb-ipod-you-wished-for-in-the-00s-is-an-isore/). Check out the Quake port in action after the break.

  
  
from Hackaday https://ift.tt/3aNDwvZ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)