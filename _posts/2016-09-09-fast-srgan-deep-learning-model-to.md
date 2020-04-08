---
title: 'Fast-SRGAN: Deep learning model to convert low res pictures to high res'
date: 2019-11-10T09:51:00+01:00
draft: false
---

[](https://github.com/HasnainRaz/Fast-SRGAN#fast-srgan)Fast-SRGAN
=================================================================

The goal of this repository is to enable real time super resolution for upsampling low resolution videos. Currently, the design follows the [SR-GAN](https://arxiv.org/pdf/1609.04802.pdf) architecture. But instead of residual blocks, inverted residual blocks are employed for parameter efficiency and fast operation. This idea is somewhat inspired by [Real time image enhancement GANs](http://www.micc.unifi.it/seidenari/wp-content/papercite-data/pdf/caip_2019.pdf).

The training setup looks like the following diagram:

[![](https://user-images.githubusercontent.com/4294680/67164120-22157480-f377-11e9-87c1-5b6acace0e47.png)](https://user-images.githubusercontent.com/4294680/67164120-22157480-f377-11e9-87c1-5b6acace0e47.png)

[](https://github.com/HasnainRaz/Fast-SRGAN#speed-benchmarks)Speed Benchmarks
=============================================================================

The following runtimes/fps are obtained by averaging runtimes over 800 frames. Measured on a GTX 1080.

Input Image Size

Output Size

Time (s)

FPS

128x128

512x512

0.019

52

256x256

1024x1024

0.034

30

384x384

1536x1536

0.068

15

We see it's possible to upsample to 720p at around 30fps.

[](https://github.com/HasnainRaz/Fast-SRGAN#pre-trained-model)Pre-trained Model
===============================================================================

A pretrained generator model on the DIV2k dataset is provided in the 'models' directory. It uses 6 inverted residual blocks, with 32 filters in every layer of the generator.

Upsampling is done via phase shifts in the low resolution space for speed.

To try out the provided pretrained model on your own images, run the following:

```
python infer.py --image\_dir 'path/to/your/image/directory' --output\_dir 'path/to/save/super/resolution/images'
```

[](https://github.com/HasnainRaz/Fast-SRGAN#training)Training
=============================================================

To train, simply execute the following command in your terminal:

```
python main.py --image\_dir 'path/to/image/directory' --hr\_size 384 --lr 1e-4 --save\_iter 200 --epochs 10 --batch\_size 14
```

Model checkpoints and training summaries are saved in tensorboard. To monitor training progress, open up tensorboard by pointing it to the 'logs' directory that will created when you start training.

[](https://github.com/HasnainRaz/Fast-SRGAN#samples)Samples
===========================================================

Following are some results from the provided trained model. Left shows the low res image, after 4x bicubic upsampling. Middle is the output of the model. Right is the actual high resolution image.

**384x384 to 1536x1536 Upsampling** [![](https://user-images.githubusercontent.com/4294680/67642055-4f7a9900-f908-11e9-93d7-5efc902bd81c.png)](https://user-images.githubusercontent.com/4294680/67642055-4f7a9900-f908-11e9-93d7-5efc902bd81c.png) **256x256 to 1024x1024 Upsampling** [![](https://user-images.githubusercontent.com/4294680/67642086-8fda1700-f908-11e9-8428-8a69ea86dedb.png)](https://user-images.githubusercontent.com/4294680/67642086-8fda1700-f908-11e9-8428-8a69ea86dedb.png) **128x128 to 512x512 Upsampling** [![](https://user-images.githubusercontent.com/4294680/67641979-5ead1700-f907-11e9-866c-b72d2e1dec8a.png)](https://user-images.githubusercontent.com/4294680/67641979-5ead1700-f907-11e9-866c-b72d2e1dec8a.png)

[](https://github.com/HasnainRaz/Fast-SRGAN#extreme-super-resolution)Extreme Super Resolution
=============================================================================================

Upsampling HQ images 4x as a check to see the image is not destroyed (since the network is trained on low quality, it should also upsample high quality images while preserving their quality).

[![](https://user-images.githubusercontent.com/4294680/67641915-b434f400-f906-11e9-88d1-44a7f2a80923.png)](https://user-images.githubusercontent.com/4294680/67641915-b434f400-f906-11e9-88d1-44a7f2a80923.png) [![](https://user-images.githubusercontent.com/4294680/67641917-b8611180-f906-11e9-8539-81f17d69653f.png)](https://user-images.githubusercontent.com/4294680/67641917-b8611180-f906-11e9-8539-81f17d69653f.png) [![](https://user-images.githubusercontent.com/4294680/67641946-fbbb8000-f906-11e9-95af-2873eb01e2ec.png)](https://user-images.githubusercontent.com/4294680/67641946-fbbb8000-f906-11e9-95af-2873eb01e2ec.png)

[](https://github.com/HasnainRaz/Fast-SRGAN#changing-input-size)Changing Input Size
===================================================================================

The provided model was trained on 384x384 inputs, but to run it on inputs of arbitrary size, you'll have to change the input shape like so:

```
from tensorflow import keras # Load the model model \= keras.models.load\_model('models/generator.h5') # Define arbitrary spatial dims, and 3 channels. inputs \= keras.Input((None, None, 3)) # Trace out the graph using the input: outputs \= model(inputs) # Override the model: model \= keras.model.Model(inputs, outputs) # Now you are free to predict on images of any size.
```

[](https://github.com/HasnainRaz/Fast-SRGAN#contributing)Contributing
=====================================================================

If you have ideas on improving model performance, adding metrics, or any other changes, please make a pull request or open an issue. I'd be happy to accept any contributions.

  
  
from Hacker News https://github.com/HasnainRaz/Fast-SRGAN