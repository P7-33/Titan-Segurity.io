---
title: 'A CircuitPython library for Fast Fourier Transforms
(FFT) #CircuitPython #FFT @tdsepsilon'
date: 2020-01-21T15:40:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/untitled-27.jpg)

[Tom posts on Twitter](https://twitter.com/tdsepsilon/status/1219116722021490690) about creating a Fast Fourier Transform (FFT) library for [CircuitPython](https://circuitpython.org/)!

![](https://cdn-blog.adafruit.com/uploads/2020/01/untitled-26-600x383.jpg)

[The guide post](https://teaandtechtime.com/fft-circuitpython-library/) has all the details:

> I have been playing with the [Adafruit CircuitPython](https://circuitpython.org/) for a while now on the PyGamer board . Using the Adafruit libraries to light up the NeoPixels and to display pictures and text on the screen.
> 
> Then I learned that the Hackaday Supercon attendees would be given an [Adafruit Edge Badge](https://www.adafruit.com/product/4400) along with the official badge. This had a built in microphone which sparked my interest on creating an audio spectrum waterfall plot of the measured frequency.
> 
> This was a bit of a problem because the library that python uses to perform the Fast Fourier Transform (FFT) did not have a CircuitPython port. So I decided to write my own code in CircuitPython to compute the FFT. Now I could have written C code to run underneath, but I have not gotten to that point yet, and also wanted to get this done for Supercon, which required a few other parts, so that drove my decision to just use pure Python.

Tom concludes:

> **I have really enjoyed using CircuitPython, as it is a much simpler method to playing with microcontrollers than Arduino.** The ecosystem that Adafruit has developed makes it a breeze for developers, new and old, to quickly get a project off the ground and running. I hope more boards and manufactures make CircuitPython an option on their products as it provides fast visual feedback and is a simple way to work with microcontroller hardware. I also hope more people start creating libraries for the ecosystem so that future users have an easier time developing new creative things.

See [the GitHub repo for the library here](https://github.com/Tschucker/CircuitPython_FFT) and [the blog post here](https://teaandtechtime.com/fft-circuitpython-library/). Excellent work!

[Learn more about CircuitPython at circuitpython.org](https://circuitpython.org/) and [see the Adafruit Edge Badge here](https://www.adafruit.com/product/4400).