---
title: 'These Bit Twiddling Tricks Will Make Your Coworkers Hate You'
date: 2020-01-17T04:17:00+01:00
draft: false
---

In the embedded world, twiddling a few bits is expected behavior. Firmware is far enough down the stack that the author may care about the number of bits and bytes used, or needs to work with registers directly to make the machine dance. Usually these operations are confined to the typical shifting and masking but sometimes a problem calls for more exotic solutions. If you need to descend down these dark depths you invariably come across the classic [Bit Twiddling Hacks](https://graphics.stanford.edu/~seander/bithacks.html) collected by \[Sean Eron Anderson\]. Here be dragons.

![](https://hackaday.com/wp-content/uploads/2020/01/Rotate_left_through_carry-Hackaday.png?w=400)

Discussions of bit math are great opportunities to revisit [Wikipedia’s superb illustrations](https://en.wikipedia.org/wiki/Bitwise_operation)

Bit Twiddling Hacks is exactly as described; a page full of snippets and suggestions for how to perform all manner of bit math in convenient or efficient ways. To our surprise upon reading the disclaimer at the top of the page, \[Sean\] observes that so many people have used the contents of the page that it’s effectively all been thoroughly tested. Considering how esoteric some of the snippets are we’d love to know how the darkest corners found use.

The page contains a variety of nifty tricks. Interview content like [counting set bits](https://graphics.stanford.edu/~seander/bithacks.html#CountBitsSetNaive) makes an early appearance.  There’s more esoteric content like [this trick for interleaving](https://graphics.stanford.edu/~seander/bithacks.html#InterleaveTableLookup) the bits in two u16’s into a single u32, or [rounding up to the next power of two](https://graphics.stanford.edu/~seander/bithacks.html#RoundUpPowerOf2Float) by casting floats. This author has only been forced to turn to Bit Twiddling Hacks on one occasion: to [sign extend](https://graphics.stanford.edu/~seander/bithacks.html#FixedSignExtend) the output from an unfortunately designed sensor with unusual length registers.

Next time you need to perform an operation with bitmatch, check out Bit Twiddling Hacks. Have you ever needed it in production? How did you use it? We’d love to hear about it in the comments.

  
  
from Hackaday https://ift.tt/2RozOzJ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)