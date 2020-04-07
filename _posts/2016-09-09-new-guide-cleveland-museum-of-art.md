---
title: 'NEW GUIDE: Cleveland Museum of Art PyPortal
Frame #AdafruitLearningSystem #CircuitPython #PyPortal #Adafruit @Adafruit @cogliano'
date: 2020-01-29T23:33:00+01:00
draft: false
---

![Adafruit Learning System](https://cdn-blog.adafruit.com/uploads/2020/01/untitled-58.jpg)

A new guide today in the Adafruit Learning System: a [Cleveland Museum of Art PyPortal Frame](https://learn.adafruit.com/cleveland-museum-of-art-pyportal-frame/overview) by Dan Cogliano.

On January 23, 2019, the Cleveland Museum of Art (CMA) announced over 31,000 digital images of artwork from its collection will be available in the public domain. There are dozens of art types included in the collection, including paintings, drawings, photographs, coins and jewelry. All of these images are available under [the Creative Commons Zero (CC0) license](https://creativecommons.org/publicdomain/zero/1.0/), which allows people to share, collaborate, remix, and reuse images from the collection for both commercial and non-commercial use. The CMA also created [a free API](https://openaccess-api.clevelandart.org/) that allows programs to easily retrieve information about each of these images.

This no solder project accesses the CMA API using [CircuitPython](https://circuitpython.org/) running on an [Adafruit PyPortal](https://www.adafruit.com/product/4116). It uses the API to pick a random item from the collection. It converts and resizes the JPEG image from the collection to a BMP image sized to the PyPortal using [Adafruit IO](https://io.adafruit.com/) image conversion service. Finally, the converted image is downloaded to the PyPortal for display. A new feature of the PyPortal allows the correct scaling of portrait images, which is a great feature for this project.

[See this new guide now > > >](https://learn.adafruit.com/cleveland-museum-of-art-pyportal-frame/)

![adafruit_io_IMG_20200129_141515.jpg](https://cdn-learn.adafruit.com/assets/assets/000/087/796/medium800/adafruit_io_IMG_20200129_141515.jpg?1580326095)