---
title: 'Hacking Neural Networks: A Short Introduction'
date: 2019-11-17T06:49:00+01:00
draft: false
---

![](https://repository-images.githubusercontent.com/215415332/2024c100-0810-11ea-967e-d3ca25f36581 "GitHub - Kayzaks/HackingNeuralNetworks: A small course on exploiting and defending neural networks")  

[](https://github.com/Kayzaks/HackingNeuralNetworks#hacking-neural-networks-a-short-introduction)Hacking Neural Networks: A Short Introduction
==============================================================================================================================================

**Disclaimer: This article and all the associated exercises are for educational purposes only.**

This is a short introduction on methods that use neural networks in an offensive manner (bug hunting, shellcode obfuscation, etc.) and how to exploit neural networks found in the wild (information extraction, malware injection, backdooring, etc.).

Most of the methods presented are accompanied by an exercise found in this repo. The full article can be found here in '[Article.pdf](https://github.com/Kayzaks/HackingNeuralNetworks/blob/master/Article.pdf)' or on arXiv (uploaded soon).

* * *

[](https://github.com/Kayzaks/HackingNeuralNetworks#setup)Setup
---------------------------------------------------------------

### [](https://github.com/Kayzaks/HackingNeuralNetworks#python-and-pip)Python and pip

Download and install Python3 and its package installer pip using a package manager or directly from the website [https://www.python.org/downloads/](https://www.python.org/downloads/).

### [](https://github.com/Kayzaks/HackingNeuralNetworks#editor)Editor

An editor is required to work with the code, preferably one that allows code highlighting for Python. Vim/Emacs will do. As a reference, all exercises were prepared using Visual Studio Code [https://code.visualstudio.com/docs/python/python-tutorial](https://code.visualstudio.com/docs/python/python-tutorial).

### [](https://github.com/Kayzaks/HackingNeuralNetworks#packages)Packages

*   **Keras**: Installing Keras can be tricky. We refer to the official installation guide at [https://keras.io/#installation](https://keras.io/#installation) and suggest TensorFlow as a backend (using the GPU-enabled version, if one is available on the machine).
*   **NumPy** and **SciPy**: NumPy and SciPy are excellent helper packages, which are used throughout all exercises. Following the official SciPy instructions should also install NumPy [https://www.scipy.org/install.html](https://www.scipy.org/install.html).
*   **PyCuda**: PyCuda is required for the GPU-based attack exercise. If no nVidia GPU is available on the machine, this can be skipped. [https://wiki.tiker.net/PyCuda/Installation](https://wiki.tiker.net/PyCuda/Installation)
*   **NLTK**: NLTK provides functionalities for natural language processing and is very helpful for some of the exercises. [https://www.nltk.org/install.html](https://www.nltk.org/install.html)

* * *

[](https://github.com/Kayzaks/HackingNeuralNetworks#the-exercises)The exercises
-------------------------------------------------------------------------------

*   _0 - Last Layer Attack_
*   _1 - Backdooring_
*   _2 - Extracting Information_
*   _3 - Brute Forcing_
*   _4 - Neural Overflow_
*   _5 - Malware Injection_
*   _6 - Neural Obfuscation_
*   _7 - Bug Hunting_
*   _8 - GPU Attack_

For instructions, please read the 'README.md' file in each of the exercise directories.

* * *

[](https://github.com/Kayzaks/HackingNeuralNetworks#what-else)What else?
------------------------------------------------------------------------

The neural networks found in the exercises are based on the examples provided by [keras](https://keras.io/).

Also check out Isao Takaesu's course on [Security and Machine Learning](https://github.com/13o-bbr-bbq/machine_learning_security/tree/master/Security_and_MachineLearning).

If you find that there are errors or missing references, feel free to make a PR or contact me.

  
  
from Hacker News https://ift.tt/35jkD0n