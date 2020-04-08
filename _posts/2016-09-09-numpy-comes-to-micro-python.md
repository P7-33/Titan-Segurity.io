---
title: 'Numpy Comes To Micro Python'
date: 2019-10-30T03:02:00+01:00
draft: false
---

\[Zoltán\] sends in his very interesting implementation of a [NumPy-like library for micropython called ulab.](https://github.com/v923z/micropython-ulab)

He had a project in MicroPython that needed a very fast FFT on a micro controller, and was looking at all of the options when it occurred to him that a more structured approach like the one we all know and love in CPython would be possible on a micro controller too. He thus ended up with a python library that could do the FFT 50 times faster than the the pure Python implementation while providing all the readability and ease of use benefits that NumPy and Python together provide.

As cool as this is, what’s even cooler is that \[Zoltan\] wrote [excellent documentation on the use of the library](https://micropython-ulab.readthedocs.io/en/latest/). Not only can this documentation be used for his library, but it provides many excellent examples of how to use MicroPython itself.

We really recommend that fans of Python and NumPy give this one a look over!

  
  
from Hackaday https://ift.tt/2Prx0CJ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)