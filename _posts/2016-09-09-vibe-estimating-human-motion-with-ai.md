---
title: 'VIBE: Estimating Human Motion with
AI #ArtificialIntelligence #MachineLearning #PyTorch #AdversarialNetworks @MPI_IS'
date: 2020-01-27T07:28:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/vibe.gif)

VIBE example from https://ift.tt/348WHM9.

At the end of last year, the [Max Planck Institute for Intelligent Systems](https://www.is.mpg.de/) published a [paper](https://arxiv.org/abs/1912.05656) on VIBE – Video Inference for Human Body Pose and Shape Estimation. VIBE is a machine learning framework that is able to digest video and produce motion sequences without 3D labels. The framework has a number of moving pieces and utilizes data from the [AMASS motion capture dataset](https://amass.is.tue.mpg.de/).

> Our key novelty is an adversarial learning framework that leverages AMASS to discriminate between real human motions and those produced by our temporal pose and shape regression networks. We define a temporal network architecture and show that adversarial training, at the sequence level, produces kinematically plausible motion sequences without in-the-wild ground-truth 3D labels.

The code for the [PyTorch](https://pytorch.org/) implementation of VIBE can be found on [@mkocabas](https://ps.is.mpg.de/person/mkocabas)‘ GitHub [Repo](https://github.com/mkocabas/VIBE). If you’d like to try out the implementation there is also a [CoLab](https://colab.research.google.com/drive/1dFfwxZ52MN86FA6uFNypMEdFShd2euQA) version. If you’d like to see some example output check out this [video](https://drive.google.com/file/d/1kCQI2mjPkhFaHbnquiQHtq7oArDQ_Aus/view).

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2GrzWJK  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)