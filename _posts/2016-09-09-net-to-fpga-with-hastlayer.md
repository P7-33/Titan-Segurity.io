---
title: '.NET to FPGA with Hastlayer'
date: 2019-12-15T10:11:00+01:00
draft: false
---

tHERE are lots of ways to use FPGAs. One way is to convert compute-bound software into hardware. This can increase speed and — in some cases — reduce power consumption. Typically, you’ll do this by writing in a subset of C, but [Hastlayer](https://hastlayer.com/) can convert .NET assemblies into FPGA configurations with some limitations.

The Hungarian company behind Hastlayer claims they’ll eventually have to charge money for something but for now, the tool is free and they are promising to always have some free option. The interesting thing is that the .NET assemblies are essentially object code so you aren’t compiling source but rather an intermediate language that you can generate with many different language tools.

The actual compilation occurs on remote servers, so some people aren’t going to like that. However, at least you aren’t loading your source code, just the DLLs. The tool targets the Nexys 4 DDR board which is apparently now the Nexys A7 board. This board is only $265, but it is frankly a little anemic for the kinds of things you’d typically want to do with FPGA acceleration. In the getting started guide they even say:

> Note that this is a relatively low-end development board that can’t fit huge algorithms and it only supports slow communication channels. So with this board Hastlayer is only suitable for simpler algorithms that only need to exchange small amount of data.

Presumably, they will eventually support bigger hardware.

There are, of course, limitations. Only public virtual methods or methods that implement a method defined in an interface will have hardware entry points. Not all data types are available. Some methods like Array.Copy have limited function. There are no exceptions and recursion has some limitations, too.

Still, if you are adept at .NET and want to get into FPGA coprocessing this could be just the thing.  If you prefer C, there’s [a tool for that](https://hackaday.com/2017/04/26/fpgas-in-c-with-cynth/). Or maybe you prefer [Python](https://hackaday.com/2012/06/13/myhdl-python-programming-option-for-fpga/).

  
  
from Hackaday https://ift.tt/2PlnznO  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)