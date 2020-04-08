---
title: 'An Algorithm For De-Biasing AI Systems'
date: 2019-10-22T03:11:00+01:00
draft: false
---

A fundamental truth about AI systems is that training the system with biased data creates biased results. This can be especially dangerous when the systems are being used to predict crime or select sentences for criminals, since they can hinge on unrelated traits such as race or gender to make determinations.

![](https://hackaday.com/wp-content/uploads/2019/10/debiasing.gif?w=302)

A group of researchers from the Massachusetts Institute of Technology (MIT) CSAIL is working on a solution to “de-bias” data by resampling it to be more balanced. The [paper](https://dl.acm.org/citation.cfm?doid=3306618.3314243) published by PhD students \[Alexander Amini\] and \[Ava Soleimany\] describes an algorithm that can learn a specific task – such as facial recognition – as well as the structure of the training data, which allows it to identify and minimize any hidden biases.

Testing showed that the algorithm minimized “categorical bias” by over 60% compared against other widely cited facial detection models, all while maintaining the same precision of detection. This figure was maintained when the team evaluated a facial-image dataset from the [Algorithmic Justice League](http://www.google.com/url?q=http%3A%2F%2Ficm-tracking.meltwater.com%2Flink.php%3FDynEngagement%3Dtrue%26H%3DbtYXC68syxnIlVIaW0qBweEUHWPFwuN5EgnqFgPj0oiC1OMl9zi1Rm5cLnf5FaHSIWjGgRC8gwJiNfWjv7EgiJXXu%252B1ZiFgV%252BBiMCBAV3KlBqBVLVWZOxw%253D%253D%26G%3D0%26R%3Dhttps%253A%252F%252Fwww.ajlunited.org%252Fgender-shades%26I%3D20190127220005.0000002ce5db%2540mail6-113-ussnn1%26X%3DMHwxMDQ2NzU4OjVjNGUwZjU3MWNmNjEwYTZmNDM4Njg4Njs%253D%26S%3DUFv1IjGkQPXG9ti5w41H95rYSJfH4rESuOjEStaFqaw&sa=D&sntz=1&usg=AFQjCNE1H_3TyjIzwTn2axMHqCI3EUj74g), a spin-off group from the MIT Media Lab.

The team says that their algorithm would be particularly relevant for large datasets that can’t easily be vetted by a human, and can potentially rectify algorithms used in security, law enforcement, and other domains beyond facial detection.

  
  
from Hackaday https://ift.tt/2pLC2yX  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)