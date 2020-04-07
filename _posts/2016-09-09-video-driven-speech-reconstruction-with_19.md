---
title: 'Video-Driven Speech Reconstruction with
GANs! #GAN #ArtificialIntelligence #MachineLearning #AI #Speech @imperialcollege @MajaPantic70'
date: 2020-02-20T08:44:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/Screen-Shot-2020-02-19-at-9.28.26-PM-600x274.png)

From the publication, “Video-Driven Speech Reconstruction using Generative Adversarial Networks”.  https://ift.tt/2SXYmR3

Last year the [iBUG group](https://ibug.doc.ic.ac.uk/) out of the [Imperial College London](https://www.imperial.ac.uk/) and the [Samsung AI Centre](https://research.samsung.com/aicenter_cambridge) published a [paper on speech reconstruction from video](https://arxiv.org/abs/1906.06301). The model presented is novel in its ability to generate interpretable speech from video only of previously unseen participants.  The main ML engine for the workflow is the [Wasserstein GAN](https://arxiv.org/abs/1701.07875) and is part of a collection of networks working together to generate speech. The model is composed of three parts: the generator network, the critic which forces the generation of ‘natural’ sounding waveforms, and a speech encoder.

> The generator network…is responsible for transforming the sequence of video frames into a waveform. During the training phase the critic network drives the generator to produce waveforms that sound similar to natural speech. Finally, a pretrained speech encoder is used to conserve the speech content of the waveform.

The model is trained on the [GRID dataset](http://spandh.dcs.shef.ac.uk/gridcorpus/) which is a freely available audiovisual corpus of participants reading sentences. The model was evaluated based on “sound quality” and on “accuracy of the spoken words”. They also [posted videos](https://sites.google.com/view/speech-synthesis/home) of model performance and comparisons with another recent framework/model [Lip2AudSpec](https://arxiv.org/abs/1710.09798) with quite impressive results.

If you’d like to learn more about the authors [check](https://ibug.doc.ic.ac.uk/people/kvougioukas) [out](https://ibug.doc.ic.ac.uk/people/pma) [their](https://ibug.doc.ic.ac.uk/people/spetridis) [pages](https://ibug.doc.ic.ac.uk/people/mpantic) on iBUG. If you’d like to check out their work you can find the [first](https://github.com/DinoMan) and [second](https://github.com/mpc001) authors on GitHub. Aaaand…if you’re still interested in more lip reading fun, take a look at this [video](https://twitter.com/psaranto/status/1142842720173600768) of Rasputin killing it at some Beyoncé karaoke.

##### _Written by Rebecca Minich, Product Analyst, Data Science at Google. Opinions expressed are solely my own and do not express the views or opinions of my employer._