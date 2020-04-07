---
title: 'FPGA 6800 Uses Python Toolbox'
date: 2019-12-28T07:51:00+01:00
draft: false
---

Usually, when you think of designing — or recreating — a CPU on an FPGA, you assume you’ll have to use Verilog or VHDL. There are other options, as well, but those are the biggest two players in FPGA configuration. \[Robert Baruch\] has a multipart series [where he uses nMigen](https://www.youtube.com/watch?v=85ZCTuekjGA) — a Python toolbox — to recreate a 6800 CPU like the one used in many vintage video games and pinball machines.

Unlike some tools that try to convert software written in some language to an FPGA configuration, nMigen uses Python as a scripting language to create code in FHDL. This is similar in concept to VHDL or Verilog, but gives up the event-driven paradigm, opting instead to allow designers to explicitly call out synchronous and combinatorial logic.

Interestingly the tool hinges on Yosys, so it can target several Lattice parts as well as FPGAs from Intel/Altera and Xilinx.  It turns out that the n in nMigen is for new, and you might find some of the [documentation for regular old Migen](https://m-labs.hk/gateware/migen/) to be useful.

As for the 6800, it is one of the older CPUs used in hobby computers. The 8 bit CPU had about 72 instructions, depending on how you counted them. This was before reduced instruction sets were the rage, so it is a little extra work to implement a rich instruction set.

There are other Python options, such as [MyHDL](https://hackaday.com/2012/06/13/myhdl-python-programming-option-for-fpga/) and [PyCPU](https://hackaday.com/2012/06/11/programming-fpgas-with-python/), for example. You can even try [using .NET](https://hackaday.com/2019/12/15/net-to-fpga-with-hastlayer/).

  
  
from Hackaday https://ift.tt/2tZpo1B  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)