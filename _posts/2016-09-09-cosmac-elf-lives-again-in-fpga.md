---
title: 'COSMAC ELF Lives Again, in FPGA'
date: 2020-01-23T10:19:00+01:00
draft: false
---

Looking around at the personal computing markets in modern times, there seem to be a lot of choices in the market. In reality, though, almost everything runs on hardware from a very small group of companies, and software is often available across platforms. This wasn’t the case in the personal computing boom of the 70s and 80s, where different computers were wildly different in hardware and even architecture. The Cosmac ELF was one of the more interesting specimens from this era, and [this one has been meticulously reproduced on an FPGA](https://hackaday.io/project/169486-fpga-cosmac-elf).

The original hardware was based on an RCA 1802 microprocessor and had a rudimentary (by today’s standards) set of switches and buttons as the computer’s inputs. It was low cost, even for the time, but was one of the first single-board computers available. This recreation is coded in SpinalHDL and the simplicity of the original hardware makes it relatively easy to understand. The FPGA is cycle-accurate to the original hardware, too, which makes it nearly perfect even without any of the original hardware.

The project’s creator, \[Winston\] aka \[wel97459\], found that SpinalHDL made this project fun to work on (and released his code on his [GitHub page](https://github.com/wel97459/FPGACosmacELF)), and was able to get the code down to just 1500 lines to recreate the original hardware. It’s very impressive, and also an accessible read for anyone interested in [some of the more unique computers offered during the early computer renaissance in the 70s](https://hackaday.com/2017/03/06/vintage-cosmac-elf-is-pretty-close-to-original/).

  
  
from Hackaday https://ift.tt/2NSA5Kk  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)