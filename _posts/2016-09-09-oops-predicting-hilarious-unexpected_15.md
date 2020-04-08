---
title: 'Oops! Predicting Hilarious ‘Unexpected’ Action in
Videos #MachineLearning #ArtificialIntelligence #NeuralNet #3DCNN'
date: 2019-12-16T07:35:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Screen-Shot-2019-12-15-at-7.12.38-PM-600x318.png)

Oops! video tracking identifying unintentional action in a video from https://ift.tt/2OQqvaq

Columbia University recently [published a paper](https://oops.cs.columbia.edu/paper.pdf) on ‘fail’ videos. Besides being a ton of fun to [watch](https://oops.cs.columbia.edu/data/explore/) it turns out classifying ‘fail’  action (or unintentional action) is a difficult machine learning problem. The project, published by [Dave Epstein](https://cv.cs.columbia.edu/dave/), [Boyuan Chen](http://www.cs.columbia.edu/~bchen/) and [Carl Vondrick](http://www.cs.columbia.edu/~vondrick/), includes the development of the [‘Oops! dataset’](https://oops.cs.columbia.edu/data/). This dataset contains hours of ‘fail’ videos from YouTube with the unintentional action annotated.

> The dataset consists of 20,338 videos from YouTube fail compilation videos, adding up to over 50 hours of data. These clips, filmed by amateur videographers in the real world, are diverse in action, environment, and intention.

To recognize and predict unintentional action in the videos the team utilized a [3D convolutional network](https://towardsdatascience.com/2d-or-3d-a-simple-comparison-of-convolutional-neural-networks-for-automatic-segmentation-of-625308f52aa7). The still image above shows a snapshot of outputs from the machine learning model which predicts intentional, transitional, and unintentional action in the video. As a comparison, the team also investigated the speed of video to measure intentionality. The intrinsic speed model is competitive with the machine learning algorithm but neither is comparable to human performance.

> We train a supervised neural network as a baseline and analyze its performance compared to human consistency on the tasks. We also investigate self-supervised representations that leverage natural signals in our dataset, and show the effectiveness of an approach that uses the intrinsic speed of video to perform competitively with highly-supervised pretraining. However, a significant gap between machine and human performance remains.

If you would like to learn more check out the blog [post](https://oops.cs.columbia.edu/) for “Oops! Predicting Unintentional Action in Video”. You can also download the [Oops! dataset](https://oops.cs.columbia.edu/data/) or check out the code on the GitHub [repo](https://github.com/cvlab-columbia/oops).

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._