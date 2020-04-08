---
title: 'Training StyleGAN with
RunwayML #Training #GAN #MachineLearning #ArtificialIntelligence @RunwayML'
date: 2019-12-09T05:40:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Screen-Shot-2019-12-08-at-7.09.10-PM-600x415.png)

Announcement for the Beta release of training on the RunwayML platform.

RunwayML is a machine learning platform for creators. The platform [boasts an impressive number of pre-trained algorithms](https://blog.adafruit.com/2019/08/12/runwayml-puts-machine-learning-in-the-hands-of-creators-machinelearning-runwayml-creators-runwayml-shiffman/) in addition to some [interactive demos](https://blog.adafruit.com/2019/09/27/interactive-ai-with-runwayml-experiments-machinelearning-artificialintelligence-ai-art-design-create-runwayml/). Several weeks ago they announced the Beta release of training on the platform! That said, training is currently limited to testing. If you would like to try it out and provide feedback, you can download RunwayML from their [website](https://runwayml.com/) and request training access through [support](https://support.runwayml.com/en/articles/3000038-runwayml-support). I went through that process this week and, once granted access, was able to get everything up and running in a couple of minutes.

RunwayML is currently using [transfer learning](https://medium.com/kansas-city-machine-learning-artificial-intelligen/an-introduction-to-transfer-learning-in-machine-learning-7efd104b6026) on the [StyleGAN model](https://link.medium.com/DpMVLUYK41) for training. StyleGAN is a [Generative Adversarial Network](https://blog.adafruit.com/2019/07/25/paint-by-ai-with-gaugan-gan-pytorch-machinelearning-nvidiadesign-liu_mingyu/) that is able to create photorealistic images. The model was trained on thousands of images of faces from [Flickr](https://github.com/NVlabs/ffhq-dataset). RunwayML allows users to upload their own datasets and retrain StyleGAN in the likeness of your datasets.

> …Transfer Learning leverages all of the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) it learned from the original data to speed up the process of learning features in your image dataset. Not only does this greatly reduce training time, it also reduces the number of images that you need to train your own model.

If you want to get started quickly you can also use one of RunwayML’s image datasets (mountains, forests, graffiti, etc). Selecting the smallest dataset (mountains) and training for two hours generated pretty passable landscape photos (below). If you’d like to learn more about training, check out the docs on the RunwayML [website](https://learn.runwayml.com/#/create/train-models)! If you’re interested in GANs or StyleGAN on RunwayML check out [these](https://www.youtube.com/watch?v=f-cCpVGoxhY) [videos](https://www.youtube.com/watch?v=vEetoBuHj8g).

![](https://cdn-blog.adafruit.com/uploads/2019/12/Sample-Step-220-300x171.jpg)

Early in Training – StyleGAN is just starting to learn about mountains.

![](https://cdn-blog.adafruit.com/uploads/2019/12/Screen-Shot-2019-12-08-at-6.26.42-PM-e1575863900159-300x172.png)

Midway Through Training – StyleGAN is having an identity crisis.

![](https://cdn-blog.adafruit.com/uploads/2019/12/Screen-Shot-2019-12-08-at-6.52.30-PM-e1575863940574-300x172.png)

Near the end of Training – Images are starting to look like mountains WITH faces.

![](https://cdn-blog.adafruit.com/uploads/2019/12/Screen-Shot-2019-12-08-at-7.32.26-PM-e1575864013901-300x170.png)

End of Training – Passable mountain landscape photos.

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._