---
title: 'AI Competitions – What are they good
for? #AI #ArtificialIntelligence #MachineLearning #overfitting #underpowered #SOTA @DrLukeOR'
date: 2019-09-26T02:18:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/09/Screen-Shot-2019-09-25-at-4.36.55-PM-e1569454850983-590x480.png)

Keyboard object recognition with Tensorflow mobilenet\_v2\_1.0\_224 model from Adafruit’s interactive Colab notebook. image credit @minichre.

In a recent blog [post](https://lukeoakdenrayner.wordpress.com/2019/09/19/ai-competitions-dont-produce-useful-models/) Luke Oakden-Rayner (@DrLukeOR) discusses some drawbacks of the AI-competition approach to advancing machine learning. While most can agree AI-competitions are great for networking, recruiting and learning, @DrLukeOR is skeptical about the usefulness of the models that ‘win’ these competitions.  

> AI competitions are fun, community building, talent scouting, brand promoting, and attention grabbing. But competitions are not intended to develop useful models.

While slightly controversial, @DrLukeOR walks through several scenarios explaining this point of view. The summary is that evaluation of models to identify winning teams is statistically under-powered. This is primarily because test sets for model evaluation are too small to separate the vast majority of comepting models. Additionally, testing the model once or twice is insufficient to assess accuracy. The post also touches on competition models over-fitting data making it difficult to apply them to real world problems, specifically in medicine (@DrLukeOR’s field).

In response to this critique, [community members pointed out](https://twitter.com/DrLukeOR/status/1174682290544230405) that competitions foster the development of novel AI frameworks which push the field forward AND, as @DrLukeOR puts it, they’re ‘fun, community building, talent scouting, brand promoting…’ opportunities. I would add that the winners receive financial awards and bragging rights. That said, some restructuring in how models are assessed or how money is awarded (maybe to the top 10 models instead of the top model?) might help to assuage some of these concerns.

If you would like to learn more about AI competitions checkout this [post](https://towardsdatascience.com/top-competitive-data-science-platforms-other-than-kaggle-2995e9dad93c). If you want to play around with ImageNet predictions (and face off against the model) checkout this [project](https://cs.stanford.edu/people/karpathy/ilsvrc/) from Stanford. If you would like to learn more about over-fitting and AI competitions here are a few links from the community:

*   [Why rankings of biomedical image analysis competitions should be interpreted with care](https://www.nature.com/articles/s41467-018-07619-7)
*   [Do ImageNet Classifiers Generalize to ImageNet?](https://arxiv.org/abs/1902.10811)
*   [Do CIFAR-10 Classifiers Generalize to CIFAR-10?](https://arxiv.org/abs/1806.00451)
*   [Cold Case: The Lost MNIST Digits](https://arxiv.org/abs/1905.10498)
*   [Do Better ImageNet Models Transfer Better?](https://arxiv.org/abs/1805.08974)
*   [Measuring the tendency of CNNs to Learn Surface Statistical Regularities](https://arxiv.org/abs/1711.11561)

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2lQqAk1  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)