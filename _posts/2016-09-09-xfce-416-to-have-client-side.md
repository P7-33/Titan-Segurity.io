---
title: 'Xfce 4.16 to have client side decorations and headerbars but not go “full GNOME”'
date: 2019-10-23T01:21:00+01:00
draft: false
---

It took almost half a decade from the release of version 4.12 of the Xfce desktop environment in 2015 to the release of Xfce 4.14 two months ago. Major version Xfce releases have generally been several years apart since it's inception in 1996. This will not be the case with Xfce 4.16; it will arrive much sooner than one would except given Xfce's release-history. The developers secret roadmap reveals that it could be released this time next year. Planned features include a "night light" mode, client side decorations and header-bars in simpler applications. GTK2 will no longer be supported.

[![Xfce-4.14-thunar-ristretto-mousepad.jpg](https://linuxreviews.org/images/thumb/3/32/Xfce-4.14-thunar-ristretto-mousepad.jpg/640px-Xfce-4.14-thunar-ristretto-mousepad.jpg)](https://linuxreviews.org/images/3/32/Xfce-4.14-thunar-ristretto-mousepad.jpg)  
_[Xfce](https://linuxreviews.org/Xfce "Xfce") 4.14 running typical [Xfce](https://linuxreviews.org/Xfce "Xfce") applications: The [Thunar](https://linuxreviews.org/Thunar "Thunar") filemanager, the [ristretto](https://linuxreviews.org/Ristretto "Ristretto") image viewer and the [mousepad](https://linuxreviews.org/w/index.php?title=Mousepad&action=tinymceedit&redlink=1 "Mousepad (page does not exist)") editor._

Major versions of free software projects have even numbers, development versions have odd numbers. The release of [Xfce](https://linuxreviews.org/Xfce "Xfce") Panel 4.15 on October 20th was therefore a development version release and the kick-off for the [Xfce](https://linuxreviews.org/Xfce "Xfce") 4.16 development cycle.

**The [changelog for xfce4-panel 4.15](http://xfce.10915.n7.nabble.com/ANNOUNCE-xfce4-panel-4-15-0-released-td56229.html) gives some pointer to the Xfce developments teams total plan for Xfce 4.16.** The first three lines in it's changelog are:

*   **Drop support for Gtk2** and 4.6 plugins
*   **Drop Gtk2/4.6-only references** from the docs
*   **Don't show or try to load Gtk2 plugins** anymore

[Xfce](https://linuxreviews.org/Xfce "Xfce") 4.14 was a re-write to use version 3 of the GTK toolkit instead of older and barely maintained GTK2. Some plugins and components were not ported. Xfce 4.14 supports those for compatibility. **It seems clear that 4.16 will deprecate GTK2 and remove all support and traces of it. Old panel plugins and everything else which relies on the GTK2 support in libxfce4ui will have to be ported to GTK3**

xfce4-panel 4.15 has some additional changes such as a face-lifted pager and about a dozen bugfixes. It's also got a new "dark mode" selector, more on that below.

"Night light" and "Dark mode" are coming
----------------------------------------

Version 5.17 of the [KDE Plasma](https://linuxreviews.org/KDE_Plasma "KDE Plasma") desktop environment got a brand new built-in "dark mode" feature. Some proprietary operating system from some software company out of Redmond in the United States has a similar built-in feature. Xfce 4.16 will join the club in having a "dark mode" feature which essentially turns the current theme into a sad and dull black and white theme.

**Xfce 4.16 will also have a _night light_ mode for those who prefer a happy colorful theme with less blue light over dark and depressing colors.**

[![Redshift.png](https://linuxreviews.org/images/thumb/1/14/Redshift.png/640px-Redshift.png)](https://linuxreviews.org/images/1/14/Redshift.png)  
_Redshift has been the go-to tray application for night color temperatures on GNU/Linux systems since 2009. More and more desktop environments are duplicating it's functionality so it can be included in the desktop's core programs._

Xfce's release-manager [Simon Steinbeiß](https://linuxreviews.org/Simon_Steinbei%C3%9F "Simon Steinbeiß") has a [secret blog titled "Simon's Secret"](https://simon.shimmerproject.org) where he writes that:

"“Night light” (as in: a timed function that applies a colorfilter to your display to reduce strain on the eyes) will likely be added to the power manager."

**It has been possible to use the small and simple [Redshift](https://linuxreviews.org/w/index.php?title=Redshift&action=tinymceedit&redlink=1 "Redshift (page does not exist)") application to automatically shift the display's temperature to "night-light" since 2009.** It supports changing the color temperature based on when the sun currently sets at a specified location and it has a handy tray-icon for quickly turning it on/off. [Redshift](https://linuxreviews.org/w/index.php?title=Redshift&action=tinymceedit&redlink=1 "Redshift (page does not exist)") works great on _all_ desktop environments including [Xfce](https://linuxreviews.org/Xfce "Xfce") (except for GNOME, of course, since it lacks tray icon support and other basic features. It's more of a tablet/smartfridge desktop so it doesn't really count). [Redshift](https://linuxreviews.org/w/index.php?title=Redshift&action=tinymceedit&redlink=1 "Redshift (page does not exist)") is optional and not many people know about it so it's nice that desktop environments build and integrate their own implementation even though it is somewhat unnecessary.

There will be header-bars and client side decorations
-----------------------------------------------------

[Xfce](https://linuxreviews.org/Xfce "Xfce") developer [Simon Steinbeiß](https://linuxreviews.org/Simon_Steinbei%C3%9F "Simon Steinbeiß") announced that Xfce 4.16 will "play with" client side decorations where "it makes sense". Simpler programs and dialog boxes like the "Appearance" dialog will have header-bars instead of a regular window manager title-bar.

[![Xfce4-appearance-4.14-vs-4.16.png](https://linuxreviews.org/images/thumb/5/59/Xfce4-appearance-4.14-vs-4.16.png/640px-Xfce4-appearance-4.14-vs-4.16.png)](https://linuxreviews.org/images/5/59/Xfce4-appearance-4.14-vs-4.16.png)  
_The current state of affairs in 4.14 (left) and an example of the planned header-bars in 4.16 (right)_

"It is not planned to redesign more complex applications (like Thunar) with Headerbars in 4.16. We will however try to keep the experience and looks consistent, which means gradually moving to client side decorations also with our applications."

Simon expects a "shitstorm about this change".

The [Xfce Wiki has a decorations review page](https://wiki.xfce.org/releng/4.16/roadmap/general_ui/csd) which gives a rough idea of what their plans for header-bars is. It specifically says Xfce will not go "go full Gnome style". Not all applications will have header-bars and those who do will be able to retain the window manager buttons. It will be possible to have the regular title-bar buttons for making programs sticky or minimized and so on _and_ have application-specific

**There is no mention of Wayland support anywhere as of now.** However, the move to client-side decorations does indicate that it is at minimum on the developers mind since that would be the most logical reason as to why they are doing it.

Expect Xfce 4.16 Q3 2020
------------------------

[![Xfce-4.14-on-ubuntu-disco-dango.jpg](https://linuxreviews.org/images/thumb/d/d1/Xfce-4.14-on-ubuntu-disco-dango.jpg/640px-Xfce-4.14-on-ubuntu-disco-dango.jpg)](https://linuxreviews.org/images/d/d1/Xfce-4.14-on-ubuntu-disco-dango.jpg)  
_Xfce 4.14 on Ubuntu_

It took almost 5 years from [Xfce](https://linuxreviews.org/Xfce "Xfce") 4.12 was released to the advent of 4.14. The [secret total plan for Xfce 4.16](https://wiki.xfce.org/releng/4.16/roadmap) reveals that a "`Development Phase`" will last until "mid-2020". A 3 month long pre-release cycle places a Xfce 4.16 final on the table somewhere in the third quarter of 2020. That's just _one year_ from 4.14. It is a very ambitious goal. **We wish the developers of the leading GNU/Linux desktop environment good luck with the development and their very ambitious goal.**

The [roadmap](https://wiki.xfce.org/releng/4.16/roadmap) has links to goals for some of the individual components such as the [thunar](https://wiki.xfce.org/releng/4.16/roadmap/thunar) file manager, the [xfwm4](https://wiki.xfce.org/releng/4.16/roadmap/xfwm4) window manager and the [power manager](https://wiki.xfce.org/releng/4.16/roadmap/xfce4-power-manager). It may be worth a peek if you are curious about [Xfce](https://linuxreviews.org/Xfce "Xfce")'s future.

  
  
from Hacker News https://ift.tt/2Pbp8VD