---
title: 'World’s Smallest MIDI Synth, Now Even Better'
date: 2019-10-28T09:06:00+01:00
draft: false
---

We’re pretty sure there’s no internationally recognized arbiter of records like “World’s smallest full-featured polyphonic stereo MIDI synthesizer that fits in a DIN shell”. If there isn’t, there sure should be, and we’re pretty sure [\[mitxela\]’s Flash-Synth would hold that particular record](https://mitxela.com/projects/flash_synth).

This is one of those lessons that some people just can’t leave a challenge alone. First \[mitxela\] built [a MIDI synthesizer into a DIN connector](https://hackaday.com/2016/01/08/the-smallest-midi-synthesizer/), then a couple of months later he made [a somewhat more streamlined version](https://hackaday.com/2016/03/30/the-attiny-midi-plug-synth/). While both were feats of engineering derring-do, neither was entirely satisfactory. With only square wave synthesis and a limit of eight voices, plus some unpleasant audio issues and a total lack of manufacturability, the next challenge was clear.

We won’t pretend to follow all the audio arcana, of which the video below and the build log have plenty, but the technical achievement is obvious enough. The Flash-Synth has an STM32, a tantalum SMD filter capacitor that dwarfs it, and a few support components on a flexible PCB that folds back on itself twice. This bit of circuit origami is connected to a 5-pin DIN plug and stuffed into the connector’s shell, which in turn mates to a custom-machined metal housing. A stereo audio jack lives at the other end of the assembly, and the whole synth is powered parasitically off the MIDI port.

The first half of the video below is mostly a demo that proves the synth sounds great and can do just about anything; skip to the 22-minute mark for the gory build details. Suffice it to say that \[mitxela\]’s past experience with [ludicrous scale soldering](https://hackaday.com/2018/06/26/no-caffeine-no-problem-a-hand-soldered-chip-scale-package/) served him well here.

\[Vikas\] dropped this one in the tip line for us. Thanks!

  
  
from Hackaday https://ift.tt/32UAUrB  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)