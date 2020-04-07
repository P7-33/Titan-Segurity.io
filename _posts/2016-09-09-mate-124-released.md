---
title: 'MATE 1.24 Released'
date: 2020-02-10T18:06:00+01:00
draft: false
---

[MATE 1.24 has been officially released](https://mate-desktop.org/blog/2020-02-10-mate-1-24-released/) by the developers as scheduled. They are going to be part of some major Linux distribution coming up in April, such as Ubuntu 20.04 and Fedora 32. The highlight of MATE 1.24 release are moving from dbus-glib to GDBus, intltools to gettext, and also Python 3 migration due to EOL for Python 2. HiDPI is also one aspect the developer was focusing on for this release.  
  
Tarballs have been uploaded to [usual place](https://pub.mate-desktop.org/releases/1.24/) and soon it will be coming to many distributions. I was ready to provide binary packages for MATE 1.24 for Slackware (-current users), but unfortunately that idea might have to be postponed a bit since mate-power-manager now requires newer upower (0.99.8+) which Slackware doesn't have (yet). It will become part of Slackware when Plasma 5 and XFCE 4.14 are introduced to -Current tree someday.  
  
Git tree are updated to build MATE 1.24 releases in master branch (except for mate-power-manager). Feel free to pull the latest master branch and compile it on your own if you don't want to wait until new upower gets included in current.