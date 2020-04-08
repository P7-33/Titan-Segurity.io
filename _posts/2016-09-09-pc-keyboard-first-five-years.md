---
title: 'PC Keyboard: The First Five Years'
date: 2019-10-30T05:07:00+01:00
draft: false
---

The vast majority of PC users today have no memory of what PC keyboards looked like before the standard 101/102-key layout arrived, even though various OEMs do their best to mangle the standard layout in order to minimize usability, especially on laptops. OEM-specific modifications aside, the basic layout of the main block of alphanumeric keys has not changed in over 30 years, since 1986.

However, up until that point the PC keyboard layout and the keyboard hardware changed quite a bit, and looking at the 1981-1986 IBM Technical References is key to understanding a) why the standard keyboard scan codes are so complex, and b) why there are so many seemingly odd vendor-specific modifications of the standard layout.

### 83-key Layout, 1981

All keyboard diagrams were borrowed from IBM Technical References. The original PC keyboard (1981) looked like this:

[

<img src="http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-83k-us-640x295.png" alt="" class="wp-image-4542" />

](http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-83k-us.png)

Original 83-key PC keyboard, 1981

From today’s perspective, that keyboard looks rather strange for a number of reasons.

The Enter key is big on the US keyboard, the Esc key is in an odd place, the Ctrl key is where Caps Lock is now and Caps Lock is where the right Ctrl key is now, there’s just one Alt and one Ctrl key, the PrtSc key is jammed in a weird space under the Enter key, and the numeric block is barely recognizable as well.

That the function keys (only F1-F10) are organized in two columns on the left is a comparatively minor difference.

On a technical level, it is important to understand one basic but perhaps non-obvious fact: The keys have numbers corresponding to their location on the keyboard. The behavior of all keys (i.e. what data they send when pressed/released) is purely a function of their number. It has absolutely nothing to do with the labels on the key tops—that’s strictly cosmetic.

### 84-key Layout, 1984

When the IBM PC/AT came out in 1984, it sported a new and different keyboard. At first glance, the keyboard looked just like the original PC keyboard with function keys on the left; the biggest visual difference was that there was now a clear separation between the main alphanumeric block and the numeric block:

[

<img src="http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-84k-us-640x271.png" alt="" class="wp-image-4543" />

](http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-84k-us.png)

Updated 84-key PC/AT keyboard, 1984

But on closer look, there were very substantial changes. For one thing, the Esc key moved to a totally different place, and it now lived in the upper left corner of the numeric block. The backslash key moved from next to the left Shift to the other corner, next to the Backspace key. The Enter key changed shape and forced the backtick (\`) key to move where Esc used to live. The new 84th key was SysRq (System Request), never used much at all.

A significant difference not apparent from the above diagram is that the AT keyboard has three LED indicators. These show the current state of Caps Lock, Num Lock, and Scroll Lock. Another new feature not visible in diagrams is typematic control: The AT keyboard has programmable delay and repeat rate for keys held down for a longer period of time.

To that end, the AT keyboard provides bidirectional communication between the host (keyboard controller) and the keyboard itself. Note that the LEDs are fully under the control of the host system, and it is only a convention that they show the lock states. The system BIOS normally manages the LED state, or an OS does.

There was another technical change: For reasons that are not entirely obvious, the AT keyboard sends quite different scan codes compared to the original PC keyboard. The keyboard controller on the system motherboard translates the scan codes from the keyboard into scan PC-compatible scan codes, such that software written to deal with PC (and XT) scan codes continues to work on ATs.

There are echoes of the 84-key AT layout which can be found on various OEM keyboards. There are 102-key keyboards with AT-style Enter and small Backspace, for example.

### Enhanced 101/102-key Layout, 1986

In 1986, IBM finally arrived at the “enhanced” keyboard layout everyone knows:

[

<img src="http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-101k-us-640x271.png" alt="" class="wp-image-4544" />

](http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-101k-us.png)

Enhanced 101-key US layout

There was a slew of changes from the previous 84-key AT layout: The function keys were moved from the left to the top, with F11 and F12 added. Completely new “gray” cursor and movement keys were added between the main alphanumeric block and the numeric block. Because the function keys were relocated, the overall size of the keyboard did not significantly change.

The Esc key moved to the upper left corner, similar to where it was on the original PC keyboard. Caps Lock moved under the Tab key, and Ctrl and Alt keys now both came in left and right variants.

On the 101-key US layout, the Enter key lost weight; the backslash key moved to where the top part of the fat Enter used to be, making room for a double-sized Backspace key.

The non-US 102-key layouts were very similar; this is for example the UK layout:

[

<img src="http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-102k-uk-640x300.png" alt="" class="wp-image-4545" />

](http://www.os2museum.com/wp/wp-content/uploads/2019/08/ibm-102k-uk.png)

Enhanced 102-key UK layout

The differences are best described using the key position numbers (click on images to see larger size versions). Enter is still key number 43; key 29 (backslash) is gone, but effectively reappears nearby as key 42 above the right Shift key, with the same scan code. Key 45 (to the right of the smaller left Shift key) is the additional 102nd key.

The Enhanced keyboard has several non-obvious new features. It supports a new Read ID command (0F2h) which can be used by software to identify it. It also supports two additional sets of scan codes. The AT keyboard set is called Scan Set 2, the original PC set is Scan Set 1, and there is a new, much simpler and more straightforward Scan Set 3. Unfortunately this change came too late and Scan Set 1 is next to useless because the keyboard controller achieves the same thing, and the significantly more sane Scan Set 3 was never widely used by operating systems because many clone keyboards do not support it (Solaris 8 is one of the very few OSes attempting to use it).

The gray keys (arrows, Ins, Del, Home, End, Page Up, Page Down) behave in quite non-obvious manner. On the 83- and 84-key keyboards, the Num Lock key is the only option for switching between numeric input and cursor keys. On the Enhanced keyboard, Num Lock is much less important because standalone cursor keys are always available. However, for compatibility with the older keyboards, the gray keys send different scan codes depending on the state of Num Lock and Shift keys; this simulates the keys on the numeric block.

The Enhanced keyboard uses an extra byte (E0h) with some of the additional keys (gray keys, added Ctrl and Alt keys). The E0h code is ignored by old software, so only one Alt or Ctrl is still seen, but new software can use the extra code to distinguish the right and left Alt and Ctrl keys.

### PS/2 Keyboard, 1987

The only real difference between the Enhanced AT keyboards and PS/2 keyboards is the connector size. AT keyboards use a 5-pin DIN connectors, while PS/2 keyboards switched to the smaller mini-DIN connector. On the electrical and functional levels there are no differences, which is why a simple mechanical adapter suffices to convert an AT keyboard to a PS/2 keyboard or vice versa.

_Note: Thanks go to the generous folks who published scans of the various IBM Technical References. Having these documents publicly available has been very, very helpful._

  
  
from Hacker News https://ift.tt/2Ur8Mc5