---
title: 'LTs[ice and Numpy: a Fast convolution filter #Python #EE'
date: 2019-12-18T15:37:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-58.png)

The [AcidBurbon blog](https://acidbourbon.wordpress.com/2019/12/04/ltspice-numpy-part-2-fast-convolution-filter/) takes [their study](https://acidbourbon.wordpress.com/2019/11/26/seamless-integration-of-ltspice-in-python-numpy-signal-processing/) of using the Python Numpy library with LTspice and [ups the ante](https://acidbourbon.wordpress.com/2019/12/04/ltspice-numpy-part-2-fast-convolution-filter/) with faster processing.

> In the [previous post](https://acidbourbon.wordpress.com/2019/11/26/seamless-integration-of-ltspice-in-python-numpy-signal-processing/) we discussed the possibility to use LTspice as a “plug in” into a Python/Numpy signal processing project. It works quite well: you send a numpy data vector to LTspice, let it run through the simulation and get back a numpy vector again. Everything is abstracted away nicely by the “[apply\_ltspice\_filter.py](https://github.com/acidbourbon/numpy_ltspice_filter/blob/master/apply_ltspice_filter.py)” module. So far so good.
> 
> There is just one problem: It is slow. Every time you process a new signal it takes a few seconds to call up Spice again and to funnel the data through a csv file. Not good for looooong signals or many signals that you want to process with the same filter.
> 
> If there only was a way to speed things up… How about I show you a YouTube video with the end results right here, so you stay interested:

See [the blog post](https://acidbourbon.wordpress.com/2019/12/04/ltspice-numpy-part-2-fast-convolution-filter/) for the full analysis.