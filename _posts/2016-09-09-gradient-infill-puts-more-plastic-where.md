---
title: 'Gradient Infill Puts More Plastic Where You Want It'
date: 2020-01-21T04:14:00+01:00
draft: false
---

It is always tricky setting the infill for a 3D printed part. High infill parts are strong but take longer to print, while low infill prints take less time, but are weaker internally and in danger of surface layer droop between the infill pattern. \[Stephan\] has a better answer: [gradient infill](https://www.cnckitchen.com/blog/gradient-infill-for-3d-prints). You can see a video below and find his [Python code on GitHub](https://github.com/CNCKitchen/GradientInfill).

The idea is simple enough. In most cases, parts under stress see higher stress near the surface. Putting more material there will make the part stronger than adding plastic in places where the stress is lower. \[Stephan\] has done finite element analysis to determine an optimal infill pattern before, but this is somewhat difficult to do. Since the majority of parts can follow the more at the edges and less at the center rule, gradient infill makes sense except for a few special cases.

Of course, the real question is: how do you create parts with this type of infill? Some slicers have infill settings that can almost get you there. However, the setup for them isn’t easy. For example, KISSSlicer’s paid version will take a grayscale image to set the infill density. \[Stephan\] noticed, though, that Cura — and probably most other slicers — put comments in the G-code to show where different features such as infill start. By changing the extrusion amount during infill, you can use the same basic pattern, but still, get the gradient you want.

He wrote a simple program to postprocess the G-code before it is sent to the printer. He computes the distance from the outside of the part and based on that changes the amount of extrusion. This works because of an unusual type of infill he uses that is already in small line segments. However, for more conventional infill patterns, the lines are long, so his program has to chop the lines into shorter segments and then apply the algorithm. This makes for a larger file, of course.

There are a few stipulations. You need to have walls print before infill and you need to be set for relative extrusion. If your slicer doesn’t emit comments to mark where infill starts and stops, that’s going to be a problem. Even then, if the comments aren’t the same as Cura’s, you’ll probably need to change the code to suit. Or just use Cura for slicing.

The test results were good. The parts were stronger, although in some cases, simply increasing the infill would get you the same result. As \[Stephan\] notes, it may not be perfect, but it is useful for many parts.

We aren’t strangers to [postprocessing G code](https://hackaday.com/2015/07/22/better-3d-prints-by-mixing-slicing-techniques/). For some jobs, you just need to [make your own G-code](https://hackaday.com/2018/11/14/3d-print-springs-with-hacked-gcode/), anyway.

  
  
from Hackaday https://ift.tt/2v8EZMU  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)