---
title: 'C#, The Language For All Platforms – Now Including Windows 3.11 And DOS'
date: 2020-02-10T04:43:00+01:00
draft: false
---

The Microsoft .NET framework has been with us in one form or another since the millennium, and though it has remained largely the preserve of the Microsoft universe, it has found its way since then through a variety of implementations to other platforms including MacOS and GNU/Linux. In Microsoft terms though its history goes back only as far as Windows 98, earlier MS operating systems remain off-limits.

Just a glimmer of .NET in DOS and Windows 3.11 comes courtesy of \[Michal Strehovský\], [who has successfully compiled .net C# code for both Windows 3.11 and DOS](https://twitter.com/MStrehovsky/status/1215331352352034818). An in-depth explanation [comes courtesy of \[Scott Hanselman\]](https://www.hanselman.com/blog/NETEverywhereApparentlyAlsoMeansWindows311AndDOS.aspx), and it involves some tricks spanning the decades since the early 1990s. The .NET Core compiler’s object files can be fed into the linker that shipped with an ancient version of Microsoft’s C++ compiler, which when used with Microsoft’s Win32s compatibility layer that brought some of Windos NT’s APIs to the 16-bit OS, allows C# from 2020 to run as though it were 1992 again. Meanwhile the DOS version uses .NET Core’s ability to produce self-contained executables along with some very significant tricks to pare down the size of the finished program from many megabytes to an eventual DOS-suitable 27k. Remember the apocryphal Bill Gates quote, that “_640k should be enough for anyone_“, that refers to the _maximum_ memory available to DOS without extra memory-extending tricks.

Neither piece of software is especially useful, and we can’t see a rush of C# coders to these new platforms. But we applaud him for his ingenuity, and getting old hardware to do new tricks is right up our alley. It’s certainly dredged up a few memories from back in the day for us. Meanwhile we’ve featured .NET in a few projects over the years, [most recently on an FPGA](https://hackaday.com/2019/12/15/net-to-fpga-with-hastlayer/).

  
  
from Hackaday https://ift.tt/31DTAw5  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)