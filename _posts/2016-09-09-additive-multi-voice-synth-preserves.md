---
title: 'Additive, Multi-Voice Synth Preserves Sounds, Too'
date: 2020-01-13T10:18:00+01:00
draft: false
---

For his final project in \[Bruce Land\]’s infamous microcontroller design class, [\[Mark\] set out to make a decently-sized synth that sounds good](http://people.ece.cornell.edu/land/courses/ece4760/FinalProjects/f2019/mwa37/mwa37/mwa37/index.html). We think you’ll agree that he succeeded in spades. Don’t let those tiny buttons fool you, because it doesn’t sound like a toy.

Why does it sound so good? One of the reasons is that the instrument samples are made using additive synthesis, which essentially stacks harmonic overtones on top the fundamental frequency of each note. This allows synthesizers to better mimic the timbre of natural, acoustic sounds. For each note \[Mark\] plays, you’re hearing a blend of four frequencies constructed from lookup tables. These frequencies are shaped by an envelope function that improves the sound even further.

Between the sound and the features, this is quite an impressive synth. It can play polyphonically in piano, organ, or plucked string mode through a range of octaves. A PIC32 runs the synthesizer itself, and a pair of helper PIC32s can be used to record songs to be played over. So \[Mark\] could record point and counterpoint separately and play them back together, or use the helper PICs to fine-tune his three-part harmony. We’ve got this thing plugged in and waiting for you after the break.

If PICs aren’t what you normally choose, [here’s an FPGA synth](https://hackaday.com/2019/07/24/xfm-a-32-voice-polyphonic-fm-synthesizer-on-an-fpga/).

  
  
from Hackaday https://ift.tt/385jMBt  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)