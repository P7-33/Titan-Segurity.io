---
title: 'Smart gaming dice with LEDs, Bluetooth, wireless
charging #Teardown #OpenSource @tanurai @pixels_dice @hackadayio'
date: 2020-01-28T15:26:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/untitled-1.gif)

On New Year’s Day, [Pixels](https://twitter.com/pixels_dice) introduced their [signature dice](https://t.co/z9bWkob7CL?amp=1). Features include:

> *   Rull RGB LEDs on each die face
> *   Orientation sensing
> *   Customization
> *   Wireless charging
> *   Bluetooth connectivity

Intrepid Maker [Tanya Fish](https://twitter.com/tanurai) decided to look and [see how they did that](https://twitter.com/tanurai/status/1222090312576913408).

She posts the project’s [Hackaday.io site](https://hackaday.io/project/28377-electronic-dice) where [Jean Simonet](https://hackaday.io/hacker/112676-jean-simonet) details what’s inside (i.e. no dice were harmed in this teardown). What makes things happen? Some tiny but sophisticated gear:

1

×

Linear Battery Charger Controller Li-Ion/Li-Pol 15mA to 500mA 4.2V

1

×

Power Distribution Switch

1

×

Lipo Battery, 60mAh

1

×

7uH wireless charging coil

1

×

Omnipolar Hall Effect Sensor,

1

×

Crystal 32MHz ±15ppm 8pF

20

×

APA102 2020RGB LED 2mm x 2mm (“DotStar LEDs”)

1

×

Full bridge rectifier – 200mA 80V

1

×

**nRF52810 Bluetooth microcontroller**

1

×

LDO Regulator, 200mA, 5 V

1

×

3 Axis Accelerometer

1

×

2.5V to 5.5V Synchronous Step Down Single-Out 0.6V to 5.5V

Quite smart for a small 20 sided package, achieved through flexible PCB folding and resin casting – see the video below.

You can get the details on the [project website](https://www.pixels-dice.com/) (Kickstarter coming soon) and [Hackaday.io](https://hackaday.io/project/28377-electronic-dice).