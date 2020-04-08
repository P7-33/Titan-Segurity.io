---
title: 'Show HN: Imagededup – Finding duplicate images made easy'
date: 2019-10-07T03:02:00+01:00
draft: false
---

[](https://github.com/idealo/imagededup#image-deduplicator-imagededup)Image Deduplicator (imagededup)
=====================================================================================================

[![Build Status](https://camo.githubusercontent.com/a755b323568a2de1547b6ab400f1a844ff7cc02d/68747470733a2f2f7472617669732d63692e6f72672f696465616c6f2f696d61676564656475702e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/idealo/imagededup) [![Docs](https://camo.githubusercontent.com/d899216b558e71ce5e752afda08b23044fd1da27/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f646f63732d6f6e6c696e652d627269676874677265656e)](https://idealo.github.io/imagededup/) [![codecov](https://camo.githubusercontent.com/95183d7d5e4f9d46423ddaadd2887403643ed6a4/68747470733a2f2f636f6465636f762e696f2f67682f696465616c6f2f696d61676564656475702f6272616e63682f6d61737465722f67726170682f62616467652e737667)](https://codecov.io/gh/idealo/imagededup) [![PyPI Version](https://camo.githubusercontent.com/f22600aa79ff6c1614b2d8bc4ca835846e4c3eb7/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f696d6167656465647570)](https://pypi.org/project/imagededup/) [![License](https://camo.githubusercontent.com/8051e9938a1ab39cf002818dfceb6b6092f34d68/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d417061636865253230322e302d626c75652e737667)](https://github.com/idealo/imagededup/blob/master/LICENSE)

imagededup is a python package that simplifies the task of finding **exact** and **near duplicates** in an image collection.

[![](https://github.com/idealo/imagededup/raw/master/readme_figures/mona_lisa.png)](https://github.com/idealo/imagededup/blob/master/readme_figures/mona_lisa.png)

This package provides functionality to make use of hashing algorithms that are particularly good at finding exact duplicates as well as convolutional neural networks which are also adept at finding near duplicates. An evaluation framework is also provided to judge the quality of deduplication for a given dataset.

Following details the functionality provided by the package:

*   Finding duplicates in a directory using one of the following algorithms:
*   Generation of encodings for images using one of the above stated algorithms.
*   Framework to evaluate effectiveness of deduplication given a ground truth mapping.
*   Plotting duplicates found for a given image file.

Detailed documentation for the package can be found at: [https://idealo.github.io/imagededup/](https://idealo.github.io/imagededup/)

imagededup is compatible with Python 3.6 and is distributed under the Apache 2.0 license.

[](https://github.com/idealo/imagededup#contents)Contents
---------------------------------------------------------

[](https://github.com/idealo/imagededup#installation)Installation
-----------------------------------------------------------------

There are two ways to install imagededup:

*   Install imagededup from PyPI (recommended):

```
pip install imagededup 
```

⚠️**Note**: imagededup comes with TensorFlow CPU-only support by default. If you have GPUs, you should rather install the TensorFlow version with GPU support especially when you use CNN to find duplicates. It's way faster. See the [TensorFlow guide](https://www.tensorflow.org/install/gpu) for more details on how to install it.

*   Install imagededup from the GitHub source:

```
git clone https://github.com/idealo/imagededup.git cd imagededup python setup.py install 
```

[](https://github.com/idealo/imagededup#quick-start)Quick start
---------------------------------------------------------------

In order to find duplicates in an image directory using perceptual hashing, following workflow can be used:

*   Import perceptual hashing method

```
from imagededup.methods import PHash phasher \= PHash()
```

*   Generate encodings for all images in an image directory

```
encodings \= phasher.encode\_images(image\_dir\='path/to/image/directory')
```

*   Find duplicates using the generated encodings

```
duplicates \= phasher.find\_duplicates(encoding\_map\=encodings)
```

*   Plot duplicates obtained for a given file (eg: 'ukbench00120.jpg') using the duplicates dictionary

```
from imagededup.utils import plot\_duplicates plot\_duplicates(image\_dir\='path/to/image/directory', duplicate\_map\=duplicates, filename\='ukbench00120.jpg')
```

The output looks as below:

[![figs](https://github.com/idealo/imagededup/raw/master/readme_figures/plot_dups.png)](https://github.com/idealo/imagededup/blob/master/readme_figures/plot_dups.png)

The complete code for the workflow is:

```
from imagededup.methods import PHash phasher \= PHash() # Generate encodings for all images in an image directory encodings \= phasher.encode\_images(image\_dir\='path/to/image/directory') # Find duplicates using the generated encodings duplicates \= phasher.find\_duplicates(encoding\_map\=encodings) # plot duplicates obtained for a given file using the duplicates dictionary from imagededup.utils import plot\_duplicates plot\_duplicates(image\_dir\='path/to/image/directory', duplicate\_map\=duplicates, filename\='ukbench00120.jpg')
```

For more examples, refer [this](https://github.com/idealo/imagededup/tree/master/examples) part of the repository.

For more detailed usage of the package functionality, refer: [https://idealo.github.io/imagededup/](https://idealo.github.io/imagededup/)

[](https://github.com/idealo/imagededup#contribute)Contribute
-------------------------------------------------------------

We welcome all kinds of contributions. See the [Contribution](https://github.com/idealo/imagededup/blob/master/CONTRIBUTING.md) guide for more details.

[](https://github.com/idealo/imagededup#citation)Citation
---------------------------------------------------------

Please cite Imagededup in your publications if this is useful for your research. Here is an example BibTeX entry:

```
@misc{idealods2019imagededup, title={Imagededup}, author={Tanuj Jain and Christopher Lennan and Zubin John and Dat Tran}, year={2019}, howpublished={\url{https://github.com/idealo/imagededup}}, } 
```

[](https://github.com/idealo/imagededup#maintainers)Maintainers
---------------------------------------------------------------

[](https://github.com/idealo/imagededup#copyright)Copyright
-----------------------------------------------------------

See [LICENSE](https://github.com/idealo/imagededup/blob/master/LICENSE) for details.

  
  
from Hacker News https://ift.tt/31MeNmJ