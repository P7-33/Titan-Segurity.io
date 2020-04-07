---
title: 'Tensorflow Lite for Microcontrollers and…Shell
Scripts? #TensorFlow #TFlite #MachineLearning #ArtificialIntelligence #Make #ShellScripts @TensorFlow @petewarden'
date: 2020-02-04T07:17:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/0_nOrjnQz_E5qr6OiP-e1580796242983-600x149.png)

A few weeks ago [Pete Warden](https://github.com/petewarden) wrote about a recent engineering challenge with the [TensorFlow Lite](https://www.tensorflow.org/lite) project. The article titled ‘[Chesterton’s shell script](https://petewarden.com/2020/01/01/chestertons-shell-script/)‘ outlines the decision to use a combination of make and [shell scripts](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/lite/micro/tools/make/download_and_extract.sh) as their build tools. Warden outlines the necessity to keep TF Micro easy to compile for anyone working with it:

> For TFL Micro to be successful it has to be easy to compile, even for engineers from the embedded world who…may not be familiar with the wonderful world of installing Linux or MacOS dependencies. That meant downloading these packages had to be handled automatically by the build process.

Warden discusses the tradeoffs and highlights the challenges of maintaining this type of script. The moral being that before any implementation like this is rewritten in a way that seems ‘simpler’ it is best to understand the reasoning for that implementation inside and out before re-writing it. This is where [Chesterton’s fence](https://en.wikipedia.org/wiki/Wikipedia:Chesterton%27s_fence) comes in which can be summarized with, “understand the reasoning before reforming”.

To learn more about this implementation check out an early version of the shell script [here](https://github.com/tensorflow/tensorflow/blob/e98d1810c607e704609ffeef14881f87c087394c/tensorflow/lite/experimental/micro/tools/make/download_and_extract.sh). If you’d like to look at more of Pete Warden’s work on the TF build take a look at the GitHub repo [here](https://github.com/tensorflow/tensorflow/tree/e98d1810c607e704609ffeef14881f87c087394c/tensorflow/lite/experimental/micro/tools/make).

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2OoMOF2  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)