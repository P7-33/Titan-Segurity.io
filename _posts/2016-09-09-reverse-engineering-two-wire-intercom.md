---
title: 'Reverse Engineering A Two-Wire Intercom'
date: 2019-10-27T15:06:00+01:00
draft: false
---

There was a time when an intercom was simply a pair of boxes with speakers joined by a couple of wires, with an audio amplifier somewhere in the mix. But intercoms have like everything else joined the digital age, so those two wires now carry a load of other functionality as digital signalling. \[Aaron Christophel\] installs these devices for a living, and has posted [a fascinating reverse engineering video](https://www.youtube.com/watch?v=xFLoauqj9yA) that we’ve also placed below the break.

Power for the system is present as a constant 24V DC, and the audio is still an old-fashioned analogue signal that we’ll all be familiar with. On that 24V DC though are imposed a series of pulse trains to trigger the different alarms and other functions, and he describes extracting these with an oscilloscope before showing us the circuitry he’s used to send and receive pulses with an Arduino. The bulk of the video is then devoted to the software on the Arduino, which you can also find [in a GitHub repository](https://github.com/atc1441/TCSintercomArduino).

The result is an interesting primer for anyone who fancies a bit of serial detective work, eve if they don’t have a intercom to hand.

  
  
from Hackaday https://ift.tt/2plqZgf  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)