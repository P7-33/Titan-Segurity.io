---
title: 'All the Games in One Cartridge'
date: 2020-01-27T10:44:00+01:00
draft: false
---

The original Game Boy was a smash success for Nintendo and has an amazing collection of games. You might relive some childhood nostalgia by booting up a Game Boy emulator, but to really get the full experience you’ll need the battery-draining green-tinted original hardware. Thanks to modern technology you can also load all of the games at one time on the original hardware with this [STM32 cartridge that fits right in](https://emeryth.net/stm32-game-boy-cartridge/).

The device can load any Game Boy game (and homebrews) and ROMs can be sent to the cartridge via USB. There were are a lot of hurdles to getting this working properly, the largest of which is power management. A normal cartridge has a battery backup for save data, but using a small coin cell to run an STM32 would kill the battery quickly. To get around that, the cartridge writes the states to nonvolatile memory and then shuts itself off, although this has the side effect of crashing the Game Boy.

The creator of this project, \[Emeryth\], noted that we featured [a similar project from \[Dhole\]](https://hackaday.com/2014/12/30/game-boy-cartridge-emulator-uses-stm32/) a few years ago, also involving an STM32. \[Emeryth\] decided that it would be fun to build his own project anyway, and it’s certainly an interesting take on GameBoy hacking. He also has the files for this project available on [his Git Hub page](https://github.com/Emeryth/stm32gbcart).

  
  
from Hackaday https://ift.tt/2RsF9aE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)