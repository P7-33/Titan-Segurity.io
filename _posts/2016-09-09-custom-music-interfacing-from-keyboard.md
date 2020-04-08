---
title: 'Custom music interfacing from a keyboard to EuroRack via
CircuitPython #CircuitPython #Music @theavalkyrie'
date: 2019-10-09T14:39:00+01:00
draft: false
---

> She's alive!
> 
> The blue cable is sending control voltage that corresponds to the key I'm pressing (1v/octave).
> 
> The green cable is sending gate. It's 5v when a key is pressed and 0v when no key is pressed.
> 
> These two together control the synth that they're plugged into. [pic.twitter.com/g7YLjtMoNS](https://t.co/g7YLjtMoNS)
> 
> — Peaches & Scream (@theavalkyrie) [October 6, 2019](https://twitter.com/theavalkyrie/status/1180876283971944448?ref_src=twsrc%5Etfw)
> 
> [Thea Flowers](https://twitter.com/theavalkyrie) writes [on Twitter](https://twitter.com/theavalkyrie/status/1180876283971944448) about her custom [CircuitPython](https://www.circuitpython.org/) programmable board working as a USB MIDI to CV/Gate module.
> 
> > Which means that it’s \*reprogrammable\* on the fly. There are 6 output jacks on this board. 2 are continuous 0-10v waveforms driven by a 16-bit DAC. 4 are digital 0 or 5v signals driven by a line buffer. You can map those to all sorts of functions.
> > 
> > In my videos I mapped one of the DAC changes to note value. But, you can map it (or the other DAC channel) to output a (low frequency) sine, triangle, square, etc. wave. Or you can make it output a voltage that maps to the modulation wheel from the keyboard.
> > 
> > Or like… A thousand other things. The digital jacks can themselves output square waves, but you can also hook them up to all sorts of events. Like timers. Or when you press a certain note. Or when you turn a certain knob.
> 
> She says her goal with the software on this is to write a library that makes the main code.py easy to edit while making music. So if you need to swap out a jack’s function, it doesn’t break you from the experience of making music. So it’ll eventually be this powerful brain for my modular synthesizer.
> 
> You can read the entire thread and see it in action [on Twitter here](https://twitter.com/theavalkyrie/status/1180876283971944448).
> 
>  ![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-31.png)