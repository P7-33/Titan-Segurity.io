---
title: 'Combining AI Tools to Create New Beetles with
GANs #ArtificialIntelligence #MachineLearning #Colab #StyleGAN #RunwayML @cunicode'
date: 2020-02-10T10:23:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/Screen-Shot-2020-02-09-at-10.31.21-PM-600x399.png)

From the book “Biologia Centrali-Americana :zoology, botany and archaeology”

Earlier this year @cunicode [announced](https://twitter.com/cunicode/status/1214910531888439298) the release of a model titled “Confusing Coleopterists” which generates new beetles! Well, _images_ of beetles. This project started with a very thorough zoological guide to beetles titled, “[Biologia Centrali-Americana :zoology, botany and archaeology](https://archive.org/details/mobotbca_12_06_01s)“. The images in the book are beautiful, detailed and striking (see example excerpt above). @cunicode used the data in this book to create a dataset that was used to generate new AI-beetles. After experimenting with style transfer and deep dream @cunicode decided to work with GANs.

> Previously I ran some test with [DeepDream](https://research.googleblog.com/2015/06/inceptionism-going-deeper-into-neural.html) and [StyleTransfer](https://github.com/jcjohnson/neural-style), but after discovering the material published at [Machine Learning for Artists](https://ml4a.github.io/) / [@ml4a\_](https://twitter.com/ml4a_) , I decided to experiment with the [Generative Adversarial Network (GAN)](https://en.wikipedia.org/wiki/Generative_adversarial_network) approach.

The first iteration followed the methods in this [lecture](https://ml4a.github.io/classes/itp-F18/06/) on utilizing [DCGAN](https://github.com/carpedm20/DCGAN-tensorflow) but generated some pretty _fuzzy_ beetles. After that, @cunicode focused on [StyleGAN](https://github.com/NVlabs/stylegan). The first iteration utilized 128px images of beetles and trained the algorithm with [PaperSpace](https://www.paperspace.com/ml). Three days, 1 GPU,  and €125 later and some _new_ bugs were created but they were a bit low res. The next step was to generate high-resolution beetles by loading the 1024px dataset of creepy crawlies onto RunwayML and train a model. The trained model was exported to Colab and used to generate never before seen beetles.

If you would like to try out this “buggy” model (we’re talking literal bugs, not digital ones) download [RunwayML](https://runwayml.com/). If you want to tryout StyleGAN checkout this [colab](https://colab.research.google.com/drive/1ShgW6wohEFQtqs_znMna3dzrcVoABKIH#forceEdit=true&sandboxMode=true&scrollTo=rYdsgv4i6YPl). If you would like to learn more about @cunicode’s methodology check out this [post](https://www.cunicode.com/works/confusing-coleopterists). Last but not least, if you want to get lost in images of AI-generated beetle’s take a look at cunicode’s [Instagram](https://www.instagram.com/p/B52l0NVn-F_/) or [thisbeetledoesnotexist.com](http://thisbeetledoesnotexist.com/).

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/38cgQ6Q  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)