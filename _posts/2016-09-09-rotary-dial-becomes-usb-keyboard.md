---
title: 'Rotary Dial Becomes USB Keyboard'
date: 2019-11-18T04:08:00+01:00
draft: false
---

\[Max\] had a rotary dial from an old telephone and — unsurprisingly — had nothing in particular to do with it. The simple answer? Use an Arduino Leonardo to turn it into a [USB keyboard device](https://www.instructables.com/id/DIY-Analog-Dialer-to-USB-Keyboard/).

Of course, the Leonardo can easily impersonate a USB keyboard, so that’s the easy part of the project. Interfacing to the dial requires an understanding of how the phone system works.

While today, TouchTone phones are most common, they were quite uncommon for many years. Early phones required you to have an operator connect your circuit to another person’s circuit. Unfortunately for the operators, the system was inherently unscalable and also cost prohibitive.

There were a variety of schemes tried and — supposedly — an undertaker who was angry that the operator was connecting his customers to her husband’s competing mortuary invented [the dial telephone](https://hackaday.com/2017/07/26/rotary-phones-and-the-birth-of-a-network/).

The details are pretty simple. A typical dial has two contacts. There’s a normally open contact that closes when you spin the dial to any position. It says closed until the spring returns the dial to the home position.

The other contact is normally closed and makes or breaks the phone line. Each time the dial rewinds past a position, the contact opens briefly. Of course, this is a mechanical system, so the software has to debounce the inputs, but that’s [easy enough](https://github.com/MaxRomagnoli/DIY-analog-dialer-to-USB-keyboard).

If you don’t have access to a dial, you could always [print one](https://hackaday.com/2019/03/13/3d-printed-rotary-dial-keypad-is-wonderfully-useless/). Sort of.

  
  
from Hackaday https://ift.tt/2KwuTdq  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)