---
title: 'There’s more to the 3D print than the eye can see'
date: 2019-10-19T15:09:00+01:00
draft: false
---

If you thought CADing designs for 3D printing was hard enough, wait until you hear about this `.stl` trick.

\[Angus\] of Maker’s Muse recently [demoed a method for creating hidden geometries](https://www.youtube.com/watch?v=ElJHM6IMIMg) in `.stl` files that are only revealed during the slicing process before a 3D print. (Video, embedded below.) The process involves creating geometries with a thickness smaller than the size of the 3D printer’s nozzle that still appear to be solid in a `.stl` editor, but will not be rendered by a FDM slicer.

Most 3D printers have 0.4 mm thickness nozzle, so creating geometries with a wall thinner than this value will result in the effect that you’re looking for. Some possible uses for this trick are to create easter eggs or even to mess with other 3D printing enthusiasts. Of course, \[Angus\] recommends not to use this “deception for criminal or malicious intent” and I’d have to agree.

There’s a few other tricks that he reveals as well, including a way to create a body that’s actually a thin shell but appears to be solid: great for making unprintable letters that reveal hidden messages.

Nevertheless, it’s a cool trick and maybe one of those “features not bugs” in the slicer software.

  
  
from Hackaday https://ift.tt/2oXy5Hp  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)