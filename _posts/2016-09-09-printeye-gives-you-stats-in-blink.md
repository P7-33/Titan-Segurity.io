---
title: 'PrintEye Gives You Stats in a Blink'
date: 2019-10-03T12:07:00+01:00
draft: false
---

Once upon a time, most things were single-purpose, like the pocket watch. Then somebody made a watch with a date function, and next thing you know, we had TV/VCR combos and Swiss army knives. Now, people pull computers out of their pockets just to check the time or the bed temperature of their RepRap.

\[Owen\]’s antidote for this multi-function madness is [PrintEye, a simple interface that queries his printer and displays its vital signs on a pair of OLED peepers](https://hackaday.io/project/167589-printeye). It’s a parts bin special, and you know how much we love those. PrintEye connects to the Duet controller over UART, and does its firmware whispering with an ATMega328P. The ‘Mega sends a single M-command and gets back all the status and temperature data in JSON format. Then it parses the info and displays it on twin OLED screens.

Want to make one? \[Owen\]’s got all the files you need over on IO, but offers no hand-holding services. If you’ve never spun a board before, this could be your introduction. Have to have an internet connection? Check out [the Octoprint monitor that inspired PrintEye](https://hackaday.com/2018/11/05/esp8266-monitor-keeps-an-eye-on-octoprint/).

  
  
from Hackaday https://ift.tt/2nYcKNQ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)