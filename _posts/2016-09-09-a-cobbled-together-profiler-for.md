---
title: 'A cobbled-together profiler for
CircuitPython #CircuitPython @CircuitPython @xobs'
date: 2019-12-02T15:43:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-2.png)

[Sean Cross on xobs.io posts](https://xobs.io/cobbled-together-profiler/) about getting CircuitPython working on the Fomu FPGA board! But there were some issues:

> There’s an issue with the speed of Fomu’s SPI flash: It’s currently incredibly slow, and that makes for a poor experience. Worse still, the program runs so slowly that the tinyusb stack can’t keep up with the USB protocol, and the host gives up and resets the device.
> 
> An easy solution is to put frequently-used functions in RAM.  This is as simple as annotating them with `__attribute__((section(".ramtext")))`. However, the CircuitPython program is over 300 kilobytes, and Fomu only has 128 kilobytes of RAM. So we’ll have to pick and choose which functions to load into RAM.

Now it’s possible to debug the board, but how does that help with profiling?

[See Sean’s post](https://xobs.io/cobbled-together-profiler/) for the details.

![](https://cdn-blog.adafruit.com/uploads/2019/12/adafruit_blinka-300x203.png)

Read more about CircuitPython at [CircuitPython.org](https://www.circuitpython.org/).