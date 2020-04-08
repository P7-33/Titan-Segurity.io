---
title: 'Darwin Approves: Berkeley Evolves Analog Design'
date: 2019-09-28T03:04:00+01:00
draft: false
---

Digital design is hard. But in the right environment, digital circuits are more forgiving than analog. That 3.3V signal coming out of the chip has to drop a lot along the way to not be a logic level at the destination. If you are trying to push the boundary then digital design has much of analog design, but mostly you get a bit of a pass on many things that plague analog designers. Berkeley’s AI research group has been experimenting with using [deep learning to evolve analog IC design](https://bair.berkeley.edu/blog/2019/09/26/circuits/).

Analog ICs are plagued with noise sources and often don’t have the margins that digital circuit designers enjoy. According to the post by \[Kourosh Hakhamaneshi\], designers often build a few blocks and attempt to lay them out in a way that should work and meet other requirements. Then they employ simulation, make changes as required, and simulate again. Accurate simulations can be very time intensive. You can read the [actual paper](https://arxiv.org/abs/1907.10515), too, should you want to dig into the details.

The problem is really one of optimization. An amplifier for example might need a minimum gain and bandwidth. In addition, there is always the need to take up as little space on the die as possible — just as you don’t want to waste space on a PCB. Since simulation is so expensive, the work appears to try to train a neural network to determine if one design is better than another based on the desired design criteria.

The result isn’t quantitative, but knowing which of two designs is better is very useful for selecting candidates to test in simulation. Interestingly, according to the post, it sounds as if the learning model trains itself on random permutations of the exact circuit you want to design — which makes sense. This training corpus requires simulation, of course, so that eats into the potential savings.

This technique could have applications with other optimization problems, too. We generally like [simulation](https://hackaday.com/2016/02/29/spice-power/), even if ours don’t usually take that long. Our favorite one is pretty simple and [runs in a browser](https://hackaday.com/2015/07/20/a-breadboard-in-a-browser/).

  
  
from Hackaday https://ift.tt/2nqqUGx  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)