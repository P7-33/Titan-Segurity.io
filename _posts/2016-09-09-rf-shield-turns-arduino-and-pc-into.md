---
title: 'RF Shield Turns Arduino (And PC) into Shortwave Radio'
date: 2020-02-15T04:10:00+01:00
draft: false
---

Microcontrollers tend to consume other kinds of electronics. A project you might once have done with a 555 now probably has a cheap microcontroller in it. Music synthesizers? RC controllers? Most likely, all microcontroller-based now. We always thought RF electronics would be immune to that, but the last decade or two has proven us wrong. Software-defined radio or SDR means you get the RF signal to digital as soon as possible and do everything else in software. If you want an introduction to SDR, Elektor now has [an inexpensive RF shield](https://www.elektor.com/elektor-sdr-hands-on-kit) for the Arduino. The Si5351-based board uses that oscillator IC to shift RF signals down to audio frequencies and then makes it available to the PC to do more processing.

The board is available alone or as part of a kit that includes a book. There’s also a series of Elektor articles about it. There’s also a review video from Elektor about the board in the video, below.

We peeked at the schematic and the shield is more for letting the Arduino control the radio by changing the oscillator frequency rather than performing the SDR functions. The IQ signals appear on the PC’s soundcard via a microphone or line-in jack, and don’t really route to the Arduino.

That’s a shame because some of the 32-bit Arduinos might be able to do some interesting things with the right hardware. Plus there are many capable CPU and FPGA boards that have Arduino shield-compatible layouts. That could have led to some interesting possibilities.

Then again, having a programmable signal source on the Arduino isn’t a bad thing and compared to the older version of the board, the new board offers easier breakout for the oscillator signals.

If you want to learn more about how SDR works, try starting with [spreadsheets](https://hackaday.com/2019/11/15/dsp-spreadsheet-iq-diagrams/). However, if you want to graduate to something more practical, try our series on [GNU Radio](https://hackaday.com/2015/11/12/your-first-gnu-radio-receiver-with-sdrplay/).

  
  
from Hackaday https://ift.tt/2uPLG6y  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)