---
title: 'A Python Numpy-like library written for
MicroPython #MicroPython #Numpy #Python #ulab @Hackaday'
date: 2019-10-30T16:43:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-106.png)

[Via Hackaday](https://hackaday.com/2019/10/29/numpy-comes-to-micro-python/), Zoltán Vörös has written ulab, a library for MicroPython which implements a subset of the Python Numpy array manipulation library.

> Zoltán had a project in MicroPython that needed a very fast FFT on a microcontroller, and was looking at all of the options when it occurred to him that a more structured approach like the one we all know and love in CPython would be possible on a microcontroller. He  ended up with a Python library that could do a FFT 50 times faster than the pure Python implementation, while providing all the readability and ease of use benefits that NumPy and Python together provide.
> 
> As cool as this is, what’s even cooler is that Zoltán wrote [excellent documentation on the use of the library](https://micropython-ulab.readthedocs.io/en/latest/). Not only can this documentation be used for his library, but it provides many excellent examples of how to use MicroPython itself.
> 
> We really recommend that fans of Python and NumPy give this one a look over!

The module is written in C, defines compact containers for numerical data, and is fast.

The code is available on [GitHub here](https://github.com/v923z/micropython-ulab) and released under an [MIT license](https://github.com/v923z/micropython-ulab/blob/master/LICENSE).

[See the Hackaday article here](https://hackaday.com/2019/10/29/numpy-comes-to-micro-python/).