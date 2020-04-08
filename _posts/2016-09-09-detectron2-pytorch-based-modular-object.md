---
title: 'Detectron2: A PyTorch-based modular object detection library'
date: 2019-11-10T07:51:00+01:00
draft: false
---

Since its release in 2018, the [Detectron](https://l.facebook.com/l.php?u=https%3A%2F%2Fresearch.fb.com%2Fblog%2F2018%2F01%2Ffacebook-open-sources-detectron%2F&h=AT0fj_W_wUK6lFc4CsSKM7I1pFEYoIxGR8edx8rrnudxj7wwSbL_zhJ2EpEWFD37WOHVZodKbu3l3fq4av5uUUN9o7Cpns27EAMaMOF8dzKGDvkW4ybECddyT0qyrtPLn0hsU1c0Dxmkx4-HSuGrdy9ViFQ) object detection platform has become one of Facebook AI Research (FAIR)’s most widely adopted open source projects. To build on and advance this project, we are now sharing the second generation of the library, with important enhancements for both research and production use. It is available [here.](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2Ffacebookresearch%2Fdetectron2&h=AT3x1xym-cDSyrzFUW63hbDw1YGHvEpPt4FvpQlOztpNtzqswxsFAkJI6DTmFooo6itc1GG6R0Ck0KhXZgaQY5FiiP25VI9m5rDHinpsoOBofo23JzKVLTGGqG9atv-8KJvuSNSJvTbul1WKpI5xPPCIt8o)

Detectron2 is a ground-up rewrite of Detectron that started with [maskrcnn-benchmark](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2Ffacebookresearch%2Fmaskrcnn-benchmark&h=AT3fIWNVW-NShn7kVKBGlA1kEgmvN2NFYEde8Ugq-irz1nGvVBPXWSSBPXHVCzZnzNjJgTucs0jMQW05oQpO8hL8gHWpR1FH78Qt6f5fd5nK3MZ5hwtlStyizENXzdl6ilh_oXtMXpkZ5Vv1cLU7RilWCCM). The platform is now implemented in [PyTorch](https://l.facebook.com/l.php?u=https%3A%2F%2Fpytorch.org%2F&h=AT0l8fOWJ7ICDQJxOPVgjglvzJP0datNGXNMAlb0vpeIu6lIldQ9Yk97Go2MyYuSqmID4ziyisI6as7GJfkwxnSPpAn_tsfYVyHoSkcOvBVxF3aYqAtFsRRFoazZrEAuu5o2jg7TvYzcjePka95k22VZUvw). With a new, more modular design, Detectron2 is flexible and extensible, and able to provide fast training on single or multiple GPU servers. Detectron2 includes high-quality implementations of state-of-the-art object detection algorithms, including [DensePose](https://l.facebook.com/l.php?u=http%3A%2F%2Fdensepose.org%2F&h=AT1M54KrlGPJAtIzPyMmMAutre-RRo1286hUkGqcc14NdiNnG9gZ84L6ZBfTCe3hY2C5ZqOGvOqL9Y3P1XJFaodbGPQxeG4lLC0lvs08Hddshv2dTkLBx3DdYAP4wrRPwYoXWoCAOkZaA4_0MJAR_wuPk0I), [panoptic feature pyramid networks](https://ai.facebook.com/blog/improving-scene-understanding-through-panoptic-segmentation/), and numerous variants of the pioneering [Mask R-CNN](https://l.facebook.com/l.php?u=https%3A%2F%2Fresearch.fb.com%2Fpublications%2Fmask-r-cnn%2F&h=AT351kUpSTSwzn3KyWd1BSCImCZFDyUiOEhsRLLcJyYOWzRTHRLi04OnJu6N2cBj4x3XJQYHjIRcdr2BsjfhSurODdAHIaeNniB_A45bUUnNzck-6OF7JUU6XZSMD1cg07KzzSaPpYpAnNqftP-iuzYM6x4) model family also developed by FAIR. Its extensible design makes it easy to implement cutting-edge research projects without having to fork the entire codebase.

We built Detectron2 to meet the research needs of Facebook AI and to provide the foundation for object detection in production use cases at Facebook. We are now using Detectron2 to rapidly design and train the next-generation pose detection models that [power Smart Camera](https://ai.facebook.com/blog/smart-camera-portal-advances/), the AI camera system in Facebook’s Portal video-calling devices. By relying on Detectron2 as the unified library for object detection across research and production use cases, we are able to rapidly move research ideas into production models that are deployed at scale.

Something Went Wrong

We're having trouble playing this video.

This video shows different types of object detection tasks done with Detectron2.

We’re sharing Detectron2 because open source research platforms are critical to the rapid advances in AI made by the entire community, including researchers and practitioners in academia and industry. We hope that releasing Detectron2 will continue to accelerate progress in the area of object detection and segmentation.

Improvements in Detectron2
--------------------------

PyTorch: The original Detectron was implemented in Caffe2. PyTorch provides a more intuitive imperative programming model that allows researchers and practitioners to iterate more rapidly on model design and experiments. Because we’ve rewritten Detectron2 from scratch in PyTorch, users can now benefit from PyTorch’s approach to deep learning as well as the large and active community that continually improves PyTorch

Modular, extensible design: In Detectron2, we’ve introduced a modular design that allows users to plug custom module implementations into almost any part of an object detection system. This means that many new research projects can be written in hundreds of lines of code with a clean separation between the core Detectron2 library and the novel research implementation. We continue to refine the modular, extensible design by implementing new models and discovering new ways in which we can make Detectron2 more flexible.

Something Went Wrong

We're having trouble playing this video.

This graphic shows how Detectron2’s modular design allows users to take an image and easily switch to custom backbones, insert different prediction heads, and perform panoptic segmentation.

New models and features: Detectron2 includes all the models that were available in the original Detectron, such as Faster R-CNN, Mask R-CNN, RetinaNet, and DensePose. It also features several new models, including Cascade R-CNN, Panoptic FPN, and TensorMask, and we will continue to add more algorithms. We’ve also added features such as synchronous Batch Norm and support for new datasets like [LVIS](https://l.facebook.com/l.php?u=https%3A%2F%2Fresearch.fb.com%2Fpublications%2Flvis-a-dataset-for-large-vocabulary-instance-segmentation%2F&h=AT1z4tuj3dbaCMkOrIgnGVk0Q8guJlnx3z4tlGJ4fHIunGQPyLXP8OE1SQLRgiNB6TQ7wJDbiiZVdjGgKhQ2tnJBp0FpZ944Myhru6ZzOBBPMW-oG_grlo3DkZAIXxN-Tcb1J_tEnM15vLV_5pbs4xT2Fd8).

New tasks: Detectron2 supports a range of tasks related to object detection. Like the original Detectron, it supports object detection with boxes and instance segmentation masks, as well as human pose prediction. Beyond that, Detectron2 adds support for semantic segmentation and panoptic segmentation, a task that combines both semantic and instance segmentation.

Implementation quality: Rewriting Detectron2 from the ground up allowed us to revisit low-level design decisions and address several implementation issues in the original Detectron.

Speed and scalability: By moving the entire training pipeline to GPU, we were able to make Detectron2 faster than the original Detectron for a variety of standard models. Additionally, distributing training to multiple GPU servers is now easy, making it much simpler to scale training to very large data sets.

Detectron2go: Facebook AI’s computer vision engineers have implemented an additional software layer, Detectron2go, to make it easier to deploy advanced new models to production. These features include standard training workflows with in-house data sets, network quantization, and model conversion to optimized formats for cloud and mobile deployment.

Accelerating AI research and engineering for all
------------------------------------------------

Progress in AI is a community effort that includes individuals, large and small labs, academia, and industry. The problems we aim to solve go far beyond what any individual or group can achieve in isolation. For this reason, we believe strongly in sharing code that enables reproducible research, rapid experimentation, and development of new ideas. By releasing Detectron2, we hope to further accelerate research in the areas of object detection, segmentation, and human pose understanding.

New research starts with understanding, reproducing, and verifying previous results in the literature. With Detectron2, we aim to provide high-quality reference implementations for many state-of-the-art algorithms in order to democratize this phase of the research process.

The library’s modular design also enables researchers to implement new projects with clean separation from standard detection library functionality. As an example, Mesh R-CNN, FAIR’s recent work on predicting per-object instance 3D meshes from 2D images, was developed in Detectron2. Detectron2’s modular design enabled the researchers to easily extend Mask R-CNN to work with complex data structures representing 3D meshes, integrate new data sets, and design novel evaluation metrics.

Detectron2 can be easily shared between research-first use cases and production-oriented use cases. Because the library is built in PyTorch, new models can be implemented rapidly and then transferred to production.

Building technology to enable the next CV breakthroughs
-------------------------------------------------------

Our goal with Detectron2 is to support the wide range of cutting-edge object detection and segmentations models available today, but also to serve the ever-shifting landscape of cutting-edge research. Novel research by definition involves inventing new models that will likely break the design assumptions of existing models. This meant building software to support a nearly unspecifiable set of requirements while also making it as simple as possible to use. We expect to continually develop and refine Detectron2 in service of this objective. With the library now available to the wider ML community, we look forward to collaborating with and learning from others as we push the limits of what’s possible in computer vision systems.

_**We’d like to acknowledge the contributions of Xinlei Chen, Jing Huang, Vasil Khalidov, Yanghao Li, Jon Morton, Sam Pepose, Ria Verma, Yanghan Wang, Peizhao Zhang, and others who helped build Detectron2.**_

Written by
----------

Research Engineering Manager

  
  
from Hacker News https://ift.tt/2OYTM4N