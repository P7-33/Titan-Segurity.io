---
title: 'Xaxxon announces Open LIDAR as Open Hardware with Open
Software #LIDAR #OpenHardware #OpenSource @xaxxontech'
date: 2019-10-15T14:58:00+01:00
draft: false
---

The [Xaxxon OpenLIDAR Sensor](http://www.xaxxon.com/xaxxon/openlidar) is a rotational laser scanner with open software and hardware, intended for use with autonomous mobile robots and simultaneous-location-and-mapping (SLAM) applications.

The sensor has a simple mechanical design, using the proven [Garmin LIDAR-Lite v3](https://buy.garmin.com/en-US/US/p/pn/010-01722-00) laser distance measurement sensor, wired through a rotational slip ring, with stepper motor drive, two 3D printed frame parts, and an Arduino compatible PCB. Power and communication are delivered via USB cable.

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-52.png)

Python ROS drivers and firmware source code [are available on our Github](https://github.com/xaxxontech/xaxxon_openlidar). All configuration settings are dynamically tweakable using the [rqt\_reconfigure](http://wiki.ros.org/rqt_reconfigure) GUI tool, which comes standard with all versions of ROS.

The sensor is compatible with Linux, Windows, and MacOS operating systems, running on either x86 or ARM architectures. However, full drivers and support are currently limited to systems running Linux OS with the Robot Operating System (ROS-Inigo/Kinetic/Melodic).

But, communication with host-systems other than Linux/ROS is straightforward using any programming language, thanks to the OpenLIDAR PCB’s [simple serial communication protocol](http://www.xaxxon.com/documentation/view/xaxxon-openlidar-pcb#commands).

See the [product page](http://www.xaxxon.com/xaxxon/openlidar) for more information and links to source files.

[http://www.xaxxon.com/images/xaxxon/openlidar/openlidarmapping.mp4](http://www.xaxxon.com/images/xaxxon/openlidar/openlidarmapping.mp4)