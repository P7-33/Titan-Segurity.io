---
title: 'Old Rotary Phone Gets Called Into Action'
date: 2020-02-04T10:02:00+01:00
draft: false
---

The more glass we punch with our fingertips, the more we miss fun physical interfaces like the rotary phone. Sure, they took forever to dial, and you did not want to be one of those kids stuck with one during the transition to DTMF, especially if you were trying to be the 9th caller to a radio station, but the solidly electromechanical experience of it all was just cool, okay? The sound and the heft made them seem so adult.

\[Tal O\] gets it. [He’s all but finished bringing this old girl into the 21st century without giving anything away on her surface](https://www.hackster.io/talofer99/taking-a-rotary-dial-phone-into-the-future-c974b2). Inside are some things you’d expect, like a SIM800 GSM module for the telephony part, and an ESP32 to count the pulses from the dialer and communicate between it and the GSM module. But it also has a few things we haven’t seen before. The entire journey is outlined in a five-part video series, and we’ve got part one dialed in for you after the break.

Although \[Tal\] got the ringer working to prove it could be done, he didn’t want to have a separate 12V circuit just to run the bells. Also, the bells and their electromagnets take up a lot of space, so he compromised with an mp3 of a rotary ringer. \[Tal\] also wanted a way to have dialed-number feedback without cutting up the phone to add a screen, so he found a text-to-speech library and made the phone speak each number aloud as soon as it’s dialed. It uses the same internal speaker as the ringer, but we think it would be neat if the feedback came through the handset speaker.

If \[Tal\] is looking for another modern convenience to add to this phone, how about [speed dial](https://hackaday.com/2019/09/24/finally-a-rotary-cell-phone-with-speed-dial/)?

  
  
from Hackaday https://ift.tt/36P8DUA  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)