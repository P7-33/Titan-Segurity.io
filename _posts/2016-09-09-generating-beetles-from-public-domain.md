---
title: 'Generating Beetles from Public Domain Images'
date: 2020-01-12T13:18:00+01:00
draft: false
---

Ever since \[Ian Goodfellow\] and his colleagues invented the generative adversarial network (GAN) in 2014, hundreds of projects, from style transfers to poetry generators, have been produced using the concept of contesting neural networks. Unlike traditional neural networks, GANs can generate new data that fits statistically within the same set as the training set.

\[Bernat Cuni\], the one-man design team behind \[cunicode\] came up with the idea to [generate beetles](https://www.cunicode.com/works/confusing-coleopterists/#StyleGAN) using this technique. Inspired by material published on [Machine Learning for Artists](https://ml4a.github.io/), he decided to deploy some visual experiments with zoological illustrations. The training data was found from a public domain book hosted at archive.org, found through the Biodiversity Heritage Library. A combination of OpenCV and ImageMagick helped with individually extracting illustrations to squared images.

![](https://hackaday.com/wp-content/uploads/2020/01/Screen-Shot-2020-01-02-at-1.11.14-PM.png?w=400)

\[Cuni\] then ran a DCGAN with the data set, generating the first set of quasi-beetles after some tinkering with epochs and settings. After the failed first experiment, he went with StyleGAN, setting up a machine at [PaperSpace](https://www.paperspace.com/ml) with 1 GPU and running the training for >3 days on 128 px images. The results were much better, but fairly small and the cost of running the machine was quite expensive (>€125).![](https://hackaday.com/wp-content/uploads/2020/01/Screen-Shot-2020-01-02-at-1.11.29-PM.png?w=400)

Given the success of the previous experiment, he decided to transfer over to [Google CoLab](https://www.google.com/url?cad=rja&cd=1&esrc=s&q=&rct=j&sa=t&source=web&uact=8&url=https%3A%2F%2Fcolab.research.google.com%2F&usg=AOvVaw3A5aPK2kLFzKOzb6sOckVw&ved=2ahUKEwidmdGN7s7mAhXNz4UKHa42DK0QFjAAegQIEBAC), using their 12 hours of K80 GPU per run for free to generate some more beetles. With the intent on producing more HD beetles, he used [Runway](https://runwayml.com/) trained on 1024 px beetles, discovering much better results after 3000 steps. The model was moved over to Google CoLab to produce HD outputs.

He has since continued to experiment with the beetles, producing some [confusing generated image](https://twitter.com/cunicode/status/1207695898710626304?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1207695898710626304)s and [fun collectibles](https://makersplace.com/store/cunicode/category/confusing-coleopterists/).

Check out the beetles here:

  
  
from Hackaday https://ift.tt/2ThaX3m  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)