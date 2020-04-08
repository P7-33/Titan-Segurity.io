---
title: 'Perfmatters v1.4.2 – Lightweight Performance Plugin'
date: 2019-10-02T06:04:00+01:00
draft: false
---

Most people have at least seen those cheap component testers you can buy on the Chinese websites for $10 or so. If you haven’t seen them before, they usually have some kind of multi pin socket. You put a component in the socket and it will identify — with a push of a button — what the part is, which pin is which, and the value of the part. For example, you can insert a resistor, a capacitor, an inductor, a diode, or a transistor and get a readout of which pin is which. It seems like magic, but \[Andreas Spiess\] did the research on how it all works and summed up his findings in a [recent video](https://www.youtube.com/watch?v=4Xsg8lpP75s).

\[Andreas\] even quotes our [earlier post on the topic](https://hackaday.com/2015/04/24/review-transistor-tester/) and, as we did, dug into the original developers of the device which has been cloned over and over by Chinese sellers. Although there have been some divergence with all the different versions, the basic idea is the same. An AVR CPU uses some analog and digital trickery to make a lot of different measurements.

There are quite a few coding tricks you can learn by examining how the testers can do the job with very few external components. It also helps to go to [the original project](https://www.mikrocontroller.net/articles/AVR_Transistortester#Introduction_.28English.29). Just be careful. Your $7 tester from eBay might not be able to work with the original code — some makers do simple modifications for different displays or other reasons.

We’ve seen these hacked to do [other things](https://hackaday.com/2017/02/22/t-rex-runner-runs-on-transistor-tester/), although maybe nothing as useful as the original. [More fun](https://hackaday.com/2019/05/03/play-tetris-on-a-transistor-tester-because-why-not/) perhaps, but not as useful.

  
  
from Hackaday https://ift.tt/2orEkm9  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)