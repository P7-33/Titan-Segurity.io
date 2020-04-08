---
title: 'Gesture Wand on the Edge with Particle’s Xenon and
TF #Tensorflowlite #machinelearning #AI #artificialintelligence #particle'
date: 2019-12-02T05:43:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/xenon_tflite.jpg)

Gesture Wand Setup with Particle’s Xenon board and Adafruit’s LSM9DS1 accelerometer. Image Credit: Brandon Satrom.

Particle recently [posted](https://blog.particle.io/2019/11/08/particle-machine-learning-101/) several guides for machine learning on MCUs. Most recently, Brandon Satrom [created](https://blog.particle.io/2019/11/26/machine-learning-102/) a gesture tracking device using [Particle’s](https://www.particle.io/) [Xenon board](https://store.particle.io/collections/bluetooth/products/xenon-kit) and Adafriut’s [LSM9DS1 3 axis accelerometer](https://www.adafruit.com/product/3387). The device is able to differentiate between three gestures “O”, “W”, and “left slope” and lights up an LED on the Xenon board when a gesture is detected. A pre-trained [TensorFlow Lite](https://www.tensorflow.org/lite/microcontrollers) gesture model was used to power the device. This model is a [convolutional neural network](https://towardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53) trained on gesture data from several people.

> The model, which was created by the TensorFlow team, is a 20 KB convolutional neural network (or CNN) trained on gesture data from 10 people performing four gestures fifteen times each (ring, wing, slope, and an unknown gesture).

Besides being a fun and easy example of ML for IoT, Satrom also highlights the utility of performing machine learning computations on edge devices:

> If you’re working with a high-precision sensor and you need to make a decision based on raw data, you often cannot shoulder the cost of sending all that data to the cloud. And even if you could, the round trip latency runs counter to the frequent need for real-time decision-making.
> 
> By performing prediction on a microcontroller, you can process all that raw data on the edge, quickly, without sending a single byte to the cloud.

If you would like to learn more check out the GitHub [repo](https://github.com/bsatrom/Particle_TensorFlowLite/tree/master/examples/magic_wand) for this work.

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/37QdzdD  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)