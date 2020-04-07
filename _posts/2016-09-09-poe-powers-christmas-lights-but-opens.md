---
title: 'PoE Powers Christmas Lights, But Opens Up So Much More'
date: 2020-01-01T07:47:00+01:00
draft: false
---

Addressable LEDs are a staple of homemade Christmas decorations in our community, as is microprocessor control of those LEDs. So at first sight \[Glen Akins\]’ [LED decorated Christmas tree](https://bikerglen.com/blog/ethernet-powered-pixels/) looks pretty enough, but isn’t particularly unusual. But after reading his write-up you’ll discover there’s far more to the project than meets the eye, and learn a lot about the technologies behind it that has relevance far beyond a festive light show.

The decoration is powered exclusively from power-over-Ethernet, with a PIC microcontroller translating [Art-Net](https://art-net.org.uk/) DMX-over-Ethernet packets into commands for the LED string. The control board is designed from the ground up and includes all the PoE circuitry, and the write-up  gives a very thorough introduction to this power source that takes the reader way beyond regarding PoE as simply another off-the-shelf black box. Along the way we see all his code, as well as learn a few interesting tidbits such as the use of a pre-programmed EEPROM containing a unique MAC address.

So if your house has CAT5 wiring and you want an extra dimension to your festive splendour, you’ve officially got a whole year to build your own version. He’s featured here before, with [his buzzer to break the Caps Lock habit](https://hackaday.com/2019/11/13/break-the-caps-lock-habit-with-this-annoying-buzzer/).

  
  
from Hackaday https://ift.tt/2ZIxFTb  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)