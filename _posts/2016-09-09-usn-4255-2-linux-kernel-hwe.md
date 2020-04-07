---
title: 'USN-4255-2: Linux kernel (HWE) vulnerabilities'
date: 2020-01-29T02:34:00+01:00
draft: false
---

linux-hwe, linux-aws-hwe vulnerabilities
----------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux-aws-hwe - Linux kernel for Amazon Web Services (AWS-HWE) systems
*   linux-hwe - Linux hardware enablement (HWE) kernel

### Details

USN-4255-1 fixed vulnerabilities in the Linux kernel for Ubuntu 18.04 LTS. This update provides the corresponding updates for the Linux Hardware Enablement (HWE) kernel from Ubuntu 18.04 LTS for Ubuntu 16.04 LTS.

It was discovered that the Linux kernel did not properly clear data structures on context switches for certain Intel graphics processors. A local attacker could use this to expose sensitive information. (CVE-2019-14615)

It was discovered that a race condition can lead to a use-after-free while destroying GEM contexts in the i915 driver for the Linux kernel. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2020-7053)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 16.04 LTS

[linux-image-4.15.0-1058-aws](https://launchpad.net/ubuntu/+source/linux-aws-hwe) - [4.15.0-1058.60~16.04.1](https://launchpad.net/ubuntu/+source/linux-aws-hwe/4.15.0-1058.60~16.04.1)

[linux-image-4.15.0-76-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-76.86~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-76.86~16.04.1)

[linux-image-4.15.0-76-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-76.86~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-76.86~16.04.1)

[linux-image-4.15.0-76-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-76.86~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-76.86~16.04.1)

linux-image-aws-hwe - 4.15.0.1058.58

linux-image-generic-hwe-16.04 - 4.15.0.76.96

linux-image-generic-lpae-hwe-16.04 - 4.15.0.76.96

linux-image-lowlatency-hwe-16.04 - 4.15.0.76.96

linux-image-oem - 4.15.0.76.96

linux-image-virtual-hwe-16.04 - 4.15.0.76.96

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4255-1](https://usn.ubuntu.com/usn/usn-4255-1)
*   [CVE-2019-14615](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14615)
*   [CVE-2020-7053](https://people.canonical.com/~ubuntu-security/cve/CVE-2020-7053)

  
  
from Ubuntu Security Notices https://ift.tt/2tZKlJZ