---
title: 'Tiny Machine Learning On The Attiny85'
date: 2020-01-07T13:04:00+01:00
draft: false
---

We tend to think that the lowest point of entry for machine learning  (ML) is on a Raspberry Pi, which it definitely is not. \[EloquentArduino\] has been pushing the limits to the low end of the scale, and managed to get a basic [classification model running on the ATtiny85](https://eloquentarduino.github.io/2019/12/machine-learning-on-attiny85/).

Using his experience of running ML models on an old Arduino Nano, he had created a [generator](https://eloquentarduino.github.io/2019/11/how-to-create-a-classifier-for-arduino-machine-learning-projects/) that can export C code from a `scikit-learn`. He tried using this generator to compile a support-vector colour classifier for the ATtiny85, but ran into a problem with the Arduino ATtiny85 compiler not supporting a variadic function used by the generator. Fortunately he had already experimented with an alternative approach that uses a non-variadic function, so he was able to dust that off and get it working. The classifier accepts inputs from an RGB sensor to identify a set of objects by colour. The model ended up easily fitting into the capabilities of the diminutive ATtiny85, using only 41% of the available flash and 4% of the available ram.

It’s important to note what \[EloquentArduino\] _isn’t_ doing here: running an artificial neural network. They’re just too inefficient in terms of memory and computation time to fit on an ATtiny. But neural nets aren’t the only game in town, and if your task is classifying something based on a few inputs, like reading a gesture from accelerometer data, or naming a color from a color sensor, the approach here will serve you well. We wonder if this wouldn’t be a good solution to the pesky problem of [identifying bats by their calls](https://hackaday.com/2019/11/21/training-bats-in-the-random-forest-with-the-confusion-matrix/).

We really like how approachable machine learning has become and if you’re keen to give ML a go, have a look at the rest of the EloquentArduino blog, it’s a small goldmine.

We’re getting more and more machine learning related hacks, like basic [ML on an Arduino Uno](https://hackaday.com/2019/06/30/blisteringly-fast-machine-learning-on-an-arduino-uno/), and [Lego sortings](https://hackaday.com/2019/06/30/blisteringly-fast-machine-learning-on-an-arduino-uno/) using ML on a Raspberry Pi.

  
  
from Hackaday https://ift.tt/2QvkMsL  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)