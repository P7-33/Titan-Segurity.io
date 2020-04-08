---
title: 'Please Think Architecture'
date: 2019-10-26T02:52:00+01:00
draft: false
---

Please think architecture...
============================

**Poul-Henning Kamp** [phk at phk.freebsd.dk](mailto:freebsd-arch%40freebsd.org?Subject=Please%20think%20architecture...&In-Reply-To= "Please think architecture...")  
_Wed Aug 29 10:02:01 PDT 2007_

* * *

```
 My new laptop is a Fujitsu-Siemens and when I load the acpi\_fujitsu, some new sysctls appear: hw.acpi.fujitsu.lcd\_brightness: 4 hw.acpi.fujitsu.lcd\_brightness\_radix: 8 But these are named wrong, they should be: hw.backlight.brightness: 4 hw.backlight.brightness\_radix: 8 or something like it. Backlighting is not a vendor specific feature, all laptops with LCD displays have it. If generic stuff like that end up under vendor-specific branches, we will never grow generic tools to handle backlightning but will instead have a tool for each vendor or a maddening list like the lists of SCSI controllers in devd.conf: set scsi-controller-regex "(aac|adv|adw|aha|ahb|ahc|ahd|aic|amd|amr|asr|bt|ciss|ct|dpt|\\ esp|ida|iir|ips|isp|mlx|mly|mpt|ncr|ncv|nsp|stg|sym|trm|wds)\\ \[0-9\]+"; Please don't turn FreeBSD into a nightmare of fragmented bits, just like Linux. -- Poul-Henning Kamp | UNIX since Zilog Zeus 3.20 [phk at FreeBSD.ORG](http://lists.freebsd.org/mailman/listinfo/freebsd-arch) | TCP/IP since RFC 956 FreeBSD committer | BSD since 4.3-tahoe Never attribute to malice what can adequately be explained by incompetence. 
```

* * *

* * *

[More information about the freebsd-arch mailing list](http://lists.freebsd.org/mailman/listinfo/freebsd-arch)  

  
  
from Hacker News https://ift.tt/2Nc81k6