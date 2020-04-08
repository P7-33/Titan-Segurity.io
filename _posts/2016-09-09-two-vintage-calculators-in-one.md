---
title: 'Two Vintage Calculators In One'
date: 2019-11-14T07:07:00+01:00
draft: false
---

The FPGA revolution that occurred within the past few decades was a boon to many people interested in “antique” electronics. The devices “wire together” logic elements as needed rather than emulating chips completely in a software layer, which makes them uniquely suited for replicating chips that are rare, no longer in production, damaged, or otherwise lost. They also make it easy to experiment with hardware, like [this project which combines two antique calculators into one single unit](https://hackaday.io/project/167457-tms0800-fpga-implementation-in-vhdl).

The two calculators used in this combination device are the TI Datamath and the Sinclair Scientific, both released in the early 1970s, the [former of which has been extensively documented and reverse engineered on at least one occasion](https://hackaday.com/2013/08/30/ken-shirriff-completely-reverse-engineers-the-1974-sinclair-scientific-calculator/). The reproduction from \[zpekic\] has a toggle that allows the user to switch between the two “modes”. This showcases the power of microprogramming and microcode, and of the FPGA platform itself. Although both modes are functional, there are still a few bugs resulting from how different the two pieces of hardware were, which is really more of an interesting facet of this project than anything.

The build is a great showcase of FPGA technology, not to mention a great read-through for understanding these two calculators and their fundamental differences in data entry and manipulation, clock cycles, memory, and everything in between. It’s worth checking out, even if you don’t plan on using a [decades-old calculator in your day-to-day life](https://xkcd.com/768/).

  
  
from Hackaday https://ift.tt/351bol7  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)