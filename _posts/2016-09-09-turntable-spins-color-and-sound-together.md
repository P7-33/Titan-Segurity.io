---
title: 'Turntable Spins Color And Sound Together'
date: 2019-10-27T12:11:00+01:00
draft: false
---

If you can’t grow your own synesthesia, buying electronics to do it for you is fine. Such is the case with [the CHROMATIC](https://www.youtube.com/watch?v=ljxQYGn5PMU&feature=youtu.be) by \[Xavier Gazon\], an artist who turns all kinds of electronics into circuit-bent musical art pieces. His project turns an old Philips Music 5120 turntable into a colorful MIDI sequencer, inspired by older 20th century instruments such as the Optophonic Piano and the Luminaphone.

The CHROMATIC uses colored pucks placed on a converted turntable to perform a looping sequence of chords in a given musical scale, generating MIDI data as output. Where its inspirations used primitive optics as their medium, this project employs a Teensy microcontroller and two modern optical sensors to do the work. One of these is a simple infrared sensor which tracks a white spot on the edge of the turntable, generating a MIDI clock signal to keep everything quantized and in sync. The other is a color sensor mounted on the tone arm, which can tell what color it sees and the height of the arm from the turntable.

While the instrument is still in beta testing phase details on how notes are generated aren’t yet given, though the general idea is that they are dictated by the color the tone arm sees and its position above the platter. Moving the tone arm changes which pucks it tracks, and the speed of the turntable can also be adjusted, changing how the melody sounds.​

The CHROMATIC is a very interesting project, but it’s not [the first optical-based turntable hack we’ve seen here](https://hackaday.com/2014/03/12/hacked-turntable-plays-a-trees-rings-instead-of-records/). We’ve also seen [a much weirder use for a color sensor](https://hackaday.com/2018/07/08/rgb-sensors-new-job-cryptocurrency-trade-advisor/), too. Check out the video of this one in action after the break.

  
  
from Hackaday https://ift.tt/2BL9Qiq  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)