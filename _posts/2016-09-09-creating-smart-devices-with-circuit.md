---
title: 'Creating smart devices with Circuit Playground and
AWS #IoT #CircuitPython #CircuitPlaygroundExpress @AWS @Adafruit @SheSponse'
date: 2019-11-07T17:23:00+01:00
draft: false
---

[Jen at Jenius posts](https://jenius.io/portfolio/creating-smart-devices-with-circuitplayground-and-aws/) a smart coaster project. Multicolored LEDs illuminatea drink and indicate when the beverage is at the perfect temperature for consumption.

> I don’t have any coasters in my apartment, and all of my furniture is white. It only made sense for me to 3D print a coaster. However, if you know me, you know that I can’t just make a simple coaster, it has to have some tech inside of it. Immediately, I thought about what action I wanted my coaster to perform. … I decided that I wanted my coaster to tell me how cold or hot my drink is and also let me know when it’s reached the optimal level of drinking temperature.
> 
> I’m a massive fan of [Adafruit.com](https://www.adafruit.com/) and their boards. One of my favorite circuit boards developed by Adafruit is the Circuit Playground. It has every sensor one would need to create something unique, and it’s easy to program. I knew that the board had a temperature sensor, an accelerometer, and a speaker, which are things I needed to make the smart coaster project successful. 
> 
> Another cool thing about Circuit Playground is that you can program it in multiple ways. You can program the board with Arduino, CircuitPython, or even Microsoft MakeCode. Because I wanted to play audio files, I decided to use CircuitPython. I highly recommend following the “[CircuitPython Made Easy on Circuit Playground Express](https://learn.adafruit.com/circuitpython-made-easy-on-circuit-playground-express/circuit-playground-express-library)” by Adafruit to get started. This guide walks you through how to setup your Circuit Playground for Circuit Python code.  
> 
> I also recommend following Adafruit’s [Microcontroller Compatible Audio File Conversion](https://learn.adafruit.com/microcontroller-compatible-audio-file-conversion/check-your-files) guide as the Circuit Playground cannot play MP3s. All MP3s must be converted to PCM 16-bit Mono WAV files before using it in the code. 

The project uses the [Adafruit Circuit Playground Express board](https://www.adafruit.com/product/3333) and [CircuitPython](https://circuitpython.org/) for programming. Voice synthesis is provided by [Amazon Polly](https://aws.amazon.com/polly/).

See [the post](https://jenius.io/portfolio/creating-smart-devices-with-circuitplayground-and-aws/) for details and the videos [above](https://youtu.be/PibmNHyO_zQ) and [below](https://youtu.be/5cgWwjZuw64).

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-21.png)