---
title: 'A business card which runs Linux #Linux #MicroPython'
date: 2019-12-27T16:59:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-89.png)

[George Hilliard](https://www.thirtythreeforty.net/posts/2019/12/my-business-card-runs-linux/) is an embedded systems engineer who spends a lot of time looking for things for use in future designs, or things that tickle a fancy:

> One of those things is cheap Linux-capable computers, the cheaper the better. So I started diving into the very deep rabbit hole of obscure processors.
> 
> I thought to myself, “These processors are nearly cheap enough to give away.” After a while I hit upon the idea of making a barebones Linux board in a business card form factor.
> 
> As soon as I had the idea I thought it would be pretty cool to do. I have [seen](https://hackaday.com/2017/10/04/literally-flashy-business-cards/) electronic [business](https://hackaday.com/2014/06/17/designing-the-second-version-of-my-business-card/) cards [before](https://hackaday.com/2018/05/11/stylish-business-card-with-a-stylophone-built-in/), with various fun features including emulating USB flash drives, blinkenlights, or even wireless transceivers. I have never seen one running Linux, however. So I built one.

You can run all these from the emulated serial console after you log in (as `root`, the only user):

*   **`rogue`**: the classic Unix dungeon crawler.
*   **`2048`**: a simple console mode 2048 game.
*   **`fortune`**: various pithy sayings. I decided not to include the entire database of quotes here to save space for other functionality.
*   **[`micropython`](https://micropython.org/)**: a very small Python interpreter.

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-90.png)

It has a USB port in the corner. If you plug it into a computer, it boots in about 6 seconds and shows up over USB as a flash drive and a virtual serial port that you can use to log into the card’s shell. The flash drive has a README file, a copy of George’s résumé and photography. The shell has several games and Unix classics such as fortune and rogue, a small 2048, and a small MicroPython interpreter.

> **Bill of Materials & Cost**
> 
> I kept costs low. It’s cheap enough that I don’t feel bad giving it away, as designed! I’m not going to give one to absolutely everyone because it does take time to assemble each card, and assembly cost is not factored in here (my time is “free”).
> 
> Component
> 
> Price
> 
> F1C100s
> 
> $1.42
> 
> PCB
> 
> $0.80
> 
> 8MB flash
> 
> $0.17
> 
> All other components
> 
> $0.49
> 
> **Total**
> 
> **$2.88**

See the entire project on the [blog post here](https://www.thirtythreeforty.net/posts/2019/12/my-business-card-runs-linux/).