---
title: 'Extract voice, piano, drums, etc. from any music track using Machine Learning'
date: 2019-11-03T01:39:00+01:00
draft: false
---

[![](https://github.com/deezer/spleeter/raw/master/images/spleeter_logo.png)](https://github.com/deezer/spleeter/raw/master/images/spleeter_logo.png)

[![PyPI version](https://camo.githubusercontent.com/384c6765b84c81f0c37f7f1504ef7d512a97ee9f/68747470733a2f2f62616467652e667572792e696f2f70792f73706c65657465722e737667)](https://badge.fury.io/py/spleeter) [![Conda](https://camo.githubusercontent.com/220130f46de51248362c8b4643e71243fe88dc3e/68747470733a2f2f696d672e736869656c64732e696f2f636f6e64612f646e2f636f6e64612d666f7267652f73706c6565746572)](https://camo.githubusercontent.com/220130f46de51248362c8b4643e71243fe88dc3e/68747470733a2f2f696d672e736869656c64732e696f2f636f6e64612f646e2f636f6e64612d666f7267652f73706c6565746572) [![PyPI - Python Version](https://camo.githubusercontent.com/b20de8e30b90fda67073582722d7cf1b26ffa3e2/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f73706c6565746572)](https://camo.githubusercontent.com/b20de8e30b90fda67073582722d7cf1b26ffa3e2/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f73706c6565746572)

[](https://github.com/deezer/spleeter#about)About
-------------------------------------------------

**Spleeter** is the [Deezer](https://www.deezer.com/) source separation library with pretrained models written in [Python](https://www.python.org/) and uses [Tensorflow](https://tensorflow.org/). It makes it easy to train source separation model (assuming you have a dataset of isolated sources), and provides already trained state of the art model for performing various flavour of separation :

*   Vocals (singing voice) / accompaniment separation ([2 stems](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-2stems-model))
*   Vocals / drums / bass / other separation ([4 stems](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-4stems-model))
*   Vocals / drums / bass / piano / other separation ([5 stems](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-5stems-model))

2 stems and 4 stems models have state of the art performances on the [musdb](https://sigsep.github.io/datasets/musdb.html) dataset. **Spleeter** is also very fast as it can perform separation of audio files to 4 stems 100x faster than real-time when run on a GPU.

We designed **Spleeter** so you can use it straight from [command line](https://github.com/deezer/spleeter/wiki/2.-Getting-started#usage) as well as directly in your own development pipeline as a [Python library](https://github.com/deezer/spleeter/wiki/4.-API-Reference#separator). It can be installed with [Conda](https://github.com/deezer/spleeter/wiki/1.-Installation#using-conda), with [pip](https://github.com/deezer/spleeter/wiki/1.-Installation#using-pip) or be used with [Docker](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-docker-image).

[](https://github.com/deezer/spleeter#quick-start)Quick start
-------------------------------------------------------------

Want to try it out ? Just clone the repository and install a [Conda](https://github.com/deezer/spleeter/wiki/1.-Installation#using-conda) environment to start separating audio file as follows:

```
git clone https://github.com/Deezer/spleeter conda env create -f spleeter/conda/spleeter-cpu.yaml conda activate spleeter-cpu spleeter separate -i spleeter/audio\_example.mp3 -p spleeter:2stems -o output
```

You should get two separated audio files (`vocals.wav` and `accompaniment.wav`) in the `output/audio_example` folder.

For a more detailed documentation, please check the [repository wiki](https://github.com/deezer/spleeter/wiki)

[](https://github.com/deezer/spleeter#reference)Reference
---------------------------------------------------------

If you use **Spleeter** in your work, please cite:

```
@misc{spleeter2019, title\={Spleeter: A Fast And State-of-the Art Music Source Separation Tool With Pre-trained Models}, author\={Romain Hennequin and Anis Khlif and Felix Voituret and Manuel Moussallam}, howpublished\={Late-Breaking/Demo ISMIR 2019}, month\={November}, year\={2019} }
```

[](https://github.com/deezer/spleeter#license)License
-----------------------------------------------------

The code of **Spleeter** is MIT-licensed.

[](https://github.com/deezer/spleeter#note)Note
-----------------------------------------------

This repository include a demo audio file `audio_example.mp3` which is an excerpt from Slow Motion Dream by Steven M Bryant (c) copyright 2011 Licensed under a Creative Commons Attribution (3.0) license. [http://dig.ccmixter.org/files/stevieb357/34740](http://dig.ccmixter.org/files/stevieb357/34740) Ft: CSoul,Alex Beroza & Robert Siekawitch

  
  
from Hacker News https://ift.tt/2ppdjAS