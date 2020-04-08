---
title: 'Issue 24 HackSpace magazine: a World War II radio broadcast time
machine #Radio #RaspberryPi #Amplifier #Adafruit @HackSpaceMag'
date: 2019-10-25T14:09:00+01:00
draft: false
---

![by Adam Clark](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-87.png)

[Issue 24, HackSpace Magazine](https://hackspace.raspberrypi.org/issues/24) features a vintage radio playback build using a [Raspberry Pi Zero](https://www.adafruit.com/product/3400) and an [Adafruit I2S Amplifier](https://www.adafruit.com/product/3006).

> The first obstacle was to find a satisfactory way to play back audio. In the past, I have had some success using PWM pins, but this needs a low-pass filter as well as an amplifier, and the quality of audio was never as good as I’d hoped for. The other alternative is to use one of the many HATs available, but these come at a price as they are normally aimed at more serious quality of audio. I wanted to keep the cost down, so these were excluded as an option. The other option was to use a mono I2S 3W amplifier breakout board – [MAX98357A from Adafruit](https://www.adafruit.com/product/3006) – which is extremely  
> simple to use. As the BBC didn’t start broadcasting stereo commercially until the late 1950s, this was also very apt for the radio (which only has one speaker).
> 
> ![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-88.png)
> 
> Connecting up this board is very easy – it just requires three GPIO pins, power, and the speaker. For this, I just soldered some female jumper leads to the breakout board and connected them to the header pins of the Raspberry Pi Zero. There are detailed instructions on the Adafruit website for this which basically entails running their install script.
> 
> ```
> curl -sS https://raw.githubusercontent. com/adafruit/Raspberry-Pi-Installer-Scripts/master/i2samp.sh | bash
> ```
> 
> Once the install scripts and mpg123 player are installed with a speaker connected, the Raspberry Pi Zero immediately started playing some very nice quality audio through the [on-board 3W amplifier](https://www.adafruit.com/product/3006) – and it is certainly loud enough to emulate a radio.
> 
> On/Off control is via a [Pimoroni OnOff SHIM](https://www.adafruit.com/product/3581).

The project is coded in Python and content is from the Internet Archive.

See the project in [Issue 24 of HackSpace Magazine](https://hackspace.raspberrypi.org/issues/24) ([PDF](https://hackspace.raspberrypi.org/issues/24/pdf) pp. 56-61)