---
title: 'The SEGGER Compiler available in Embedded Studio for ARM @SEGGERMicro'
date: 2020-02-18T15:54:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-43.jpg)

SEGGER is a company making electronics and software used by many makers on a daily basis, including the debug interfaces Adafruit uses for embedded system development. So what software does SEGGER use in developing their own products?

> At SEGGER, we use our own tools to establish an internal feedback loop. This is extremely helpful in creating and fine-tuning our products. A significant amount of engineering time and effort is put into making our IDE [Embedded Studio](https://www.segger.com/products/development-tools/embedded-studio/) better and better, every day.
> 
> We felt there was one thing we should add: Our own compiler.
> 
> Although the included compilers, GCC and Clang, are well proven and widely used, it would be nice to have full control over the compiler, to maintain, tailor, and optimize it.

The SEGGER compiler easily beats the “plain vanilla Clang” in speed and also in code size, as well as beating GCC by most measures. It is up to par with commercial compilers.

They have been focusing on changes in the code generator for ARM’s Thumb-2 code, targeting Cortex-M based microcontrollers. Next steps are improved compatibility with other compilers, not just GCC & Clang, (for pragmas and other specialties) to make it easy to switch.

A beta version is already included in the latest version of Embedded Studio for ARM. The official release is planned for some time in Q1 of this year.

Being a part of Embedded Studio, the SEGGER Compiler can be used under the terms of [SEGGER’s Friendly Licensing](https://www.segger.com/purchase/licensing/license-sfl/), which allows anybody to use it free-of-charge for non-commercial use and evaluation.

See [the SEGGER blog](https://blog.segger.com/the-segger-compiler/) for additional information.