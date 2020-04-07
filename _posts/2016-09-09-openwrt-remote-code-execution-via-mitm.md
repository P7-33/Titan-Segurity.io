---
title: 'OpenWRT remote code execution via MITM due to bug in package manager'
date: 2020-02-01T02:13:00+01:00
draft: false
---

\[OpenWrt-Devel\] Security Advisory 2020-01-31-1 - Opkg susceptible to MITM (CVE-2020-7982)
===========================================================================================

**Jo-Philipp Wich** [jo at mein.io](mailto:openwrt-devel%40lists.openwrt.org?Subject=Re:%20Re%3A%20%5BOpenWrt-Devel%5D%20Security%20Advisory%202020-01-31-1%20-%20Opkg%20susceptible%0A%20to%20MITM%20%28CVE-2020-7982%29&In-Reply-To=%3Cf44cc4eb-5e77-ec3d-f22b-2292cc133376%40wwsnet.net%3E "[OpenWrt-Devel] Security Advisory 2020-01-31-1 - Opkg susceptible to MITM (CVE-2020-7982)")  
_Fri Jan 31 13:54:07 PST 2020_

* * *

```
DESCRIPTION A bug in the package list parse logic of OpenWrt's opkg fork caused the package manager to ignore SHA-256 checksums embedded in the signed repository index, effectively bypassing integrity checking of downloaded .ipk artifacts. The bug has been introduced with commit [https://git.openwrt.org/54cc7e3](https://git.openwrt.org/54cc7e3) which failed to advance the proper string pointer when skipping the leading white- space portition of the checksum string, causing the subsequent hex decoding loop to return early with a zero length checksum. Due to the fact that opkg on OpenWrt runs as root and has write access to the entire filesystem, arbitrary code could be injected by the means of forged .ipk packages with malicious payload. CVE-2020-7982 has been assigned to this issue. REQUIREMENTS In order to exploit this vulnerability, a malicious actor needs to pose as MITM, serving a valid and signed package index - e.g. one obtained from downloads.openwrt.org - and one or more forged .ipk packages having the same size as specified in the repository index while an \`opkg install\` command is invoked on the victim system. MITIGATIONS To fix this issue, upgrade to the latest OpenWrt version. The fix is contained in the following and later OpenWrt releases: \* OpenWrt master: 2020-01-29 reboot-12146-gc69c20c667 \* OpenWrt 19.07: 2019-01-29 v19.07.1-1-g4668ae3bed \* OpenWrt 18.06: 2019-01-29 v18.06.7-1-g6bfde67581 The fixed opkg package will carry the version 2020-01-25. Alternatively, to update the opkg package itself without upgrading the entire firmware, the following commands may be used once all repositories have been updated: cd /tmp opkg update opkg download opkg zcat ./opkg-lists/openwrt\_base | grep -A10 "Package: opkg" | grep SHA256sum sha256sum ./opkg\_2020-01-25-c09fe209-1\_\*.ipk Compare both checksums and, if matching, proceed with installing the package: opkg install ./opkg\_2020-01-25-c09fe209-1\_\*.ipk AFFECTED VERSIONS To our knowledge, OpenWrt versions 18.06.0 to 18.06.6 and 19.07.0 as well as LEDE 17.01.0 to 17.01.7 are affected. The fixed packages are integrated in the OpenWrt 18.06.7, OpenWrt 19.07.1 and subsequent releases. Older versions of OpenWrt (e.g. OpenWrt 15.05 and LEDE 17.01) are end of life and not supported any more. CREDITS The issue was discovered by Guido Vranken for ForAllSecure, Inc. -------------- next part -------------- A non-text attachment was scrubbed... Name: signature.asc Type: application/pgp-signature Size: 833 bytes Desc: OpenPGP digital signature URL: <[http://lists.infradead.org/pipermail/openwrt-devel/attachments/20200131/1629c8c7/attachment.sig](http://lists.infradead.org/pipermail/openwrt-devel/attachments/20200131/1629c8c7/attachment.sig)\> 
```

* * *

* * *

[More information about the openwrt-devel mailing list](http://lists.infradead.org/mailman/listinfo/openwrt-devel)  

  
  
from Hacker News https://ift.tt/36LRUSb