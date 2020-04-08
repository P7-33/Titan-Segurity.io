---
title: 'Easy Halloween Sound Hack, Part One'
date: 2019-10-29T06:19:00+01:00
draft: false
---

My aunt and uncle set up a "Haunted Forest" every year, where they take area kids through a section of their woods with groomed trails and various scary things. This year I'm helping "up the ante" with sound, lighting, and robotics (pneumatic and/or otherwise depending on time). I'll cover various means of tech-ing up the fear.

The first hack is pretty straight-forward, the only possible glitch being sound file format conversion (the board I'm using doesn't support MP3) to OGG. WAV is supported (and desirable under some conditions) but the storage space is somewhat limited, so I'm using mostly OGG except for when sounds are being looped or played sequentially. The compressed format introduces a small, but perceptible, delay under those conditions.

My test rig was designed to be cheap and mutable, so I used a mono amplifier (

[Adafruit ID 2130](https://www.adafruit.com/products/2130)

) and the mini sound trigger board (

[Adafruit ID 2342, 2M flash storage](https://www.adafruit.com/products/2342)

), about $19 altogether. There's an integrated version (

[2M flash, stereo amp](https://www.adafruit.com/products/2210)

) that I might consider, it's about $25. I'm anticipating we'll use anywhere from 2-6 of these across the forest, with a variety of triggering mechanisms.

[![](http://3.bp.blogspot.com/-lilDqAqyaBY/VUJAMwL00HI/AAAAAAAALNA/CEB_jFJiyJ4/s1600/sfx01.jpg)](http://3.bp.blogspot.com/-lilDqAqyaBY/VUJAMwL00HI/AAAAAAAALNA/CEB_jFJiyJ4/s1600/sfx01.jpg)

Breadboarded prototype; cheap version

The Adafruit docs detail how the device works. Nutshell: sounds are triggered via either the board's GPIO pins (pull to ground) or serial port. Only one of these mechanisms can be used at a time. (I have another project using serial control; this will be documented later.)

For the haunted forest (and my own display) we'll need several triggering options, including PIR, simple switches, and possibly audio. Trigger pins will be externally exposed via a simple jack, probably 1/8" audio. Speakers will be external with an option to stick it onto the project box.

One obvious usage is to hang the box from a tree with the PIR firing down, or towards the path. For extra giggles you could either point it so it fires after the victims have passed so the sound comes from behind them. With only minor effort, and separated stereo speakers, you could set up a sequential trigger that first comes from behind, then in front of, the victims, etc.

For my own Halloween display I'll be using two setups, one with a PIR for people approaching the house, and another at the house for when they dip into the candy bowl. With a 4 Ohm speaker the sound is more than enough to raise a hackle or two, although if you need to project over a distance you'll want something more powerful than the 2.5W amps shown here or on the integrated device.

Upcoming posts will detail the lighting (fire and lightning effects, other simple things), any robotics, and the integration of all these systems into a unified pee-inducing system.

  
  
from Hacker News https://ift.tt/36e5UEW