---
title: 'Guitar Effect Built from an Old Record Player'
date: 2019-12-09T13:32:00+01:00
draft: false
---

With little more than a gutted record player, a light bulb, and the legendary 555 timer IC, \[Jacob Ellzey\] has constructed [this very slick optical tremolo effect for his guitar](https://imgur.com/a/7iT9X5x). By modulating the volume of the input signal, the device creates the wavering effect demonstrated in the video after the break.

[![](https://hackaday.com/wp-content/uploads/2019/12/tremolo_detail.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/12/tremolo_detail.jpg)The key is a vinyl record with large tabs cut out of it. As the record spins, these voids alternately block and unblock a small incandescent bulb. A common GL5537 photoresistor, mounted on the arm that originally held the player’s needle, picks up the varying light levels and passes that on to the electronics underneath the deck. An important note here is that different spacing and sizing of the cutouts will change the sound produced by the effect. \[Jacob\] has already produced a few different designs and plans on experimenting with more now that the electronics are completed.

Under the hood there’s a voltage divider and low gain amplifier connected to the photoresistor, and also a 555 timer circuit that’s driving the incandescent bulb. Once he was done fiddling with them, the circuit was moved to a neat little protoboard. A pair of potentiometers mounted through the side of the record player allow for adjusting the depth of the effect itself, as well as the output volume. Naturally, there’s also an external foot pedal that allows keying the effect on and off without taking your hands from the guitar.

As is usually the case, everything was going well on this project until the final moments, when \[Jacob\] found that the circuit and bulb were both browning out when powered from the same transformer. As a quick fix, he gutted a Keurig and used its transformer to drive the light bulb by itself. With independent power supplies, he was ready to rock.

Of course this isn’t the first time we’ve seen [a piece of consumer electronics modified into a guitar effect](https://hackaday.com/2019/01/09/the-t-pain-toy-is-now-a-guitar-effect/), but if you’re looking for something a bit more built for purpose, [there’s plenty of high-tech options to keep you busy](https://hackaday.com/2018/05/08/stomping-microcontrollers-arduino-mega-guitar-effects-pedal/).

  
  
from Hackaday https://ift.tt/2RyDukc  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)