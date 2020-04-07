---
title: 'A Mini SDR Receiver Using An Audio DSP'
date: 2020-02-02T07:23:00+01:00
draft: false
---

Software defined radio or SDR is the most exciting frontier in the field of radio, transferring as it does all signal functions from the analogue to the digital domain. Radios using SDR techniques can be surprisingly straightforward and easy to understand, and \[Ray Ring\]’s little SDR receiver [manages to combine this with the novel use of an audio DSP](https://circuitsalad.com/2020/01/06/compact-si5351-based-sdr/) rather than a computer to perform its SDR functions.

The front end is a conventional enough direct conversion design with an Si5531 clock generator providing I and Q phase-shifted local oscillator signals to a [TS3A5017](http://www.ti.com/product/TS3A5017) analogue switch used as a mixer. An unexpected presence is an LTC6252 op-amp as an RF amplifier, but the special part comes after the I and Q baseband signals have been filtered. The SDR part of this receiver is an audio DSP, but it’s one that might not be an immediate choice. The [Spin Semiconductor FV-1](http://www.spinsemi.com/products.html) is a dedicated digital reverb chip for musical effects boxes, but it comes with the feature that its internal DSP core can access custom code from an external ROM. \[Ray\] has written his own code for demodulation of AM, USB, and LSB signals rather than musical effects, and used the device’s left and right audio channels to process I and Q quadrature signals. The use of a single purpose chip to do something its designers never intended gives it the essence of a good hack, and we’re mightily impressed at his spotting the potential for an SDR in a musical effect. Hear it in action in the video below the break.

Meanwhile if the operation of a receiver such as this one is a mystery to you, [we published a handy primer back in 2017](https://hackaday.com/2017/05/16/if-the-i-and-q-of-software-defined-radio-are-your-nemesis-read-on/).

Thanks \[Ziew\] for the tip.

  
  
from Hackaday https://ift.tt/36VvlKU  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)