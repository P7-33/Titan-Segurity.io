---
title: 'Upgrade Your Shades to Find Lost Items'
date: 2019-12-07T16:02:00+01:00
draft: false
---

Ever wish you could augment your sense of sight?

\[Nick Bild\]’s latest hack helps you find objects (or people) by [locating their position](https://github.com/nickbild/artemis) and tracking them with a laser. The device, dubbed Artemis, latches onto your eyeglasses and can be configured to locate a specific object.

Images collected from the device are streamed to an NVIDIA Jetson AGX Xavier board, which uses a SSD300 (Single Shot MultiBox Detection) model to locate objects. The model was pre-trained with the [COCO dataset](https://pytorch.org/hub/nvidia_deeplearningexamples_ssd/) to recognize and localize 80 different object types given input from images thresholded in OpenCV. Once the desired object is identified and located, a laser diode activates.

Probably due to the current thresholds, the demo runs mostly work on objects placed further apart against a neutral background. It’s an interesting look at applications combining computer vision with physical devices to augment experiences, rather than simply processing and analyzing data.

The device uses two servos for controlling the laser: one for X-axis control and the other for Y-axis control. The controls are executed from an Adafruit Itsy Bitsy M4 Express microcontroller.

Perhaps with a bit more training, we might not have so much trouble with “Where’s Waldo” puzzles anymore.

Check out some of our other sunglasses hacks, from [home automation](https://hackaday.com/2019/08/15/home-automation-at-a-glance-using-ai-glasses/) to [using LCDs](https://hackaday.com/2019/10/22/the-futures-so-bright-i-gotta-wear-lcds/) to lessening the glare from headlights.

  
  
from Hackaday https://ift.tt/34Y21mA  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)