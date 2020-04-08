---
title: 'Retro Hardware Plots Again Thanks to Grbl and ESP32'
date: 2019-10-24T09:16:00+01:00
draft: false
---

When it comes to building a new CNC machine, you’ve got a wide world of controller boards to choose from. Whether you’re building a 3D-printer or a CNC plasma cutter, chances are good you’ll find a controller that fits your needs and your budget. Not so much, though, when you want to add CNC to a pen plotter from the early days of the PC revolution.

\[Barton Dring\] just posted [the last installment of a five-part series](http://www.buildlog.net/blog/2019/10/inktober-project-2019-post-5/) in which he documented putting an Atari 1020 plotter under CNC control. The plotter was a peripheral for the Atari line of 6502 machines from the late 1970s; the guts of the little roll-fed, ballpoint-pen plotter appeared in Commodore, Tandy, and TI versions as well. \[Bart\]’s goal was to not add or modify anything to the mechanically simple device apart from the controller. That was easier said than done, given the unipolar stepper motors controlling the pen position and paper roll, and the fact that the pen lift mechanism uses a solenoid. Support for those had to be added to [his Grbl\_ESP32 firmware](https://hackaday.com/2018/07/26/grbl-ported-to-the-esp32/), as did dealing with the lack of homing switches in the plotter, and adapting the Grbl tool change command to the pen color change mechanism, which rotates the pen holder by bumping it into the right-hand carriage stop. The stock controller was replaced by a custom PCB that fits perfectly within the case, with plenty of room to spare. The video below shows it plotting out a vexillogically relevant sample.

From [custom coasters](https://hackaday.com/2018/12/26/make-an-impression-at-the-bar-with-a-cnc-coaster-plotter/) to [wooden nickels](https://hackaday.com/2018/12/26/make-an-impression-at-the-bar-with-a-cnc-coaster-plotter/) to [complex string art](https://hackaday.com/2019/02/23/polar-platform-spins-out-intricate-string-art-portraits/), \[Bart\] has really put Grbl through the wringer. We really like this retro-redo, though, and fully support his stated desire to convert more old hardware to Grbl\_ESP32.

  
  
from Hackaday https://ift.tt/33Q10fw  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)