---
title: 'Analog Meter Clock Uses Parts From A Simpler Time'
date: 2019-12-29T13:26:00+01:00
draft: false
---

Clocks with hands that turn are all well and good for the common folk, but hacker types prefer something different. \[Sjm4306\] is one such person, [and developed this analog dial clock with parts we’d almost consider retro by modern standards.](https://hackaday.io/project/168974-analog-meter-clock)

The microcontroller at the heart of the build is a PIC16F886. An 8-bit micro from the Microchip brand, it features no Arduino bootloader or USB interface, being flashed via a dedicated programmer. This is combined with a DS1302 real-time clock to keep accurate time, and a MCP4922 DAC which is responsible for generating the output to drive the dials. The dials themselves are sourced from eBay, being simple voltmeters. They’re given a new backing to display hours and minutes instead of volts, and backlit with LEDs for style.

In this day and age, we’re more used to seeing high-end micros used with integrated DACs and USB programming, but it’s nice to see the parts of yesteryear being used, too. [It’s not the first clock we’ve seen from \[sjm4306\], either](https://hackaday.com/2019/09/26/mini-vfd-clock-floats-the-display-above-it-all/). Video after the break.

  
  
from Hackaday https://ift.tt/2F8HEYt  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)