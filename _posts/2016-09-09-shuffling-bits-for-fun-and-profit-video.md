---
title: 'Shuffling bits for fun and profit – Video RAM @QuinnDunki'
date: 2019-10-11T15:34:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-44.png)

[Quinn Dunki](https://twitter.com/QuinnDunki) writes on [blondihacks](http://quinndunki.com/blondihacks/?p=680) about working with the video RAM of [Veronica](http://quinndunki.com/blondihacks/?p=680), a home-brew 6502 computer. The GPU magic that makes decent video for an 8-bit computer is a board called [F18A by Matthew Hagerty](http://codehackcreate.com/).

> I felt my VRAM block copier wasn’t working, despite my rigorous on-paper vetting of the code. However, this is one of those situations where it’s hard to say what’s actually broken. There are a lot of moving parts here- my block copier, all the various indirection tables in the F18A, the frame buffer, and so on.
> 
> Any one of those things being incorrect would cause the whole system to fail. As usual, this debugging task boils down to trying to find a way to isolate pieces of this system to verify independently.

![..](http://quinndunki.com/blondihacks/wp-content/uploads/2019/09/IMG_1872-600x450.jpg)

I played around with this for a while, and I suddenly realized what was wrong. I wish I could say it was a careful scientific process of eliminating variables, but sometimes debugging is just a flash of inspiration. I realized that my block copier was relying on the source data being aligned to a 256-byte boundary. This radically simplifies the code, so it’s a nice requirement to impose. My test font was not aligned to anything. In fact I even commented in the block copier that the source must be page-aligned (a “page” in 6502-speak is a 256-byte block) and then promptly forgot about my own constraint. It always pays to RTFM, especially when _you wrote_ TFM.

![](http://quinndunki.com/blondihacks/wp-content/uploads/2019/09/IMG_2011-600x450.jpg)

See [the full blog post](http://quinndunki.com/blondihacks/?p=5294) for all the details.