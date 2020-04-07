---
title: 'Displaying 9 DoF orientation in a browser using webserial
with @adafruit CLUE #threejs #JavaScript3Dlibrary'
date: 2020-02-15T16:14:00+01:00
draft: false
---

[The CLUE board](https://www.adafruit.com/clue) has a 9 DoF motion sensor (accel/gyro/mag) that can be used to calculate orientation ([video](https://youtu.be/Z0IpAMcecHE)). It’s hard to visualize using just text. Normally folks would use a Processing sketch to display the 3D model but now that webserial is available in the browser, it’s much easier to use that! This website uses webserial to get the Euler angles & three.js to display a bunny that moves around. We’ll update it to use quaternions next ![🙂](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f642.png)