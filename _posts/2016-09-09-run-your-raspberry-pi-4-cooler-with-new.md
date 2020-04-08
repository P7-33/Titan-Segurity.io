---
title: 'Run your Raspberry Pi 4 cooler with a new
firmware @Raspberry_Pi #Thermal'
date: 2019-12-03T15:26:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/pi4-vlisdram-idle-scaled.png)

It’s no secret that the Raspberry Pi 4 is faster than the Raspberry Pi 3 B+. Unfortunately, getting better performance out of this board requires a heatsink or a heatsink _and _fan to ensure the board won’t be thermally throttled.

Last week, the Raspberry Pi Foundation released a new firmware to the Via Labs USB Controller (VLI). This USB controller handles the two USB 3.0 ports on the Pi 4, and the updated firmware drops the overall temperature by 3 degrees C to 5 degrees C. The writeup on the Raspberry Pi website is a lengthy blog post describing how they stress test the CPU and GPU to determine the power draw of the Pi at idle and load.

![](https://cdn-blog.adafruit.com/uploads/2019/12/Raspberry-Pi-4-Power-Consumption-768x489.png)

To ensure your Pi 4 is running the latest firmware, open a terminal on your Raspberry Pi and enter:

`sudo apt update`  
`sudo apt full-upgrade`

Then, to restart your Pi, run:

`sudo shutdown - r now`

_Have you noticed your Pi running cooler? Did you build a water-cooling loop for your Pi?_ Tell us about it in the comments below.

[Read the full writeup on Raspberrypi.org >>>](https://www.raspberrypi.org/blog/thermal-testing-raspberry-pi-4/)