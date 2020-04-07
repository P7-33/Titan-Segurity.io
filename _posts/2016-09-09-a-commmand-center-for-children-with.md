---
title: 'A Commmand Center for Children with Sensory Needs'
date: 2020-01-25T10:08:00+01:00
draft: false
---

Toys for children are meant to be fun and interactive, but they’re even better if they’re educational as well. For \[carrola1\], a parent of a 4-year-old suffering from from medical disabilities, sensory needs, and autism, a more personalized approach seemed best. The electrical engineer built a [wall-mounted command center](https://hackaday.io/project/169293-command-center) with plenty of switches, buttons, and knobs to trigger to keep any child happy.

Apart from basic inputs, the device also has a color sensor – the command center can ask the child for an object of a particular color and congratulate them with a song when they’ve successfully acquired one.

![](https://hackaday.com/wp-content/uploads/2020/01/command-center-behind.jpeg?w=400)

The software for the audio and light controls was [written in C](https://github.com/carrola1/CommandCenter) for a STM32L0 series MCU, with CMSIS as the hardware abstraction layer and STM32CubeIDE as the IDE. The design uses SPI and I2C for serial communication and I2S for communicating between the digital audio devices. Physical inputs include toggle switches, rotary switches, and key switches to provide variety, with all physical hardware connected to the MCU on a custom PCB.

The audio output, sourced from a library of wav files, seems like the most challenging part of the build: the amps needed to be changed from left channel mono configuration to stereo, the output had to be LC filtered, and the code for had to be optimized for size to allow the audio files to play.

You can check out a video of the command center in action on the [Reddit post](https://www.reddit.com/r/somethingimade/comments/ejx6ho/built_this_wallmounted_command_center_for_my_son/).

  
  
from Hackaday https://ift.tt/2RMHHPQ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)