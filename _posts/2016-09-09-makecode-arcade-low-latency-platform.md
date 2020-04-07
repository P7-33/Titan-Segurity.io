---
title: 'MakeCode Arcade – a low latency platform? #MakeCode #Gaming @MSMakeCode'
date: 2020-01-01T19:11:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/makecode.jpg)

[kjw](https://forum.makecode.com/u/kjw) on the [Microsoft MakeCode blog](https://forum.makecode.com/t/makecode-arcade-a-low-latency-platform/966) posts about measuring the latency on MakeCode Arcade hardware.

> I stumbled across [Dan Luu’s Computer Latency 1](https://danluu.com/input-lag/) page where he’s investigated and measured the response times from keyboard to screen of a wide range of devices. I’m sure he’s surprised some with the 1980s computer from some obscure manufacturer ruling the roost.
> 
> I thought I’d have a look at the Arcade hardware. Here’s the [Adafruit PyGamer](https://www.adafruit.com/product/4242) running some simple code which puts a sprite on screen when `A` is pressed (compiled on `0.15.5`):
> 
> [![button-to-screen-latency-example-1](https://aws1.discourse-cdn.com/standard14/uploads/makecode/original/1X/86de8fccf9538d73a061a50ab331ef5eee0245f7.gif)](https://aws1.discourse-cdn.com/standard14/uploads/makecode/original/1X/86de8fccf9538d73a061a50ab331ef5eee0245f7.gif)
> 
> Frame 13 is where the highlighter pen hits the button, frame 25 is where A is first visible on screen, frame 34 is roughly where A reaches maximum brightness. That’s from a very cheap 240fps camera which in the mp4 says it’s actually 233.79fps (latter value confirmed by the Android tablet’s timer).
> 
> I had a look at a few presses and it looks strangely consistent at 12 frames for the A to first appear on screen which makes the delay 51ms (12 \* (1/233.79) \* 1000). Is that a likely number given the hardware (including any debouncing) and game loop? I was expecting it to vary a bit more varied based on when the button was pressed within the 20ms duration game loop?
> 
> It’s interesting to see the response time of the humble Adafruit [1.8″ TFT LCD screen](https://www.adafruit.com/product/618) too. From watching the reset screen it looks like they update from the left so it’s possible that sprite position is important for this latency measurement and that middle of screen gives a useful mean value.
> 
> The tiny program is available on [https://makecode.com/\_8VY3WT1Dychj](https://makecode.com/_8VY3WT1Dychj)

As a response, [mmoskal](https://forum.makecode.com/u/mmoskal) posts:

> I believe we scan buttons every 4ms, it may take 8 or even 12 to register. Game loop update is around 25ms. So it all sounds about right. Not sure why the timing would be so consistent.

[See the post here](https://forum.makecode.com/t/makecode-arcade-a-low-latency-platform/966).