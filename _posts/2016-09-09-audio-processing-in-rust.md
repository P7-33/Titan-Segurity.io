---
title: 'Audio Processing in Rust'
date: 2019-11-15T04:06:00+01:00
draft: false
---

\[Michael\] volunteers with emergency services, and sometimes has to monitor radio traffic. Sometimes there’s a lot to review, and to make it easier he wrote [a noise gate](http://adventures.michaelfbryan.com/posts/audio-processing-for-dummies/) — think of it as a squelch — to break apart recorded audio into parts. Rust has been gaining popularity for writing low level software, and that’s the language he uses. However, you’ll see even if you don’t know Rust, it is pretty easy to figure out.

For test data, \[Michael\] took some publicly-available recordings of air traffic control. Using some ready-made audio processing functions and a simple state machine makes the code easy to write.

The code allows you to set a threshold the signal has to exceed to start a new grouping. It also lets you set a decay time. If the signal goes below the threshold for that amount of time, it will cause the gate to close and close the current recording.

Typical noise gates also have an attack time to reject larger spikes from getting through the gate, however, this code appears to react immediately to a signal above the threshold.

The main function reads the input file and applies the algorithm. When the state machine triggers, it copies audio data to the sink which writes it out. It is that simple.

We see Rush more and more in [small systems](https://hackaday.com/2019/10/21/a-diy-computer-programmed-in-pure-rust/). If you want to read more about that trend, we’ve talked about it at length.

  
  
from Hackaday https://ift.tt/352ffyo  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)