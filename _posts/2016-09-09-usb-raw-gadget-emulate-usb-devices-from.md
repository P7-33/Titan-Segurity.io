---
title: 'USB Raw Gadget: emulate USB devices from Linux userspace #USB #Linux'
date: 2020-02-12T17:54:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/Untitled.png)

Andrey Konovalov (GitHub user [xairy](https://github.com/xairy)) has developed a Linux kernel module for a USB Raw Gadget. A [USB Raw Gadget](https://github.com/google/kasan/blob/usb-fuzzer/Documentation/usb/raw-gadget.rst) is a kernel module that allows to emulate USB devices from userspace.

There is a [GitHub repository](https://github.com/xairy/raw-gadget) which contains instructions and examples for using Raw Gadget.

The module is currently [under review](https://patchwork.kernel.org/cover/11332295/) for upstream inclusion, so the interface it provides for the userspace might change.