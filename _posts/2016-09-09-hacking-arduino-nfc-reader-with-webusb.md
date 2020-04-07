---
title: 'Hacking An Arduino NFC Reader With WebUSB'
date: 2020-01-02T07:47:00+01:00
draft: false
---

When \[gdarchen\] wanted to read some NFC tags, he went through several iterations. First, he tried an Electron application, and then a client-server architecture. But his final iteration was to make [a standalone reader with an Arduino and use WebUSB](https://github.com/gdarchen/webusb-arduino-nfc/tree/master/3-webusb) to connect to the application on the PC.

This sounds easy, but there were quite a few tricks required to make it work. He had to hack the board to get the NFC reader’s interrupt connected correctly because he was using a Leonardo board. But the biggest problem was enabling WebUSB support. There’s a library, but you have to change over your Arduino to use USB 2.1. It turns out that’s not hard, but there’s a caveat: Once you make this change you will need the WebUSB library in all your programs or Windows will refuse to recognize the Arduino and you won’t be able to easily reprogram it.

Once you fix those things, the rest is pretty easy. The PC side uses node.js. If you back up a level in the GitHub repository, you can see the earlier non-Arduino versions of the code, as well.

If you want to understand all the logic that went into the design, the author also included a [slide show](https://slides.com/gautierdarchen/webusb-arduino-nfc/fullscreen) that discusses the three versions and their pros and cons. He did mention that he wanted a short-range solution so barcodes and QR codes were out. He also decided against RFID but didn’t really say why.

[NFC business cards](https://hackaday.com/2017/10/25/nfc-enabled-business-card/) are a thing. You can also use them to catch some [public transportation](https://hackaday.com/2017/06/20/making-a-wearable-nfc-bus-pass/).

  
  
from Hackaday https://ift.tt/2ZJWQF9  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)