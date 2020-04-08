---
title: 'Native MP3 decoding/playback in CircuitPython @adafruit @circuitpython'
date: 2019-11-30T03:58:00+01:00
draft: false
---

Native MP3 decoding/playback in CircuitPython ([video](https://youtu.be/4xh_mPaYG3s)). We’re testing out a new PR in CircuitPython by JEpler. This one adds native MP3 decoding – no playback chip required! Thanks to the patent expiration, we can now distribute MP3 decoding and its a great way to support compressed audio playback. We can even play 2 mp3’s at once. More than that isn’t possible yet due to RAM constraints. I’m testing an nRF52840 BLE feather with I2S. We’ll also try SAMD51 next. SAMD21 won’t be able to do it, due to the RAM requirements.