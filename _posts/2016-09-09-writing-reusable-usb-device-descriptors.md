---
title: 'Writing reusable USB device descriptors with XML, Python, and C #USB'
date: 2020-01-14T20:37:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/Untitled-58.png)

[Kevin Cuzner points out](http://kevincuzner.com/2019/12/27/writing-reusable-usb-device-descriptors-with-some-xml-python-and-c/) that writing USB device descriptors time and again is rather annoying. A project ripe for a bit of automation.

> A recent project required me to reuse (once again) my USB HID device driver. This is my third or fourth project using this and I had started to find it annoying to need to hand-modify a heavily-commented, self-referencing array of uint8\_t’s. I figured there must be a better way, so I decided to try something different.
> 
> In this post I will present a script that turns this madness, which lives in a separate file.

The project goals:

*   Fully automatic computation of the wLength fields in descriptors.
*   Ad-hoc descriptor definition (i.e. I can specify descriptors throughout the code in many places).
*   Portable to all my machines without any dependencies other than Python. In general I use arch with python installed, so requesting that python be available isn’t a big deal for me.
*   Fully compatible with my existing USB driver structure (i.e. use the same usb\_descriptors table format).
*   Fairly agnostic of the actual USB driver used. The idea is that this can be used by other people who don’t want to be stuck with my USB driver implementation.

The script consists of a 800-ish line Python script (current version: [https://github.com/kcuzner/midi-fader/blob/master/firmware/scripts/descriptorgen.py](https://github.com/kcuzner/midi-fader/blob/master/firmware/scripts/descriptorgen.py)) which takes as its arguments every source file in the project that could have some block comments. It then does the following:

1.  Find all block comments (/\* … \*/) in the source and extract them, stripping off leading “\*” characters from each line. The blocks are retained as individual continuous pieces and are each parsed separately.
2.  If the block doesn’t contain text matching the regex “”, it is discarded. Otherwise, the contents of the block comment are wrapped in an arbitrary element and then parsed using [elementtree](https://docs.python.org/2/library/xml.etree.elementtree.html).
3.  Each parsed comment block is assumed to declare one or more “descriptors”. The parsed XML is run through an interpreter which begins assembling objects which will generate the binary descriptor.
4.  After every block has been parsed, the script will generate all the descriptors into a C file, automatically tracking endpoint numbers, addresses, and descriptor lengths.

See the [full description in the post here](http://kevincuzner.com/2019/12/27/writing-reusable-usb-device-descriptors-with-some-xml-python-and-c/).