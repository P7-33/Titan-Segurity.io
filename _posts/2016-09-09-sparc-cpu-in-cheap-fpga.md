---
title: 'SPARC CPU In A Cheap FPGA'
date: 2019-11-02T03:05:00+01:00
draft: false
---

There was a time when SPARC CPUs were the sole realm of pricey Sun workstations, but now you can put one on an FPGA with just a little trouble. The problem is you need a fairly big CPU which isn’t always cheap unless someone goes out of business and you get lucky. \[Ttsiodras\] picked up a Pano logic thin client. Pano went under and their entire inventory is out on the surplus market at cheap prices. With a little FPGA magic, you can [turn a few bucks into a SPARC-based computer](https://www.thanassis.space/myowncpu.html).

The insides of the workstation have a Spartan 6 FPGA inside and you’ll need to solder in some JTAG wires, but that shouldn’t put anybody here off.  Of course, the Spartan 6 isn’t the newest tech so you’ll have to get an old version of the Xilinx tools but that’s not hard either. However, there is a strange irony you’ll need to be aware of if you use Linux.

Xilinx provide their WebPack tools free and you can download older versions. However, the versions aren’t always the same. The last tools that support Spartan 6 on Linux don’t support the specific device used in the Pano G2. However, the Windows version does. In a strange twist though, the Windows version installs a Linux virtual environment to run the tools!

The story doesn’t end there, though. \[Ttsiodras\] wanted to run the tools directly in Linux and had quite the adventure trying to get it all running. He did, but it was a fun detective story and you can read about it in the post. If you want to use Windows to configure the FPGA you probably won’t care much, but it is still an interesting read. We found it especially funny that the free WebPack software was still node locked to a particular network card — we’ve had similar problems with FPGA tools from other vendors.

LEON is a SPARC CPU used in a lot of European spacecraft. That’s the CPU that eventually drove the Pano for \[Ttsiodras\]. The FPGA is large enough that he was able to get two 50 MHz cores in the box. You can even simulate the CPU before committing it to silicon.

Unfortunately, the build doesn’t support the network, the 128 MB of RAM on the board or the USB ports. So you won’t quite be ready to use this as your daily Linux workstation. There is, however, a remote gdb interface and a cross compiler, so you can certainly write code for it. If you don’t want to solder, [this technique](https://hackaday.com/2019/04/19/pano-logic-fgpa-hacking-just-got-easier/) might be helpful.

Using a ready-made CPU can be a significant jumpstart to a project. LEON, [RISC-V](https://hackaday.com/2019/02/13/western-digital-releases-their-risc-v-cores-to-the-world/), or even [NIOS](https://hackaday.com/2018/10/05/easy-fpga-cpu-with-max1000/) give you ready-made tools which is a good thing as long as your project isn’t a custom CPU.

  
  
from Hackaday https://ift.tt/2Wyd82e  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)