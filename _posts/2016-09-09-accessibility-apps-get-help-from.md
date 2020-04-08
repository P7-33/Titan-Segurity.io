---
title: 'Accessibility Apps Get Help from Bluetooth Buttons'
date: 2019-11-10T13:08:00+01:00
draft: false
---

Ever hear of Microsoft Soundscape? We hadn’t, either. But apparently it and similar apps like Blindsquare provide people with vision problems context about their surroundings. The app is made to run in the background of the user’s mobile device and respond to media controls, but if you are navigating around with a cane, getting to media controls on a phone or even a headset might not be very convenient. [\[Jazzang\] set out to build buttons that could control apps](https://www.instructables.com/id/Arduino-Accessibility-Around-Me-Buttons-Switch-Con/) like this that could be integrated with a cane or otherwise located in a convenient location.

There are four buttons of interest. Play/pause, Next, Back, and Home. There’s also a mute button and an additional button you can use with the phone’s accessibility settings. Each button has a special function for Soundscape. For example, Next will describe the point of interest in front of you. Soundscape runs on an iPhone so Bluetooth is the obvious choice for creating the buttons.

To simplify things, the project uses an Adafruit Feather nRF52 Bluefruit board. Given that it’s Arduino compatible and provides a Bluetooth Human Interface Device (HID) out of the box, there’s almost nothing else to do for the hardware but wire up the switches and some pull up resistors. That would make the circuit easy to stick almost anywhere.

Software-wise, things aren’t too hard either. The library provides all the Bluetooth HID device trappings you need, and once that’s set up, it is pretty simple to send keys to the phone. This is a great example of [how simple so many tasks have become](https://hackaday.com/2019/11/07/found-footage-elliot-williams-talks-nexus-technologies/) due to the availability of abstractions that handle all of the details. Since a Bluetooth HID device is just a keyboard, you can probably think of many other uses for this setup with just small changes in the software.

[We covered the Bluefruit](https://hackaday.com/2013/09/24/announcing-adafruits-bluefruit/) back when it first appeared. We don’t know about mounting this to a cane, but we do remember something similar [attached to a sword](https://hackaday.com/2018/08/16/welcome-to-the-internet-of-swords/).

  
  
from Hackaday https://ift.tt/34RbBr7  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)