---
title: 'Reverse engineering Bluetooth Low Energy
notes #Bluetooth #BLE @ifnotpike'
date: 2019-12-09T16:40:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-18.png)

NotPike at [bad-radio.solutions](https://bad-radio.solutions/notes_ble) writes about taking a commercial piece of gear supporting Bluetooth low energy (BLE) unencrypted communications and reverse engineering the communications.

> Kestrel is in the business of building weather and wind meters. The one I’m poking at is a 5500 Fire Weather Meter Pro and was designed for wildland fighters in mind. More or less it’s the same as the other meters and can do some wize bang math to output the Probability of Ignition (POI) and Fine Dead Fuel Moisture… Also you’re paying an extra $200 but you know lol, you’re paying the price for something built for “Emergency Response”. To help keep track of this data Kestrel built a phone app that connects to these devices using BLE. It stores weather measurements and maps|out trends in the weather. Because there’s no real consequences (As far as  I can tell) for open communication, the developers didn’t bother implementing crypto / authentication for the BLE link.

![](https://bad-radio.solutions/img/ble_1.jpg)

[See the post](https://bad-radio.solutions/notes_ble) for the process used.