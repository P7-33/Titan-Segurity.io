---
title: 'Show HN: I''ve been working on X11 on (jailbroken) iOS'
date: 2020-01-18T01:32:00+01:00
draft: false
---

X11 on iOS
==========

* * *

I'm excited to announce that X11 is coming soon to iOS. Most (see below) packages and dependencies for a fully functioning X11 desktop system have been compiled and are available on Cydia for iOS 11+. All packages have been compiled for arm64 and have been tested on iOS 12.4 and iOS 13.1. This requires a jailbroken device.

This site will serve largely as documentation for building yourself. You can add the Cydia repo below for the deb packages. Please let me know if you run across any issues with the debs; it's likely I messed up including a library or something like that. _(These aren't done just yet.)_  
  
[](cydia://url/https://cydia.saurik.com/api/share#?source=https://maxleiter.com/cydia)

![X11 on iOS](https://maxleiter.com/X11/pic.jpeg)

At the moment, a virtual screen is accessed via a VNC client to an Xvnc[\[2\]](https://maxleiter.com/X11/#1)instance running on the iDevice. If you're unfamiliar, Xvnc is an X server with a virtual screen that can be accessed via VNC. The best part of this is no drivers are required: it's all handled by Xvnc.

I want to turn my iPad into a proper development environment, and a windowing system helps with that. It's a powerful machine with a Unix-like OS, so X11 seemed like a reasonable project. X11 allows running arbirtary Linux applications (assuming you can make them compile) — Advanced applications like browsers and IDEs are now available, assuming you can make them compile.

*   X11 on iOS via Xvnc
*   Working window manager (jwm)
*   [Loads](https://github.com/MaxLeiter/cydia/tree/master/debs) of other packaged libraries, tools, and applications, including meson/ninja and ocaml.
*   All available in a [Cydia repo](https://maxleiter.com/cydia)

*   Fix modern versions of fontconfig (> 2.8.0)
*   Proper desktop enviroments like XFCE and GNOME
*   Qt support
*   Experiment with Wayland via wayvnc

If you're interested in using X11 now, or helping make it available sooner, feel free to

[email me](https://maxleiter.com/cdn-cgi/l/email-protection#afc2ced7d8cac3c381c3cac6dbcaddefc8c2cec6c381ccc0c2)

or find me on IRC as MaxLeiter in #X11iOS on Freenode. More information on contributing is in the works.

[On a separate page](https://maxleiter.com/X11/instructions.html)

*   Getting ``checking build system type... Invalid configuration `arm64-apple-darwin19.0.0': machine `arm64-apple' not recognized``? Run `echo 'echo arm-apple-darwin' > config.sub`

* * *

  
  
from Hacker News https://ift.tt/363a80U