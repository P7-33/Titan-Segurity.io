---
title: 'Back to the Future: Part III: a color fix patch on Sega
Genesis #Gaming #Vintage #Sega @greg_p_kennedy'
date: 2019-11-18T16:27:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-54.png)

[greg-kennedy.com posts](https://greg-kennedy.com/wordpress/2019/11/12/back-to-the-future-part-iii-color-fix-patch/) about the Sega Genesis / Megadrive game _Back to the Future III_ and how it shipped with a bad bug:

> An exchange on Twitter led me into a trap that consumed a week of my time – the Sega Genesis / Mega Drive version of Back to the Future: Part III shipped with a bug that caused **completely wrong colors to display**. Evidently the programmer(s) were confused about the proper format of color data on the Genesis. While color values _should_ be stored in two bytes as `0000bbb0 ggg0rrr0`, this game instead uses the incorrect format `00000bbb 0ggg0rrr` – all values shifted right by one bit. The end result is that the game displays at half brightness, and lower contrast.

He produced a disassembly that was quite revealing. The game doesn’t have a lot of code re-use, it was apparently written in isolated stages and then combined together at the end. Functions for palette fades and “cutscene” display are duplicated in each segment. Finding palette setting code wasn’t too difficult once a palette were found.

![](https://greg-kennedy.com/wordpress/wp-content/uploads/2019/11/BttF3-Stage1Compare.png)

> With that fixed, I regenerated the checksum and wrote a new ROM, then used [LunarIPS](https://fusoya.eludevisibility.org/lips/) to make an IPS patch for distributing the fix.
> 
> The last step was to port the changes to the EU version of the game. Fortunately, the data is the same, and a Perl script with find-replace made locating the offsets easy. A new IPS patch, a README file, and we’re ready to ship.

You can read the details and download the patch on the [post here](https://greg-kennedy.com/wordpress/2019/11/12/back-to-the-future-part-iii-color-fix-patch/).