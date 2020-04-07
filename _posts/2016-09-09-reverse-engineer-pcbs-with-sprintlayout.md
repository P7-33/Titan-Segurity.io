---
title: 'Reverse Engineer PCBs with SprintLayout'
date: 2019-12-31T13:47:00+01:00
draft: false
---

\[Bwack\] had some scanned pictures of an old Commodore card and wanted to recreate PC boards from it. It’s true that he could have just manually redrawn everything in a CAD package, but that’s tedious. Instead, [he used SprintLayout 6.0](https://www.youtube.com/watch?v=g0nkLJ4YQ2c) which allows you to import pictures and use them as a guide for recreating a PCB layout.

You can see the entire process including straightening the original scans. There are tools that make it very easy to place new structures over the original scanned images.

One might think the process could be more automated, but it looks as though every piece needs to be touched at least once, but it is still easier than just trying to eyeball everything together.

Most of the video is sped up, which makes it look as though he’s really fast. Your speed will be less, but it is still fairly quick to go from a scan to a reasonable layout.

The software is not free, but you can do something somewhat similar in KiCAD. The trick is to get the image scaled perfectly and convert it to a component on a user layer. Then you can add the new component and enable the user layer to see the image as you work. There’s even [a repository of old boards recreated in KiCAD](https://github.com/baldengineer/bit-preserve).

There are probably [an infinite number of ways](https://hackaday.com/2013/11/15/recreate-a-pcb-with-a-scanner-and-inkscape/) to attack this. An older version of SprintLayout helped with the [Re-Amiga 1200](https://hackaday.com/2018/08/28/recreating-the-amiga-1200-pcb-from-pictures/).

  
  
from Hackaday https://ift.tt/2SFPPnb  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)