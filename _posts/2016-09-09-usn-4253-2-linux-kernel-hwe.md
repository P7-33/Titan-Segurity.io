---
title: 'USN-4253-2: Linux kernel (HWE) vulnerability'
date: 2020-01-29T02:34:00+01:00
draft: false
---

linux-hwe vulnerability
-----------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 18.04 LTS

### Summary

he Linux kernel could be made to expose sensitive information.

### Software Description

*   linux-hwe - Linux hardware enablement (HWE) kernel

### Details

USN-4253-1 fixed vulnerabilities in the Linux kernel for Ubuntu 19.10. This update provides the corresponding updates for the Linux Hardware Enablement (HWE) kernel from Ubuntu 19.10 for Ubuntu 18.04 LTS.

It was discovered that the Linux kernel did not properly clear data structures on context switches for certain Intel graphics processors. A local attacker could use this to expose sensitive information.

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS

[linux-image-5.3.0-28-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0-28.30~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

[linux-image-5.3.0-28-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0-28.30~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

[linux-image-5.3.0-28-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0-28.30~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

[linux-image-generic-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.28.96](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

[linux-image-generic-lpae-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.28.96](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

[linux-image-lowlatency-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.28.96](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

[linux-image-snapdragon-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.28.96](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

[linux-image-virtual-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.28.96](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-28.30~18.04.1)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4253-1](https://usn.ubuntu.com/usn/usn-4253-1)
*   [CVE-2019-14615](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14615)

  
  
from Ubuntu Security Notices https://ift.tt/37AhGdl