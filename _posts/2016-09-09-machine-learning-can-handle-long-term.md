---
title: 'Machine Learning Can''t Handle Long-Term Time-Series Data'
date: 2020-01-05T07:08:00+01:00
draft: false
---

More precisely, today's machine learning (ML) systems cannot infer a fractal structure from time series data.

This may come as a surprise because computers seem like they can understand time series data. After all, aren't self-driving cars, AlphaStar and recurrent neural networks all evidence that today's ML can handle time series data?

Nope.

Self-Driving Cars
=================

![Uber's Self-Crashing Car](https://s3-us-west-2.amazonaws.com/www.lsusr.com/lesswrong/uber-self-crashing-car.jpg)

Self-driving cars use a hybrid of ML and procedural programming. ML (statistical programming) handles the low-level stuff like recognizing pedestrians. Procedural (nonstatistical) programming handles high-level stuff like navigation. The details of self-driving car software are trade secrets, but we can infer bits of Uber's architecture from the National Transportation Safety Board's report on Uber's self-crashing car as [summarized](https://www.lesswrong.com/posts/tTg4bn5rxHYqQJXhD/uber--driving-crash) by jkaufman.

> "If I'm not sure what it is, how can I remember what it was doing?" The car wasn't sure whether Herzberg and her bike were a "Vehicle", "Bicycle", "Unknown", or "Other", and kept switching between classifications. This shouldn't have been a major issue, except that with each switch it discarded past observations. Had the car maintained this history it would have seen that some sort of large object was progressing across the street on a collision course, and had plenty of time to stop.

We see here (above) is that the car throws away its past observations. Now let's take a look at a consequence of this.

> "If we see a problem, wait and hope it goes away". The car was programmed to, when it determined things were very wrong, wait one second. Literally. Not even gently apply the brakes. This is absolutely nuts. If your system has so many false alarms that you need to include this kind of hack to keep it from acting erratically, you are not ready to test on public roads.

Humans have to write ugly hacks like this when when your system isn't architected bottom-up to handle concepts like the flow of time. A machine learning system designed to handle time series data should never have human beings in the loop this low down the ladder of abstraction. In other words, Uber effectively uses a stateless ML system.

All you need to know when driving a car is the position of different objects and their velocities. You almost never need to know the past history of another driver or even yourself. There is no such thing as time to a stateless system. A stateless system cannot understand the concept of time. Stateless ML systems make sense when driving a car.

AlphaStar
=========

AlphaStar (DeepMind's _StarCraft II_ AI) is only a little more complicated than Uber's self-crashing car. It uses two neural networks. One network predicts the odds of winning and another network figures out which move to perform. This turns a time-series problem (what strategy to perform) into a two separate stateless[\[1\]](https://www.lesswrong.com/posts/N594EF44CZD2aGkSh/machine-learning-can-t-understand-long-term-time-series-data#fn-b393NaRun4c63BFpL-1) problems.

Comparisons between AlphaStar and human beings are fudged because _StarCraft II_ depends heavily on actions-per-minute (APM), the speed a player can perform actions. Humans wouldn't have a chance if AlphaStar was not artificially limited in the number of actions it would take. Games between humans and AlphaStar are only interesting because AlphaStar's actions are limited thereby giving humans a handicap.

Without the handicap, AlphaStar crushes human beings tactically. With the handicap, AlphaStar still crushes human beings tactically. Human beings can beat AlphaStar on occasion only because elite _StarCraft II_ players possess superior strategic understanding.

Most conspicuously, human beings know how to build walls with buildings. This requires a sequence of steps that don't generate a useful result until the last of them are completed. A wall is useless until the last building is put into place. AlphaStar (the red player in the image below) does not know how to build walls.

![AlphaStar (red) fails to build walls](https://s3-us-west-2.amazonaws.com/www.lsusr.com/lesswrong/alphastar-fails-to-build-walls.jpg)

With infinite computing power, AlphaStar could eventually figure this out. But we don't have infinite computing power. I don't think it's realistic to expect that AlphaStar will ever figure out how to build a wall with its current algorithms and realistic hardware limitations.

AlphaStar is good at tactics and bad at strategy. To state this more precisely, AlphaStar hits a computational cliff for understanding conceptually complex strategies when time horizons exceed the tactical level. Human brains are not limited in this way.

Recurrent Neural Networks (RNNs)
================================

RNNs are neural networks with a form of short-term memory. A newly-invented variant incorporates long short-term memory. In both cases, the RNN is trained with the standard backpropagation algorithm used by all artificial neural networks[\[2\]](https://www.lesswrong.com/posts/N594EF44CZD2aGkSh/machine-learning-can-t-understand-long-term-time-series-data#fn-b393NaRun4c63BFpL-2). The backpropagation algorithm works fine on short timescales but quickly breaks down when strategizing about longer timescales conceptually. The algorithm hits a computational cliff.

This is exactly the behavior we observe from AlphaStar. It's also the behavior we observe in natural language processing and music composition. ML can answer a simple question just fine but has trouble maintaining a conversation. ML can generate classical music [just fine](https://youtu.be/Emidxpkyk6o) but can't figure out the chorus/verse system used in rock & roll. That's because the former can be constructed stochastically without any hidden variables while the latter cannot.

The Road Ahead
==============

This brings us to my first law of artificial intelligence.

> Any algorithm that is not organized fractally will eventually hit a computational wall, and vice versa.
> 
> ―Lsusr's First Law of Artificial Intelligence

For a data structure to be organized fractally means you can cut a piece off and that piece will be a smaller version of the original dataset. For example, if you cut a sorted list in half then you will end up with two smaller sorted lists. (This is part of why quicksort works.) You don't have to cut a sorted list in exactly the middle to get two smaller sorted lists. The sorted list's fractal structure means can cut the list anywhere. In this way, a sorted list is organized fractally along one dimension. Others examples of fractal datastructures are heaps and trees.

Another fractal structure is a feed forward neural network (FFNN). FFNNs are organized fractally along two dimensions. There are two ways you can cut a neural network in half to get two smaller neural networks. The most obvious is to cut the network at half at a hidden layer. To do this, duplicate the hidden layer and then cut between the pair of duplicated layers. The less obvious way to cut a neural network is to slice between its input/output nodes.

Each dimension of fractality is a dimension the FFNN can scale indefinitely. FFNNs are good at scaling the number of input and output nodes they possess because a FFNN is structured fractally along this dimension (number of input/output nodes). FFNNs are good at scaling the complexity of processing they perform because a FFNN is structured fractally along this dimension too (number of hidden layers).

Much of the recent development in image recognition comes from these two dimensions of fracticality[\[3\]](https://www.lesswrong.com/posts/N594EF44CZD2aGkSh/machine-learning-can-t-understand-long-term-time-series-data#fn-b393NaRun4c63BFpL-3). Image recognition has a high number of input nodes (all the color channels of all the pixels in an image). FFNN can apply complex rules to this large space because of its fractal geometry in the number of hidden layers dimension.

FFNNs are stateless machines so feeding time series data into a FFNN doesn't make sense. RNNs can handle time series data, but they have no mechanism for organizing it fractally. Without a fractal structure in the time dimension, RNNs cannot generalize information from short time horizons to long time horizons. They therefore do not have enough data to formulate complex strategies on long time horizons.

If we could build a neural network fractally-organized in the time domain then it could generalize (apply transfer learning) from short time horizons to long time horizons. This turns a small data problem into an big data problem. Small data problems are hard. Big data problems are easy.

This is why I'm so interested in [Connectome-Specific Harmonic Waves](https://www.lesswrong.com/posts/Rf8Bf6Abke4YjpEdi/connectome-specific-harmonic-waves) (CSHW). The fractal equation of harmonic waves (Laplacian eigendecomposition) could answer the problem of how to structure a neural network fractally in the time domain.

* * *

1.  AlphaStar does contain one bit of time-series comprehension. It can predict the actions of enemy units hidden by fog of war. I'm choosing to ignore this on the grounds it isn't an especially difficult problem. [↩︎](https://www.lesswrong.com/posts/N594EF44CZD2aGkSh/machine-learning-can-t-understand-long-term-time-series-data#fnref-b393NaRun4c63BFpL-1)
    
2.  The human brain lacks a known biological mechanism for performing the backpropagation algorithm used by artificial neural networks. Therefore biological neural networks probability use a different equation for gradient ascent. [↩︎](https://www.lesswrong.com/posts/N594EF44CZD2aGkSh/machine-learning-can-t-understand-long-term-time-series-data#fnref-b393NaRun4c63BFpL-2)
    
3.  Progress also comes from the application of parallel GPUs to massive datasets, but scaling int this way wouldn't be viable mathematically without the two-dimensional fractal structure of FFNNs. [↩︎](https://www.lesswrong.com/posts/N594EF44CZD2aGkSh/machine-learning-can-t-understand-long-term-time-series-data#fnref-b393NaRun4c63BFpL-3)
    

  
  
from Hacker News https://ift.tt/39yBX4a