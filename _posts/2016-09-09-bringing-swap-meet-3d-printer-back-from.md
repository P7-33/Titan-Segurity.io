---
title: 'Bringing a Swap Meet 3D Printer Back from the Dead'
date: 2020-02-10T10:43:00+01:00
draft: false
---

At a recent swap meet, \[digitalrice\] found what appeared to be a like-new QIDI X-Plus 3D printer. It wasn’t clear what was wrong with it, but considering it retails for $900 USD, he figured the asking price of $150 was worth the gamble. As you might expect, the printer ended up being broken. But armed with experience and a supply of spare parts, [he was able to get this orphaned machine back up and running](https://imgur.com/a/AEWi20A).

The first and most obvious problem was that the printer’s Z axis didn’t work properly. When the printer tried to home the axis, one of the motors made a terrible noise and the coupler appeared to be spinning backwards. From his experience with other printers, \[digitalrice\] knew that the coupler can slip on the shaft, but that didn’t appear to be the case here. Removing the stepper motor and testing it in isolation from the rest of the machine, he was able to determine it needed replacing.

[![](https://hackaday.com/wp-content/uploads/2020/02/qidi_detail.jpg?w=400)](https://hackaday.com/wp-content/uploads/2020/02/qidi_detail.jpg)

Improving the printer’s filament path.

Unfortunately, the spare steppers he had weren’t actually the right size. Rather than waiting around for the proper one to come in the mail, he took an angle grinder to the stepper’s shaft and cut off the 5 mm needed to make it fit, followed by a few passes with a file to smooth out any burrs. We’re not sure we’d recommend this method of adjustment under normal circumstances, but we can’t argue with the results.

The replaced Z motor got the printer moving, but \[digitalrice\] wasn’t out of the woods yet. At this point, he noticed that the hotend was hopelessly clogged. Again relying on his previous experience, he was able to disassemble the extruder assembly and free the blob of misshapen PLA, leading to test prints which looked very good.

But success was short lived. After swapping to a different filament, he found it had clogged again. While clearing this second jam, he realized that the printer’s hotend seemed to have a design flaw. The PTFE tube, which is used to guide the filament down into the hotend, didn’t extend far enough out. Right where the tube ended, the filament was getting soft and jamming up the works. With a spare piece of PTFE tube and some manual reshaping, he was able to fashion a new lining which would prevent the filament from softening in this key area; resulting in a more reliable hotend than the printer had originally.

It’s great to see this printer repaired to working condition, especially since it looks like \[digitalrice\] was able to fix a core design flaw. But a broken 3D printer can also serve as the base for a number of other interesting projects, should you find yourself in a similar situation. For example, [replacing the extruder assembly with a digital microscope](https://hackaday.com/2020/01/24/broken-3d-printer-turned-scanning-microscope/) can yield some very impressive results.

  
  
from Hackaday https://ift.tt/31Mo9Q7  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)