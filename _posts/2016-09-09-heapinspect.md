---
title: 'Heapinspect'
date: 2020-01-29T23:36:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-AkO26lTkrPM/XhU6L9gHauI/AAAAAAAARZQ/-Vk5gv3Dkboegr8nEcjUBDk_5zUcWNa7gCNcBGAsYHQ/s640/heapinspect_1_pp1.png)](https://1.bp.blogspot.com/-AkO26lTkrPM/XhU6L9gHauI/AAAAAAAARZQ/-Vk5gv3Dkboegr8nEcjUBDk_5zUcWNa7gCNcBGAsYHQ/s1600/heapinspect_1_pp1.png)

**Heapinspect - Inspect Heap In Python**

  
`HeapInspect` is designed to make `heap` much more prettier.  
**Now this tool is a [plugin](https://www.kitploit.com/search/label/Plugin "plugin") of [nadbg](https://github.com/matrix1001/nadbg "nadbg"). Try it!**  
  
**Features**

*   Free of [gdb](https://www.kitploit.com/search/label/GDB "gdb") and other requirement
*   Multi [glibc](https://www.kitploit.com/search/label/Glibc "glibc") support
    *   2.19, 2.23-2.27 (currently tested)
    *   both 32bit and 64bit
*   Nice UI to show heap
    *   `HeapShower` (detailed)
    *   `PrettyPrinter` (colorful, summary)
*   Heapdiff (working)
*   Corruption detect & exploit [analysis](https://www.kitploit.com/search/label/Analysis "analysis") (working)
*   Also support gdb (python2 only) :)

[](https://www.blogger.com/u/7/null)  
**Usage**  
  
**Quick shot**  
A quick use of this tool.  

[![](https://1.bp.blogspot.com/-OXdpnEU1u40/XhU6g-m46lI/AAAAAAAARZY/ZG2h6mepaHkt6QyJXL31AFx0u26pfXUWwCNcBGAsYHQ/s640/heapinspect_2_pp2.png)](https://1.bp.blogspot.com/-OXdpnEU1u40/XhU6g-m46lI/AAAAAAAARZY/ZG2h6mepaHkt6QyJXL31AFx0u26pfXUWwCNcBGAsYHQ/s1600/heapinspect_2_pp2.png)

  

[![](https://1.bp.blogspot.com/-ZrRlMFLTQtY/XhU6g4QwM_I/AAAAAAAARZg/qgC00qMf8b0sKKPlqnFR6AfTku6SEKO3ACNcBGAsYHQ/s640/heapinspect_3_raw1.png)](https://1.bp.blogspot.com/-ZrRlMFLTQtY/XhU6g4QwM_I/AAAAAAAARZg/qgC00qMf8b0sKKPlqnFR6AfTku6SEKO3ACNcBGAsYHQ/s1600/heapinspect_3_raw1.png)

  

[![](https://1.bp.blogspot.com/-vfJA8nZBT20/XhU6g4FhcHI/AAAAAAAARZc/r7LkCaNsjG4aEaE2qSFfJ4svT2k1ZufHwCNcBGAsYHQ/s640/heapinspect_4_rela1.png)](https://1.bp.blogspot.com/-vfJA8nZBT20/XhU6g4FhcHI/AAAAAAAARZc/r7LkCaNsjG4aEaE2qSFfJ4svT2k1ZufHwCNcBGAsYHQ/s1600/heapinspect_4_rela1.png)

  

[![](https://1.bp.blogspot.com/-AkO26lTkrPM/XhU6L9gHauI/AAAAAAAARZU/tcYwYSQp4YEbDA4jViZzrOd0QEGcBS-xgCEwYBhgL/s640/heapinspect_1_pp1.png)](https://1.bp.blogspot.com/-AkO26lTkrPM/XhU6L9gHauI/AAAAAAAARZU/tcYwYSQp4YEbDA4jViZzrOd0QEGcBS-xgCEwYBhgL/s1600/heapinspect_1_pp1.png)

  
You can also use it as a gdb plugin, very useful when `pwndbg` or other plugins failed to analysis heap.

```
sed -i "1i source `pwd`/gdbscript.py" ~/.gdbinit # alternatively, you can add that line manually
```

**Note**  
`HeapInspect` does not support `gdb python3` for now. Anyone who can make it `python3` compatible are welcome.  

[![](https://1.bp.blogspot.com/-xpaSdlBZ-TQ/XhU6pPMUvYI/AAAAAAAARZk/X-9skOdaIgMU9RF3vnBlC3MuwBj1HB7PACNcBGAsYHQ/s640/heapinspect_5_gdb1.png)](https://1.bp.blogspot.com/-xpaSdlBZ-TQ/XhU6pPMUvYI/AAAAAAAARZk/X-9skOdaIgMU9RF3vnBlC3MuwBj1HB7PACNcBGAsYHQ/s1600/heapinspect_5_gdb1.png)

  

[![](https://1.bp.blogspot.com/-UjypfAPMTg4/XhU6pEOZpmI/AAAAAAAARZo/Lf8PHptiPYINgjY7Wv5lQGhCPRcW-0E5wCNcBGAsYHQ/s640/heapinspect_6_gdb2.png)](https://1.bp.blogspot.com/-UjypfAPMTg4/XhU6pEOZpmI/AAAAAAAARZo/Lf8PHptiPYINgjY7Wv5lQGhCPRcW-0E5wCNcBGAsYHQ/s1600/heapinspect_6_gdb2.png)

  

[![](https://1.bp.blogspot.com/-zUXKVOD9bxY/XhU6pKdG7SI/AAAAAAAARZs/uoCPrxsvWew-nSVnjYWyAcKt_5z2gg6IACNcBGAsYHQ/s640/heapinspect_7_gdb3.png)](https://1.bp.blogspot.com/-zUXKVOD9bxY/XhU6pKdG7SI/AAAAAAAARZs/uoCPrxsvWew-nSVnjYWyAcKt_5z2gg6IACNcBGAsYHQ/s1600/heapinspect_7_gdb3.png)

  
**Basic**  
Pretty easy to use. I will make it a package later.

```
from heapinspect.core import *  
hi = HeapInspect(1234)       #pid here  
hs = HeapShower(hi)  
  
print(hs.fastbins)  
print(hs.smallbins)  
print(hs.largebins)  
print(hs.unsortedbins)  
print(hs.tcache_chunks)  
  
hs.relative = 1              #relative mode, check Quick shot  
print(hs.fastbins)  
  
sleep(10)  
#now assume that the [heap](https://www.kitploit.com/search/label/Heap "heap") state has changed  
hs.update()                  #use this to refresh  
  
pp = PrettyPrinter(hi)  
print(pp.all)                #pretty printer  
pp.update()                  #use this to update
```

  
**Test**  
There are some testcases.

```
heapinspect/tests/ $ python test.py  #this will run all test cases for you to check this tool.    ......  ......    test case unsortedbins64 at test/testcases/libc-2.27/64bit  pid:6704  =========================           fastbins           =========================  =========================         unsortedbins         =========================  chunk(0x7f9aae2e6720): prev_size=0x0      size=0xb1     fd=0x7f9aacdfbca0  bk=0x7f9aae2e6880  chunk(0x7f9aae2e6880): prev_size=0x0      size=0xb1     fd=0x7f9aae2e6720  bk=0x7f9aacdfbca0  =========================          smallbins           =========================  =========================          largebins           =========================  =========================            tcache            =========================  tcache[9]:  chunk(0x7f9aae2e6670): prev_size=0x0      size=0xb1     fd=0x7f9aae2e65d0  bk=0x0  chunk(0x7f9aae2e65c0): prev_size=0x0      size=0xb1     fd=0x7f9aae2e6520  bk=0x0  chunk(0x7f9aae2e6510): prev_size=0x0      size=0xb1     fd=0x7f9aae2e6470  bk=0x0  chunk(0x7f9aae2e6460): prev_size=0x0      size=0xb1     fd=0x7f9aae2e63c0  bk=0x0  chunk(0x7f9aae2e63b0): prev_size=0x0      size=0xb1     fd=0x7f9aae2e6310  bk=0x0  chunk(0x7f9aae2e6300): prev_size=0x0      size=0xb1     fd=0x7f9aae2e6260  bk=0x0  chunk(0x7f9aae2e6250): prev_size=0x0      size=0xb1     fd=0x0             bk=0x0 
```

  
**Docs**  
Detailed docstrings have been written into the source code.  
I have built a sphinx doc in `docs`. Just open `docs/build/html/index.html` with your browser.  
  
**Devlog**  
  
**2018/12/10 Version 0.1.3**

*   add support for gdb

  
**2018/11/6 version 0.1.2**  
docs update.

*   update sphinx docs
*   reshape file structure

  
**2018/11/5 version 0.1.1**  
not a functional update.

*   PEP8
*   docstrings
*   performance update

  
**2018/10/31 version 0.1.0**  
first release

*   better cmdline option

  
**2018/10/30 version 0.0.8**  
next version will be a release.

*   CRLF to LF
*   code refine
*   readme refine
*   pretty printer

  
**2018/10/29 version 0.0.7**

*   auto test
*   code refine

  
**2018/10/27 version 0.0.6**  
this is not a stable version. im trying to fix bugs due to different glibc. i need help to test this.

*   add multi libc support
*   add x86 support

  
**2018/10/26 version 0.0.5**  
next version will add multi libc support. heapdiff and heap check will be added later.

*   `HeapShower`
*   relative heap & libc offset showing
*   fix search loop bug
*   `bins` now search from `bk` instead of `fd`, as the manner of glibc

  
**2018/10/24 version 0.0.4**

*   `HeapRecoder` , I will make a heapdiff
*   `smallbins` and `largebins`

  
**2018/10/23 version 0.0.3**

*   `fastbin` prototype
*   `unsortedbin` prototype
*   `bins` prototype
*   `tcache` prototype

  
**2018/10/22 version 0.0.2**

*   add `C_Struct` to handle c structure

  
**2018/10/19 version 0.0.1**

*   add `class HeapInspector`
*   trying to parse more information of `arena`

  
**2018/10/18 version 0.0.0**

*   add `class Proc` in `proc_util`
*   experimental test in `test.py`

  

**[Download Heapinspect](http://ellevolaw.com/3sgW "Download Heapinspect")**

**Regards**

**Kang Asu**