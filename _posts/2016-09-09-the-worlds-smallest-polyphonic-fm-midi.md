---
title: 'The worlds smallest polyphonic FM MIDI synthesizer #MIDI #Music'
date: 2019-10-23T15:19:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-79.png)

[Mitxela.com features](https://mitxela.com/projects/flash_synth) an amazing project that shrinks a serious MIDI music synthesizer into a package the size of a standard MIDI DIN connector.

> The first thing we did was decide on what the synth should do:
> 
> *   Fully polyphonic, meaning 16 voices for the standard patches. More complex patches could also be added at a reduced polyphony, but the main algorithms are aiming for 16.
> *   Full support for pitch bend. This means respecting the full 14-bit value (something most keyboards don’t even send) and also working with the RPN pitchbend range adjustment messages. The synth is designed to work perfectly with the Tonal Plexus – Aaron’s microtonal MIDI keyboard, which sends a pitchbend range of 1 semitone, to get the most accurate detuning of notes.
> *   Powered by MIDI. Pulling its power parasitically from the plug. This is the real stickler.
> *   High quality sound output. This means stereo and full audio bandwidth: I aimed for the standard samplerate of 44.1kHz.
> *   Produces as many “bleeps and bloops” as possible. Some people criticised my original Smallest MIDI Synth for only producing a square wave with no envelopes or filters. This synth needs to produce a repertoire of sounds big enough to silence such comments.

And the microcontroller:

> For various reasons, I ended up switching to a smaller chip, the STM32L432KC. The physical size is a concern (the L476 was too big to fit into a midi connector) and also the power consumption of the L432 is marginally smaller. The code was quite easy to port, as the peripheral libraries are designed to make it so. Another reason for the switch was that the L476 was, to put it bluntly, overkill.

See the demo [video below](https://youtu.be/KTvVS8guBsY) and [details in the post](https://mitxela.com/projects/flash_synth).

Into MIDI? Let us know in the comments below.

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/31Ie8lg  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)