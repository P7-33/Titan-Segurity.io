---
title: 'Tiny SAO, Tough CTF Challenge!'
date: 2019-11-07T10:11:00+01:00
draft: false
---

Over the year or two since the SAO connector specification was published, otherwise known as the _Shitty Addon_, we’ve seen a huge variety of these daughter boards for our favourite electronic badges. Many of them are works of art, but there’s another subset that’s far less about show and more about clever functionality. [\[Uri Shaked\]’s little SAO](https://blog.wokwi.com/capture-the-flag-shitty-add-on/) is rather unprepossessing to look at, being a small round PCB with only an ATtiny microcontroller, reset button, and solitary LED, but its interest lies not in its looks but its software. It contains a series of CTF puzzles within, and despite its apparent simplicity should contain enough to detain even the hardiest puzzle-solving hackers.

It’s a puzzle of three parts, at the simplest level merely flashing the LED is enough, while the next level involves retrieving a buried string from the firmware and the last requires replacing the string with one of your own. You are only allowed to do so through the SAO connector, but fortunately you do have the benefit of access to the [source code](https://github.com/urish/ctf-shittyaddon/blob/master/ctf-firmware/ctf-firmware.ino) to trawl for vulnerabilities. There is a hefty hint that the data sheet for the microcontroller might also be useful.

\[Uri\] has appeared many times on these pages, most recently when he [added a microscope to his 3D printer](https://hackaday.com/2019/08/03/add-a-microscope-to-your-3d-printer/).

  
  
from Hackaday https://ift.tt/2JUucuc  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)