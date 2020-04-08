---
title: 'Scanning and advertising – BLE with CircuitPython
update @adafruit @circuitpython @tannewt'
date: 2019-10-13T20:18:00+01:00
draft: false
---

Scanning and advertising – BLE with CircuitPython update! Proximity based color demo using four Circuit Playground Express Bluefruits, [Tweets](https://twitter.com/tannewt/status/1182103930097958912) [and](https://twitter.com/tannewt/status/1182806194378833920) [YouTube](https://youtu.be/iHfd31qDTmw). Here’s a bit more about it from Scott…

> _“Last week I was heads down on BLE scanning and advertising. It’s the first phase of BLE and is incredibly powerful on it’s own. By advertising data directly, one can control a bunch of other devices all at once. I showed a simple demo of one device changing the color of another and then a more complex demo where multiple devices are advertising and multiple are scanning. By moving the scanning devices closer to different advertisers, the color changes to the nearest. To support this I’ve swapped the scan result from a list to an iterator, added rssi filtering and added advertising structure prefix filtering. These early filters reduce the number of Python level memory allocations and simplify the user code. On the library side, I’ve modeled the BLE API after the CircuitPython Register library which uses Python’s descriptor protocol to make defining advertisements declarative with easy to reuse components. This week I’m moving onto advertising designed to facilitate connections and ensuring all of the existing demos Dan has done still work.”_

All this and more in the [Python on hardware newsletter, sign up here](https://www.adafruitdaily.com/), goes out on Tues! [https://www.adafruitdaily.com/](https://www.adafruitdaily.com/)