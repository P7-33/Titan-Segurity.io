---
title: 'Pulling Display Data off of a Fitness Tracker'
date: 2019-10-28T03:06:00+01:00
draft: false
---

\[Aaron Christophel\] writes in with yet another clever hack for his D6 Fitness Tracker. Using OpenOCD and Pygame, he shows how you can [pull data right off the tracker’s screen](https://www.youtube.com/watch?v=5ymh3p8gKiQ) and sent it to the computer.

This one appealed to us for its brevity. First \[Aaron\] launches the OpenOCD server which connects to the D6. Then, a short Python script connects to the server through telnet, reads the screen data, and uses a look-up table to turn the data into a duplicate display on the PC screen. If you’re more of a visual learner, there’s a demonstration video after the break.

The D6 is a popular fitness tracker that’s often re-branded and sold at a very low cost. \[Aaron\] is a big fan of these Nordic nRF52 powered devices, and [we’ve covered some of his hacks before.](https://hackaday.com/2019/08/23/ota-flash-tool-makes-fitness-tracker-hacking-more-accessible/) If you’d like to learn more about these interesting little devices there’s [quite a write-up on their inner-workings here](https://github.com/fanoush/ds-d6).

  
  
from Hackaday https://ift.tt/348grQh  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)