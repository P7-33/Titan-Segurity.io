---
title: 'Add-On Makes ESP32 Camera Board Easier To Program'
date: 2020-01-10T01:32:00+01:00
draft: false
---

Don’t you just hate it when dev boards have some annoying little quirk that makes them harder to use than they should be? Take the ESP32-CAM, a board that started appearing on the market in early 2019. On paper, the thing is amazing: an ESP32 with support for a camera and an SD card, all for less than $10. The trouble is that programming it can be a bit of a pain, requiring extra equipment and a spare finger.

Not being one to take such challenges lying down, \[Bitluni\] has come up with [a nice programming board for the ESP32-CAM](https://www.youtube.com/watch?v=ikhZ34WgObc) that you might want to check out. The problem stems from the lack of a USB port on the ESP32-CAM. That design decision leaves users in need of a USB-to-serial adapter that has to be wired to the GPIO pins of the camera board so that programs can be uploaded from the Arduino IDE when the reset button is pressed. None of that is terribly complex, but it is inconvenient. His solution is called cam-prog, and it takes care of not only the USB conversion but also resetting the board. It does that by simply power cycling the camera, allowing sketches to be uploaded via USB. It looks to be a pretty handy board, which will be available on [his Tindie store](https://www.tindie.com/stores/bitluni/#store-section-products).

To demonstrate the add-on, he programmed his ESP32-CAM and connected it to [his enormous ping pong ball video wall](https://hackaday.com/2019/08/29/giant-led-display-is-1200-balls-to-the-wall/). The video quality is about what you’d expect from a 1,200 pixel display at 40 mm per pixel, but it’s still pretty smooth – smooth enough to make his interpretive dance moves in the last few minutes of the video pretty interesting.

  
  
from Hackaday https://ift.tt/35zR75X  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)