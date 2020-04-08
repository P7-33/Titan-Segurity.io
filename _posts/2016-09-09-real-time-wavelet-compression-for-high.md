---
title: 'Real-Time Wavelet Compression for High Speed Video #Video'
date: 2019-10-29T14:28:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-100.png)

Shane Colton explores using wavelet compression for video compression.

> The next stop on the [Freight Train of Pixels](http://scolton.blogspot.com/2019/06/freight-train-of-pixels.html) is the wavelet compression engine. Previously, I built up the [CMV12000 input module](http://scolton.blogspot.com/2019/09/cmv12000-full-speed-384gbs-read-in-on.html), which turned out to be easier than I thought. The output of that module is a set of 64 10-bit pixels and one 10-bit control signal that update on a 60MHz pixel clock (px\_clk). This is too much data to write directly to an NVMe SSD, so I want to compress it by about 5:1 in real-time on the [XCZU4](https://shop.trenz-electronic.de/en/TE0803-02-04CG-1EA-MPSoC-Module-with-Xilinx-Zynq-UltraScale-ZU4CG-1E-2-GByte-DDR4-5.2-x-7.6-cm?c=452) Zynq Ultrascale+ SoC.
> 
> Wavelet compression seems like the right tool for the job, prioritizing speed and quality over compression ratio. It needs to run on the SoC’s programmable logic (PL), where there’s enough parallel computation and memory bandwidth for the task. This post will build up the theory and implementation of this wavelet compression engine, starting from the basics of the discrete wavelet transform and ending with encoded data streams being written to RAM. It’s a bit of a long one, so I broke it into several sections:

See the [post here](http://scolton.blogspot.com/2019/10/real-time-wavelet-compression-for-high.html) and the [video](https://youtu.be/ep0a7_K0EIs) below.