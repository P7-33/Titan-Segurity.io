---
title: 'New Linux Kernel 5.5 – New Interfaces in gpiolib'
date: 2020-02-09T12:12:00+01:00
draft: false
---

[![120px Tux svg](https://cdn-blog.adafruit.com/uploads/2020/02/120px-Tux.svg_.png "120px-Tux.svg.png")](https://en.wikipedia.org/wiki/Linux_kernel)

Blog post on [Micro Hobby](https://microhobby.com.br/blog/2020/02/02/new-linux-kernel-5-5-new-interfaces-in-gpiolib/) discussing new features of Linux Kernal 5.5:

> This last Sunday, 01/26/2020, the first version of the Linux Kernel of the year was released, v5.5. In this version we have new features in gpiolib, new interfaces for pin configuration. Now we can configure a pin as a pull-up or pull-down via user space 😍.

> libgpiod makes it very easy to use the interfaces, abstracting the calls from ioctl, open and read on /dev/gpiochip files. In addition to having complete command line tools, which can facilitate use in bash scripts for example. It is a library maintained by the community that has contributors who are also part of the Linux Kernel developers, in fact maintainers of the gpio and pin control subsystems.
> 
> gpiolib is quite complete. Now we can say goodbye to /sys/class/gpio and wiringPi libraries (writing in /dev/mem that ugly 😢) without fear! The new user space GPIO management interfaces are the most secure, reliable and recommended way to work with GPIOs. They are designed to work in conjunction with the kernel space, to keep track of hardware and resource states in the best way.

[Learn more!](https://microhobby.com.br/blog/2020/02/02/new-linux-kernel-5-5-new-interfaces-in-gpiolib/)

Thanks for the [Tip](https://learn.adafruit.com/how-to-send-a-blogtip-to-adafruit/) Drew.