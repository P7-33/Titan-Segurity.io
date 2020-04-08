---
title: 'Manual Mesh Bed Levelling for 3D Printers'
date: 2019-12-01T13:01:00+01:00
draft: false
---

In 3D printing, we often talk about leveling the print bed, although that’s not an accurate term. A bed that is level in our terms presents a flat surface that is parallel to the path of the print head, but within reason we care little about that. Instead we care more about it being parallel to the path of the head than it being perfectly flat. If we had a perfectly flat bed — say a sheet of glass — you’d think it might be pretty easy, but for some other materials it could be convex or concave or even have ripples all over the place. \[Teaching Tech\] shows you how to manually “level” the bed [using a mesh but without using an automatic sensor](https://www.youtube.com/watch?v=vcxM7-VK44k). You can see the technique in the video below.

When you use adjustments to level the bed, you are tramming it, but only the very pedantic use that term for [fine adjustment](https://www.collinsdictionary.com/dictionary/english/tramming). But no amount of adjusting bed springs will get rid of bulges and ripples. A common solution is to use a sensor to measure the distance to the bed and form a mesh correction. Then, as the printer head moves in the XY plane, the software will adjust the Z-axis to rise over bumps and go down if there is a concave portion of the bed. What \[Teaching Tech\] is doing, however, is a manual mapping. You won’t need to add a sensor to your printer to take advantage of the method. 

The technique does require — probably — reflashing your firmware, and the firmware he uses appears to be Marlin. However, Repetier and perhaps other firmware does this too. The LCD bed leveling option makes it pretty trivial to do the actual work, and once you compute the mesh, you shouldn’t have to do it again. Essentially, the printer will probe multiple points and pause, allowing you to adjust the head using the usual piece of paper.

Each time you make the adjustment, the printer remembers the height adjustment and then uses the collection of different heights to build up the correction mesh. This is essentially the same process that occurs with a probe except your manual adjustment is standing in for the probe data. You shouldn’t need to do that very often as long as the shape of the bed doesn’t change.

If you can update your firmware, this is a cheap way not to have to add a Z probe to your printer. Then again, adding one isn’t that expensive, and then the whole process is automated. That automation makes it easy to recheck it or even run it before each print if you like.

There are lots of other techniques. A [force-sensitive resistor](https://hackaday.com/2019/09/01/force-sensitive-resistor-takes-the-pain-out-of-bed-leveling/) can be shared among printers, for example, and would actually work with this technique if you have a serious bed problem. If you mill PCBs, you might run into the same problem, and there’s a [very similar solution](https://hackaday.com/2014/12/12/mill-warped-pcb-blanks-on-an-uneven-bed/).

  
  
from Hackaday https://ift.tt/35OkcLy  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)