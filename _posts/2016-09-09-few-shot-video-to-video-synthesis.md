---
title: 'Few-Shot Video-to-Video Synthesis'
date: 2019-11-05T01:59:00+01:00
draft: false
---

Few-shot Video-to-Video Synthesis
=================================

NVIDIA Corporation
------------------

[![](https://nvlabs.github.io/few-shot-vid2vid/web_gifs/illustration.gif)](https://nvlabs.github.io/few-shot-vid2vid/images/teaser.gif)

Abstract
--------

Video-to-video synthesis (vid2vid) aims at converting an input semantic video, such as videos of human poses or segmentation masks, to an output photorealistic video. While the state-of-the-art of vid2vid has advanced significantly, existing approaches share two major limitations. First, they are data-hungry. Numerous images of a target human subject or a scene are required for training. Second, a learned model has limited generalization capability. A pose-to-human vid2vid model can only synthesize poses of the single person in the training set. It does not generalize to other humans that are not in the training set. To address the limitations, we propose a few-shot vid2vid framework, which learns to synthesize videos of previously unseen subjects or scenes by leveraging few example images of the target at test time. Our model achieves this few-shot generalization capability via a novel network weight generation module utilizing an attention mechanism. We conduct extensive experimental validations with comparisons to strong baselines using several large-scale video datasets including human-dancing videos, talking-head videos, and street-scene videos. The experimental results verify the effectiveness of the proposed framework in addressing the two limitations of existing vid2vid approaches.

[![paper thumbnail](https://nvlabs.github.io/few-shot-vid2vid/images/paper_thumbnail.jpg)](https://arxiv.org/abs/1910.12713)

Paper
-----

[arXiv](https://arxiv.org/abs/1910.12713), 2019.

Citation
--------

Ting-Chun Wang, Ming-Yu Liu, Andrew Tao, Guilin Liu, Jan Kautz, and Bryan Catanzaro. "Few-shot Video-to-Video Synthesis", in NeurIPS, 2019. [Bibtex](https://nvlabs.github.io/few-shot-vid2vid/Bibtex.txt)

Our Example Results
===================

Human Dancing Videos
====================

Talking Head Videos
===================

Street View Videos
==================

VIDEO

Acknowledgement
---------------

We thank Karan Sapra for generating the segmentation maps for us.

Citation
--------

If you find this useful for your research, please use the following.  
@inproceedings{wang2019fewshotvid2vid,  
title={Few-shot Video-to-Video Synthesis},  
author={Ting-Chun Wang and Ming-Yu Liu and Andrew Tao and Guilin Liu and Jan Kautz and Bryan Catanzaro},  
booktitle={Advances in Neural Information Processing Systems (NeurIPS)},  
year={2019}  
}

  
  
from Hacker News https://ift.tt/2PpUIzo