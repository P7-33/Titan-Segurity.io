---
title: 'ML Everywhere with Inexpensive
Microcontrollers #TinyML #TFlite #BangleJS #NodeWatch #MachineLearning #ArtificialIntelligence @nearform @espruino'
date: 2020-01-13T07:19:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/Screen-Shot-2020-01-12-at-7.38.25-PM-e1578886919711-600x304.png)

Epruino bangle.js emulator from https://ift.tt/2hER8QZ.

Machine learning is making its way onto open-source DIY smartwatches! The [NodeWatch](https://nodewatch.dev/) was created for [NodeConf EU 2019](https://www.google.com/search?q=node+conf+edu+2019&rlz=1C5CHFA_enUS869US869&oq=node&aqs=chrome.1.69i57j69i59j0l3j69i60l3.2933j1j7&sourceid=chrome&ie=UTF-8) by [NearForm Research](https://www.nearform.com/) and [Espruino](https://espruino.com/). The watch uses the [NRF52832](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF52832) SoC with Bluetooth LE 4.2 and, with the Espruino [IDE](https://www.espruino.com/ide/), you can connect directly to the chip from the browser. The watch also runs [TensorFlow Lite](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite) which was used to train a [hand-gesture recognition](https://www.nearform.com/blog/running-tensorflow-lite-on-nodewatch-bangle-js/) model for NodeConf. In a [recent article](https://conoroneill.net/2019/12/04/why-running-tensorflow-lite-for-microcontrollers-on-extremely-inexpensive-devices-changes-everything/), [Conor O’Neill](https://conoroneill.net/), CPO of  NearForm, uses the NodeWatch as a case study to discuss ML on edge devices and the future of ML.

> …anyone can get involved in Machine Learning on inexpensive devices without having to learn about cross-compilers, Python distributions, USB-Serial adapters or GPUs.

The article talks about increased accessibility and lower cost of ML and hypothesizes that ML will be “everywhere” (using smartwatches and smart light bulbs as examples). Beyond consumer products, O’Neill suggests that these advances will improve ML education saying:

> I’m convinced tangible/tactile ML like this will engage people for far longer than “yes you’re right, it’s a cat”.

If you’d like to read more about ML on the NodeWatch check out [these](https://www.nearform.com/blog/bangle-js-hackable-oss-js-and-tensorflow-smartwatch/) [posts](https://www.nearform.com/blog/banglejs-oss-open-health-wearables-js-tensorflow/). If you’re interested in learning more about the NodeWatch, check out the [Kickstarter](https://www.kickstarter.com/projects/gfw/banglejs-the-hackable-smart-watch/posts) for bangle.js (NodeWatch) or the [bangle.js website](https://banglejs.com/). If you’re interested in the implementation, take a look at the [bangle.js app](https://banglejs.com/apps/) and [repo](https://github.com/espruino/BangleApps), the bangle.js TensorFlow [emulator](https://www.espruino.com/ide/emulator.html) or the Espruino [repo](https://github.com/espruino/).

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._