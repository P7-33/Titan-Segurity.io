---
title: 'Fashion++: Minimal Edits for Outfit
Improvement #MachineLearning #Fashion #ComputerVision #DeepLearning #ArtificialIntelligence #AI @facebookai'
date: 2019-09-27T02:48:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/09/fashion_edits_092619.png)

Small changes to make an outfit more fashionable, the manual way. Photo credit: @minichre.

Whether you have a closet that would make [Cher from Clueless](https://mashable.com/2013/03/04/clueless-closet-fashion/) green or you have the [Steve Job’s uniform](https://www.cnn.com/2015/10/09/world/gallery/decision-fatigue-same-clothes/index.html) you’ve likely struggled to look polished at some point. In a recent [post](https://twitter.com/facebookai/status/1175058263315861505?s=20), Facebook AI announced [Fashion ++](https://research.fb.com/publications/fashion-minimal-edits-for-outfit-improvement/) a machine learning model that suggests small changes to make an outfit more fashionable (like removing the green sweater in the photo above).

> Whether removing an accessory, selecting a blouse with a higher neckline, tucking in a shirt, or swapping to pants a shade darker, often small adjustments can make an existing outfit noticeably more stylish.

The model, “consists of a deep image generation neural network that learns to synthesize clothing”. Fashion++ ingests a picture which is split into shape and texture features. Splitting the image into two components allows for edits in fit, presentation, color, patterns and material. Once the model makes enhancements to the image shape and texture (separately) the texture is mapped back onto the shape to produce the final fashionable photo.

> We first obtain latent features from texture and shape encoders Et and Es. Our editing module F ++ operates on the latent texture feature t and shape feature s. After an edit, the shape generator Gs first decodes the updated shape feature s++ back to a 2D segmentation mask m++, and then we use it to region-wise broadcast the updated texture feature t++ into a 2D feature map u++. This feature map and the updated segmentation mask are passed to the texture generator Gt to generate the final updated outfit x++.

If you’d like to take a look at Fashion++ in action checkout the [publication](https://arxiv.org/abs/1904.09261) written by Wei-Lin Hsiao, Isay Katsman, Chao-Yuan Wu, [Devi Parikh](https://research.fb.com/people/parikh-devi/) ([@deviparikh](https://twitter.com/deviparikh)) and Kristen Grauman. The results in the paper are pretty impressive and beg the question…when can we use it? @deviparikh [commented](https://twitter.com/deviparikh/status/1175066965330685953) on Twitter that this will be open source soon! You can take a look at some other cool fashion projects by Wei-Lin (Kimberly) Hsiao [here](https://www.cs.utexas.edu/~kimhsiao/). You can also find more computer vision work by Kristen Grauman’s lab [here](http://www.cs.utexas.edu/~grauman/).