---
title: 'Image Sensor from Discrete Parts Delivers Glorious 1-Kilopixel Images'
date: 2019-12-30T13:26:00+01:00
draft: false
---

Chances are pretty good that you have at least one digital image sensor somewhere close to you at this moment, likely within arm’s reach. The ubiquity of digital cameras is due to how cheap these sensors have become, and how easy they are to integrate into all sorts of devices. So why in the world would someone want to build [an image sensor from discrete parts that’s 12,000 times worse than the average smartphone camera?](https://www.youtube.com/watch?v=PaXweP73NT4) Because, why not?

\[Sean Hodgins\] originally started this project as a digital pinhole camera, which is why it was called [“digiObscura.”](https://github.com/IdleHandsProject/diycamera) The idea was to build a 32×32 array of photosensors and focus light on it using only a pinhole, but that proved optically difficult as the small aperture greatly reduced the amount of light striking the array. The sensor, though, is where the interesting stuff is. \[Sean\] soldered 1,024 ALS-PT19 surface-mount phototransistors to the custom PCB along with two 32-bit analog multiplexers. The multiplexers are driven by a microcontroller to select each pixel in turn, one row and one column at a time. It takes a full five seconds to scan the array, so taking a picture hearkens back to the long exposures common in the early days of photography. And sure, it’s only a 1-kilopixel image, but it works.

\[Sean\] has had this project cooking for a while – in fact, the multiplexers he used for the camera came up as [a separate project](https://hackaday.com/2018/06/09/arduino-analog-i-o-multiplexer/) back in 2018. We’re glad to see that he got the rest built, even with the recycled lens he used. One wonders how [a 3D-printed lens](https://hackaday.com/2014/12/13/3d-printed-lenses-open-up-possibilities/) would work in front of that sensor.

  
  
from Hackaday https://ift.tt/2MIvGcp  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)