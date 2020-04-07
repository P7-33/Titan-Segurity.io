---
title: 'Tell a Story with AI using ‘Write With
Transformer’ #MachineLearning #ArtificialIntelligence #Create #transformers @jamieabrew @huggingface'
date: 2020-01-06T07:59:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/Screen-Shot-2020-01-05-at-8.02.21-PM-600x317.png)

From the ‘Write with Transformer’ web app at transformer.huggingface.co.

At the end of last year, [@jamieabrew](https://twitter.com/jamieabrew) [posted](https://medium.com/huggingface/how-to-write-with-transformer-5ee58d6f51fa) a “how-to” about writing with AI.  The guide walks you through using a web app, “[Write With Transformer](https://transformer.huggingface.co/)“, to generate text with AI. The web app is supported by the [Transformers library](https://github.com/huggingface/transformers) which is maintained by [Hugging Face](https://huggingface.co/). It contains some pretty impressive [transformers](https://towardsdatascience.com/transformers-141e32e69591) like [GPT-2](https://blog.adafruit.com/2019/11/25/the-gptrue-or-false-browser-extension-predicts-if-text-was-written-by-gpt-2-artificialintelligence-machinelearning-neuralnet-gpt2-thesofakillers/), [Distill-GPT2](https://github.com/huggingface/transformers/tree/master/examples/distillation), and [XLnet](https://arxiv.org/abs/1906.08237). In the app, each model has a brief description to guide users. Selecting a model opens up a web doc where you can paste/type a prompt OR hit TAB to get some model generated text. Check out the example below generated with Distill-GPT2:.

![](https://cdn-blog.adafruit.com/uploads/2020/01/Screen-Shot-2020-01-05-at-7.15.25-PM-e1578290806653-600x139.png)

Human entered prompt and Distill-GPT2 generated options (in box).

The web app also allows for some tuning of the model(s) which gives the user a bit more flexibility. “Model size” and “max time” control how big the model is and how much time it has to predict the next word(s) in the series. “Temperature” and “top-p” allow the user to determine the creativity of the AI. Check out the examples below from @jamieabrew’s post of conservative vs creative AIs:

> _Here’s a typical continuation at low temperature:_
> 
> ![](https://miro.medium.com/max/1696/1*TcA_7-2TkdKTAg_ipJ7dqw.png)
> 
> _And here’s one at high temperature:_
> 
> ![](https://miro.medium.com/max/2092/1*zNZ5NKU7xS2_kLB5zpYg9g.png)

If you’d like to try it out yourself you can head over to ‘[Write With Transformer](https://transformer.huggingface.co/)‘. If you’d like to learn more about Transformers check out this [post](https://medium.com/huggingface/how-to-build-a-state-of-the-art-conversational-ai-with-transfer-learning-2d818ac26313?) or take a look at the [Hugging Face](https://huggingface.co/) code on  [GitHub](https://github.com/huggingface).