---
title: 'Making a robot cleaner even smarter'
date: 2019-10-20T12:01:00+01:00
draft: false
---

Some electric cleaners are effective and some hardly even seem to make a difference. The ILIFE V7s may be a robot cleaner, but even with its cleaning modes and anti-collision system, it still requires IR signals to complete any tasks. Tired of having to be physically in the same place as his robot cleaner, \[pimuzzo\] decided to take matters into his own hands and build a [RESTful remote control](https://github.com/pimuzzo/ilifev7s-rest-remote) to send IR signals from afar.

The program uses the [ESP8266WebServer](https://github.com/esp8266/Arduino/tree/master/libraries/ESP8266WebServer) and [IRremoteESP8266](https://github.com/crankyoldgit/IRremoteESP8266) libraries for handling HTTP requests and sending and receiving infrared signals. The remote also respond to [Actions on Google](https://github.com/pimuzzo/actions-on-google) for controlling the robot over a Google Assistant.

![](https://hackaday.com/wp-content/uploads/2019/10/ir-signals.jpg?w=400)

The IR signals are a bit funky – as one user highlighted, finding the IR protocol is a nontrivial task that can be accomplished by recording the IR signals from the original remote with a IR receiver and matching the marks, spaces, and carrier frequency with those of known protocol codes. \[Oitzu\] was able to [match the timing](https://github.com/z3t0/Arduino-IRremote/issues/354) to the NEC 32 bit protocol and find the exact codes on an oscilloscope, which simplified the translation of the codes for the remote.

Sometimes when life gives you a robot cleaner, it’s your job to make it smarter.

  
  
from Hackaday https://ift.tt/2P4rZzU  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)