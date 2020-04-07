---
title: 'Arduino Pedometer Counts Your Steps'
date: 2020-01-11T01:32:00+01:00
draft: false
---

There’s a trend in corporate America that has employees wear a step counter — technically a pedometer — and compete in teams to see who can get the most number of steps. We wonder how many people attach the device to an electric drill and win the competition easily. However if you want to do your own measurements, \[Ashish Choudhary\] has plans for making [a pedometer with an Arduino](https://circuitdigest.com/microcontroller-projects/diy-arduino-pedometer-counting-steps-using-arduino-and-accelerometer). The device isn’t tiny, but as you can see in the video below it seems to work.

For the extra size, you do get some features. For one, there is a 16×2 LCD display and an ADXL335 accelerometer, and you can probably imagine some other cool features for such a device.

The Arduino computes the magnitude of the acceleration, and if it exceeds a certain threshold it adds a step to the step count. Honestly, this is a fun project but it cries out for a more compact form factor. An ESP8266 for example could ditch the display and connect via WiFi to your phone. Then again, your phone can probably do the same job, as could not to mention many smartwatches. But those don’t have nearly as much geek cred as this project.

This is [a little large for a hamster](https://hackaday.com/2017/05/20/pedometer-for-calorie-conscious-hamster-owners/). On the other hand, there’s [plenty you can do with the accelerometer](https://hackaday.com/2016/06/24/taming-robot-arm-jump-with-accelerometers/) after you’ve had enough fun counting steps.

  
  
from Hackaday https://ift.tt/2R2VpOd  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)