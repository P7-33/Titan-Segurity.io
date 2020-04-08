---
title: 'Chisel Away At FPGA Development'
date: 2019-10-29T03:06:00+01:00
draft: false
---

Most of the time if you were to want to develop for an FPGA, you might turn to Verilog or VHDL. Both of these are quite capable, but they are also firmly rooted in languages that are old-fashioned by today’s standards. There have been quite a few attempts to treat those languages as an output to some other tool — either a higher-level language or a graphical tool. One recent effort is a toolchain that starts with [Chisel](https://www.chisel-lang.org/).

The idea behind Chisel is to provide Scala with Verilog-like constructs. If you want, you can use it as a “super Verilog” taking advantage of classes and other features. However, Chisel also allows you to create generators that produce different output Verilog depending on how you call them. True, you can do some of this with Verilog modules, but it is much easier with Chisel. Chisel uses Firrtl to convert what you ask it to do into Verilog for different FPGA and ASIC targets.

If you read some of the links at the homepage, you’ll see that they acknowledge that you can do anything you could do in Chisel in straight Verilog. In fact, there are some features Chisel lacks so far, although you can always fallback to Verilog black boxes to overcome those problems. However, that’s like saying why use C++ instead of C or C instead of assembly language. Early C++ compilers emitted C, so absolutely you could do anything C++ does in C — it just wasn’t always very easy. Ditto for assembly language. Obviously, you can do anything and everything in assembly. But the higher-level abstractions can make you more productive.

You can learn Chisel even if you don’t know Scala, without installing [any software at all](https://mybinder.org/v2/gh/freechipsproject/chisel-bootcamp/master). There are even some simulation-based verification tools available. Of course, it’s worth remembering that there are a host of similar competitors out there including [SpinalHDL](https://hackaday.com/2018/12/08/vexrisc-v-exposed/) and [MyHDL](https://hackaday.com/2012/06/13/myhdl-python-programming-option-for-fpga/). Time will tell if any of these ever gain widespread adoption.

  
  
from Hackaday https://ift.tt/2Pr4rFt  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)