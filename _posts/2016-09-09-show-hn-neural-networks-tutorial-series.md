---
title: 'Show HN: Neural networks tutorial series with code'
date: 2020-01-04T03:06:00+01:00
draft: false
---

[](https://github.com/gokadin/ai-simplest-network#simplest-artificial-neural-network)Simplest artificial neural network
=======================================================================================================================

This is the simplest artificial neural network possible explained and demonstrated.

[](https://github.com/gokadin/ai-simplest-network#this-is-part-1-of-a-series-of-github-repos-on-neural-networks)This is part 1 of a series of github repos on neural networks
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[](https://github.com/gokadin/ai-simplest-network#table-of-contents)Table of Contents
-------------------------------------------------------------------------------------

[](https://github.com/gokadin/ai-simplest-network#theory)Theory
---------------------------------------------------------------

### [](https://github.com/gokadin/ai-simplest-network#mimicking-neurons)Mimicking neurons

Artificial neural networks are inspired by the brain by having interconnected artificial neurons store patterns and communicate with each other. The simplest form of an artificial neuron has one or multiple inputs [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/9fc20fb1d3825674c6a279cb0d5ca636.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/9fc20fb1d3825674c6a279cb0d5ca636.svg?invert_in_darkmode&sanitize=true) each having a specific weight [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/c2a29561d89e139b3c7bffe51570c3ce.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/c2a29561d89e139b3c7bffe51570c3ce.svg?invert_in_darkmode&sanitize=true) and one output [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true).

[![alt text](https://github.com/gokadin/ai-simplest-network/raw/master/readme-images/perceptron.jpg)](https://github.com/gokadin/ai-simplest-network/blob/master/readme-images/perceptron.jpg)

At the simplest level, the output is the sum of its inputs times its weights.

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/c2d2775d67e954682fac686e557baed2.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/c2d2775d67e954682fac686e557baed2.svg?invert_in_darkmode&sanitize=true)

### [](https://github.com/gokadin/ai-simplest-network#a-simple-example)A simple example

Say we have a network with two inputs [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/f9b6dcc9279f659321ac3e1098b0ba4f.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/f9b6dcc9279f659321ac3e1098b0ba4f.svg?invert_in_darkmode&sanitize=true) and [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/bf84a893effff44b6d014b2b60460585.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/bf84a893effff44b6d014b2b60460585.svg?invert_in_darkmode&sanitize=true) and two weights [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true) and [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/f7eb0e840408d84a0c156d6efb611f3e.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/f7eb0e840408d84a0c156d6efb611f3e.svg?invert_in_darkmode&sanitize=true).

The idea is to adjust the weights in such a way that the given inputs produce the desired output.

Weights are normally initialized randomly since we can't know their optimal value ahead of time, however for simplicity we will initialize them both with [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/f58ed17486d1735419372f2b7d091779.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/f58ed17486d1735419372f2b7d091779.svg?invert_in_darkmode&sanitize=true).

[![alt text](https://github.com/gokadin/ai-simplest-network/raw/master/readme-images/perceptron-example.jpg)](https://github.com/gokadin/ai-simplest-network/blob/master/readme-images/perceptron-example.jpg)

Then the output [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true) will be

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/48c4f6073c4655b74cebf396493c9228.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/48c4f6073c4655b74cebf396493c9228.svg?invert_in_darkmode&sanitize=true)

### [](https://github.com/gokadin/ai-simplest-network#the-error)The error

If the output [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true) doesn't match the expected result, then we have an error.  
For example, if we wanted to get an expected output of [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/ad35a4143e0a34d97d3abc63c4dc81a3.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/ad35a4143e0a34d97d3abc63c4dc81a3.svg?invert_in_darkmode&sanitize=true) then we would have a difference of

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/c744817f1f470ba09c3750aadef1c2a9.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/c744817f1f470ba09c3750aadef1c2a9.svg?invert_in_darkmode&sanitize=true)

The most common way to measure the error is to use the square difference:

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/215d8df8edc921e2d5c6c45e3cf05508.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/215d8df8edc921e2d5c6c45e3cf05508.svg?invert_in_darkmode&sanitize=true)

If we had multiple associations of inputs and expected outputs, then the error becomes the sum of each association.

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/56def9cd4b32408db97f6999c6ba45ca.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/56def9cd4b32408db97f6999c6ba45ca.svg?invert_in_darkmode&sanitize=true)

To rectify the error, we would need to adjust the weights in a way that the actual output matches the expected output. In our example, lowering [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true) from [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/f58ed17486d1735419372f2b7d091779.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/f58ed17486d1735419372f2b7d091779.svg?invert_in_darkmode&sanitize=true) to [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/cde2d598001a947a6afd044a43d15629.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/cde2d598001a947a6afd044a43d15629.svg?invert_in_darkmode&sanitize=true) would do the trick, since

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/e6f831d1a270623d0d7f7ed67ad50360.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/e6f831d1a270623d0d7f7ed67ad50360.svg?invert_in_darkmode&sanitize=true)

However, in order to adjust the weights of our neural networks for many different inputs and expected outputs, we need a _learning algorithm_.

### [](https://github.com/gokadin/ai-simplest-network#gradient-descent)Gradient descent

The idea is to use the error in order to adjust each weight so that the error is minimized.

##### [](https://github.com/gokadin/ai-simplest-network#what-is-a-gradient)What is a gradient?

It's essentially a vector pointing to the direction of the steepest ascent of a function. The gradient is denoted with [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/47c28f1929c18f887420345e9225e08b.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/47c28f1929c18f887420345e9225e08b.svg?invert_in_darkmode&sanitize=true) and is simply the partial derivative of each variable of a function expressed as a vector.

Example for a two variable function:

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/b142e84f3f77e6dc3144eb723cd4510d.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/b142e84f3f77e6dc3144eb723cd4510d.svg?invert_in_darkmode&sanitize=true)

##### [](https://github.com/gokadin/ai-simplest-network#what-is-gradient-descent)What is gradient descent?

The _descent_ part simply means using the gradient to find the direction of steepest ascent of our function and then going in the opposite direction by a _small_ amount many times to find the function _global minimum_.

We use a constant called the **learning rate**, denoted with [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/7ccca27b5ccc533a2dd72dc6fa28ed84.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/7ccca27b5ccc533a2dd72dc6fa28ed84.svg?invert_in_darkmode&sanitize=true) to define how small of a step to take in that direction.

If [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/7ccca27b5ccc533a2dd72dc6fa28ed84.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/7ccca27b5ccc533a2dd72dc6fa28ed84.svg?invert_in_darkmode&sanitize=true) is too large, then we risk overshooting the function minimum, but if it's too low then the network will take longer to learn and we risk getting stuck in a local minimum.

[![alt text](https://github.com/gokadin/ai-simplest-network/raw/master/readme-images/gradient-descent.jpg)](https://github.com/gokadin/ai-simplest-network/blob/master/readme-images/gradient-descent.jpg)

##### [](https://github.com/gokadin/ai-simplest-network#gradient-descent-applied-to-our-example-network)Gradient descent applied to our example network

For our two weights [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true) and [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/f7eb0e840408d84a0c156d6efb611f3e.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/f7eb0e840408d84a0c156d6efb611f3e.svg?invert_in_darkmode&sanitize=true) we need to find the gradient of those weights with respect to the error function [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/84df98c65d88c6adf15d4645ffa25e47.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/84df98c65d88c6adf15d4645ffa25e47.svg?invert_in_darkmode&sanitize=true)

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/912be46ac0db99c8544f0800527d4b9f.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/912be46ac0db99c8544f0800527d4b9f.svg?invert_in_darkmode&sanitize=true)

For both [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/4b4518f1b7f0fb1347fa21506ebafb19.svg?invert_in_darkmode&sanitize=true) and [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/f7eb0e840408d84a0c156d6efb611f3e.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/f7eb0e840408d84a0c156d6efb611f3e.svg?invert_in_darkmode&sanitize=true), we can find the gradient by using the chain rule

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/94bed65fa8ab5f8d63836d674b61da83.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/94bed65fa8ab5f8d63836d674b61da83.svg?invert_in_darkmode&sanitize=true)

From now on we will denote the [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/d0a8416652c9aafee9f239948c2cd2e4.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/d0a8416652c9aafee9f239948c2cd2e4.svg?invert_in_darkmode&sanitize=true) as the [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/38f1e2a089e53d5c990a82f284948953.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/38f1e2a089e53d5c990a82f284948953.svg?invert_in_darkmode&sanitize=true) term.

Once we have the gradient, we can update our weights

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/f46613c78403dce8eed0b6093ff36d28.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/f46613c78403dce8eed0b6093ff36d28.svg?invert_in_darkmode&sanitize=true)

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/223d39de0113b6136f26962ed907c8aa.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/223d39de0113b6136f26962ed907c8aa.svg?invert_in_darkmode&sanitize=true)

