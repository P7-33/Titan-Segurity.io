---
title: 'This PIC Is A Squarewave Generator'
date: 2020-02-08T10:32:00+01:00
draft: false
---

When we use a microcontroller to flip a few GPIOs or talk SPI to a peripheral chip, we are often overlooking that it will usually contain an array of built-in peripherals that were once the preserve of extra hardware. Analogue ports, timers, UARTs, and clock generators, to name just a few. \[Giovanni Bernardo\] has been experimenting with one of these, the internal frequency synthesiser on many PIC microcontrollers, and he’s  produced a handy square wave generator [for which he’s placed code on GitHub](https://github.com/Cyb3rn0id/Microchip_Curiosity_Nano_Examples/tree/master/16F15376_Curiosity_Nano_Square_Wave_Generator.X) and produced [a write-up](https://www.settorezero.com/wordpress/un-generatore-di-onda-quadra-da-1hz-a-16mhz-con-un-microcontrollore-pic/) (Italian language, [Google translate link](https://translate.google.com/translate?sl=auto&tl=en&u=https%3A%2F%2Fwww.settorezero.com%2Fwordpress%2Fun-generatore-di-onda-quadra-da-1hz-a-16mhz-con-un-microcontrollore-pic%2F)).

The board used is a PIC16F375 Curiosity Nano, and code takes input from a rotary encoder to set the frequency, with a button to select different step sizes and an alphanumeric LCD display to show the current settings. Frequencies from 1 Hz to 15 MHz are possible, with a clever switch between two of the PICs internal clocks to be used as the reference frequency. Stability depends upon whatever source the PIC uses for its own clock, and while we suspect that will be enough for most users it’s not inconceivable that the PIC could be clocked from a GPS-disciplined source or similar were there a requirement for it.

There are plenty of ways to generate square waves from a microcontroller. [Most projects use waveform generator](https://hackaday.com/2018/09/03/arduino-powered-portable-function-generator/) ICs.

  
  
from Hackaday https://ift.tt/3blQEbE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)