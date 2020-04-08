---
title: 'AllenNLP Interpret: A Framework for Explaining Predictions of NLP Models'
date: 2019-09-29T01:42:00+01:00
draft: false
---

AllenNLP Interpret:  
A Framework for Explaining Predictions of NLP Models
--------------------------------------------------------------------------

##### Eric Wallace, Jens Tuyls, Junlin Wang, Sanjay Subramanian,  
Matt Gardner, and Sameer Singh

  
EMNLP 2019 Demo

Despite constant advances and seemingly super-human performance on constrained domains, state-of-the-art models for NLP are imperfect. These imperfections, coupled with today's advances being driven by (seemingly black-box) neural models, leave researchers and practitioners scratching their heads asking, _why did my model make this prediction?_

We present AllenNLP Interpret, a toolkit built on top of AllenNLP for interactive model interpretations. The toolkit makes it easy to apply gradient-based **saliency maps** and **adversarial attacks** to _new models_, as well as develop _new interpretation methods_. AllenNLP interpret contains three components: a suite of interpretation techniques applicable to most models, APIs for developing new interpretation methods (e.g., APIs to obtain input gradients), and reusable front-end components for visualizing the interpretation results.

This page presents links to:

*   [Paper](https://arxiv.org/abs/1909.09251) describing the framework, the technical implementation details, and showing some example use cases.
*   Live demos for various models and tasks, such as
*   Tutorials for interpreting any [model of your choice](https://github.com/allenai/allennlp-demo#contributing-a-new-model-to-the-demo), and addding [a new interpretation method](https://github.com/allenai/allennlp-demo#adding-a-new-interpretation-method).
*   [Code](https://github.com/allenai/allennlp/tree/master/allennlp/interpret) for interpreting/attacking models and visualizing the results in the demo (e.g., [sentiment analysis](https://github.com/allenai/allennlp-demo/blob/master/demo/src/components/demos/SentimentAnalysis.js)).

_Citation:_

```
 @inproceedings{Wallace2019AllenNLP, Author = {Eric Wallace and Jens Tuyls and Junlin Wang and Sanjay Subramanian and Matt Gardner and Sameer Singh}, Booktitle = {Empirical Methods in Natural Language Processing}, Year = {2019}, Title = { {AllenNLP Interpret}: A Framework for Explaining Predictions of {NLP} Models}} 
```

  
  
from Hacker News https://ift.tt/30kWbN2