And we repeat this process until the error is approximately 0​.

[](https://github.com/gokadin/ai-simplest-network#code-example)Code example
---------------------------------------------------------------------------

The included example teaches the following dataset to a neural network with two inputs and one output using gradient descent:

[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/0cdd43e831c22b1560861b7a3e660010.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/0cdd43e831c22b1560861b7a3e660010.svg?invert_in_darkmode&sanitize=true)

Once learned, the network should output ~0​ when given two [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/034d0a6be0424bffe9a6e7ac9236c0f5.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/034d0a6be0424bffe9a6e7ac9236c0f5.svg?invert_in_darkmode&sanitize=true)s and ~[![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/034d0a6be0424bffe9a6e7ac9236c0f5.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/034d0a6be0424bffe9a6e7ac9236c0f5.svg?invert_in_darkmode&sanitize=true) when given a [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/034d0a6be0424bffe9a6e7ac9236c0f5.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/034d0a6be0424bffe9a6e7ac9236c0f5.svg?invert_in_darkmode&sanitize=true) and a [![](https://github.com/gokadin/ai-simplest-network/raw/master/tex/29632a9bf827ce0200454dd32fc3be82.svg?invert_in_darkmode&sanitize=true)](https://github.com/gokadin/ai-simplest-network/blob/master/tex/29632a9bf827ce0200454dd32fc3be82.svg?invert_in_darkmode&sanitize=true).

[](https://github.com/gokadin/ai-simplest-network#references)References
-----------------------------------------------------------------------

*   Artificial intelligence engines by James V Stone (2019)

  
  
from Hacker News https://github.com/gokadin/ai-simplest-network