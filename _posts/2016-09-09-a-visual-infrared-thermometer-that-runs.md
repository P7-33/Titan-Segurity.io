---
title: 'A Visual Infrared Thermometer That Runs Off Your Laptop'
date: 2019-10-25T09:01:00+01:00
draft: false
---

A common measurement for circuits is heat dissipation inspection. While single point thermometers do the trick, they can be quite annoying to use. Meanwhile, a thermal imaging camera is often out of the budget for hobbyists. How about building your own [visual thermometer](https://www.fischl.de/usb2fir/) for cheap? That’s what \[Thomas Fischl\] decided to do, using an infrared thermal sensor array (MLX90640) connected through a PIC16LF1455 to a host computer. The computer handles the temperature calculation and visualization of hot spots, gathered from data collected by the IR pixel.

![](https://hackaday.com/wp-content/uploads/2019/10/usb2fir_matplotlib.png?w=400)

The interface board, USB2FIR, has full access to MLX90640 memory and can handle bulk transfer for faster data transmission of the raw sensor data collected by the pixel. A USB driver is needed to access the board – once the data is fetched, the visualizations can be created from a Matplotlib and TKinter GUI showing frame data and a real time heat map with minimum, maximum, and central temperature.

The hardware isn’t complicated, since the board relies on several ICs for processing the sensor data and immediately sends over the data to be processed externally. With some modifications – a 3D-printed enclosure, for instance – this can easily be made into a discreet tool for heat detection.

  
  
from Hackaday https://ift.tt/2MN4sla  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)