---
title: 'Yosys Fronts for Xilinx ISE'
date: 2019-12-14T04:11:00+01:00
draft: false
---

We always marvel at how open-source tools can often outstrip their commercial counterparts. Yosys, the open-source tool for Verilog synthesis, is a good example. Although the Xilinx ISE design suite is something close to abandonware, a lot of people still use it because it supports older FPGAs the newer tools don’t. Its Verilog parser is somewhat slow to catch up to new standards, and according to [a recent GitHub update](https://github.com/YosysHQ/yosys/issues/448), Yosys can now provide files for ISE that target Spartan 6, Virtex 7, and Series 7 FPGAs. In addition, there is some support for Spartan 3, Virtex 2, 4, and 5, although those are not ready yet.

According to the post, you’ll want to use the synth\_xilinx command along with the -ise option and a -family option that matches your target (that is, xc6s for Spartan 6).  On the output side, you’ll write an EDIF file using the write\_edif command.

This is not to say that the Xilinx XST parser that processes Verilog for ISE is terrible. However it does lag behind on some features, and if it doesn’t work… too bad. Xilinx has a lower focus on ISE and its variants in favor of Vivado which doesn’t support many older chips. With Yosys, there’s an active community around the program and, if you must, you can dig in and fix any problems yourself. You can at least use the source code to answer what if questions.

We’ve covered some tools and tricks for [Yosys and the Lattice targets](https://hackaday.com/2018/10/03/icestorm-tools-roundup/). If you are wanting to get started, there’s always our [boot camp](https://hackaday.com/2018/08/06/learn-fpga-fast-with-hackadays-fpga-boot-camp/).

  
  
from Hackaday https://ift.tt/36Jezir  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)