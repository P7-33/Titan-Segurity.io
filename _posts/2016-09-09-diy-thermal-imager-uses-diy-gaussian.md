---
title: 'DIY Thermal Imager Uses DIY Gaussian Blur'
date: 2019-09-29T09:04:00+01:00
draft: false
---

Under the right circumstances, Gaussian blurring can make an image seem more clearly defined. \[DZL\] demonstrates exactly this with [a lightweight and compact Gaussian interpolation routine](http://blog.dzl.dk/2019/06/08/compact-gaussian-interpolation-for-small-displays/) to make the low-resolution thermal sensor data display much better on a small OLED.

\[DZL\] used an MLX90640 sensor to create a [DIY thermal imager](http://blog.dzl.dk/2019/06/08/cheap-diy-thermal-imager/) with a small OLED display, but since the sensor is relatively low-resolution at 32×24, displaying the data directly looks awfully blocky. Gaussian interpolation to improve the display looks really good, but it turns out that the full Gaussian interpolation isn’t a trivial calculation write on your own. Since \[DZL\] wanted to implement it on a microcontroller, the lightweight implementation was born. The project page walks through the details of Gaussian interpolation and how some effective shortcuts were made, so be sure to give it a look.

The MLX90640 sensor also makes an appearance in the [Open Thermal Camera](https://hackaday.com/2019/09/22/getting-the-heat-on-with-a-thermal-camera/), one of the entries for the 2019 Hackaday Prize. If you’re interested in thermal imaging, don’t miss this [teardown of a thermal imaging camera](https://hackaday.com/2018/11/07/teardown-of-a-relatively-cheap-thermal-camera/).

  
  
from Hackaday https://ift.tt/2mKFysp  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)