---
title: 'Full Duplex Radio Claimed Easier with Analog Module'
date: 2020-01-07T04:08:00+01:00
draft: false
---

There’s an old saying that we have one mouth and two ears so you can listen twice as much as you talk. However, talking and listening at the same time is fairly difficult and doing it with radio signals is especially hard. A company called [Kumu Networks has an analog module that can use self-interference cancellation](http://kumunetworks.com/) which allows transmitting and receiving on the same frequency with around 50 dB of the transmitted signal in the transceiver. You can see a video about Kumu’s claims its technology below.

You may think that cell phones and ham radio repeaters transmit and receive at the same time, which of course they do, but usually on different frequencies to avoid direct interference. A diplexer is a device that sorts out the two frequencies while a duplexer sorts them out by the direction of the signal, but they are tricky to use. A duplexer can operate on a single frequency in applications such as radar, and even then it is still very difficult to prevent leakage from the transmitter from overloading and desensitizing the receiver.

While 50 dB might not sound like much, it is a factor of 100,000 which should open up new opportunities for radio transmitters and receivers to coexist even on the same frequency. The device is analog, so it uses circuitry to invert the transmitted signal and reincorporate it at the receiver.

[IEEE Spectrum](https://spectrum.ieee.org/telecom/wireless/kumu-networks-launches-an-analog-radio-module-that-cancels-its-own-interference) recently had a post claiming the company is releasing the K6 module that can be “easily installed in most any wireless system.” RF can seem like black magic, but we can envision how this should work in theory. You’d need to adjust the phase of the inversion network to match the phase delay between where you pick up the signal (presumably before power amplification) and where you mix the canceling signal with the receiver.

Sounds good, but then again, noise-canceling headphones sound straightforward too and we all know that even an expensive pair can leave something to be desired.

  
  
from Hackaday https://ift.tt/39IGMYM  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)