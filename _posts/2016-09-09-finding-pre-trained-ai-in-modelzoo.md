---
title: 'Finding Pre-Trained AI In A Modelzoo Using Python'
date: 2019-10-09T03:02:00+01:00
draft: false
---

Training a machine learning model is not a task for mere mortals, as it takes a lot of time or computing power to do so. Fortunately there are pre-trained models out there that one can use, and \[Max Bridgland\] decided it would be a good idea to write [a python module to find and view such models using the command line](https://github.com/M4cs/EasyModels).

For the uninitiated, Modelzoo is a place where you can find open source deep learning code and pre-trained models. \[Max\] taps into the (undocumented) API and allows a user to find and view models directly. When you run a utility, it goes online and retrieves the categories and then details of the available models. From then on, the user can select a model and the application will simply open the corresponding GitHub repository. Sounds simple but it has a lot of value since the code is designed to be extendable so that users working on such projects may automate the downloading part as well.

We have seen [projects with machine learning used to detect humans](https://hackaday.com/2019/01/14/project-shows-how-to-use-machine-learning-to-detect-pedestrians/), and with AI trending community tools such as this one help beginners get started even faster.

  
  
from Hackaday https://ift.tt/31YEwrX  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)