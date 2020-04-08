---
title: 'USN-4211-2: Linux kernel (Xenial HWE) vulnerabilities'
date: 2019-12-03T04:22:00+01:00
draft: false
---

linux-lts-xenial, linux-aws vulnerabilities
-------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 14.04 ESM

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux-aws - Linux kernel for Amazon Web Services (AWS) systems
*   linux-lts-xenial - Linux hardware enablement kernel from Xenial for Trusty

### Details

USN-4211-1 fixed vulnerabilities in the Linux kernel for Ubuntu 16.04 LTS. This update provides the corresponding updates for the Linux Hardware Enablement (HWE) kernel from Ubuntu 16.04 LTS for Ubuntu 14.04 ESM.

Zhipeng Xie discovered that an infinite loop could be triggered in the CFS Linux kernel process scheduler. A local attacker could possibly use this to cause a denial of service. (CVE-2018-20784)

Nicolas Waisman discovered that the WiFi driver stack in the Linux kernel did not properly validate SSID lengths. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-17133)

Nicolas Waisman discovered that the Chelsio T4/T5 RDMA Driver for the Linux kernel performed DMA from a kernel stack. A local attacker could use this to cause a denial of service (system crash). (CVE-2019-17075)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 14.04 ESM

linux-image-4.4.0-1059-aws - 4.4.0-1059.63

linux-image-4.4.0-170-generic - 4.4.0-170.199~14.04.1

linux-image-4.4.0-170-generic-lpae - 4.4.0-170.199~14.04.1

linux-image-4.4.0-170-lowlatency - 4.4.0-170.199~14.04.1

linux-image-4.4.0-170-powerpc-e500mc - 4.4.0-170.199~14.04.1

linux-image-4.4.0-170-powerpc-smp - 4.4.0-170.199~14.04.1

linux-image-4.4.0-170-powerpc64-emb - 4.4.0-170.199~14.04.1

linux-image-4.4.0-170-powerpc64-smp - 4.4.0-170.199~14.04.1

linux-image-aws - 4.4.0.1059.60

linux-image-generic-lpae-lts-xenial - 4.4.0.170.149

linux-image-generic-lts-xenial - 4.4.0.170.149

linux-image-lowlatency-lts-xenial - 4.4.0.170.149

linux-image-powerpc-e500mc-lts-xenial - 4.4.0.170.149

linux-image-powerpc-smp-lts-xenial - 4.4.0.170.149

linux-image-powerpc64-emb-lts-xenial - 4.4.0.170.149

linux-image-powerpc64-smp-lts-xenial - 4.4.0.170.149

linux-image-virtual-lts-xenial - 4.4.0.170.149

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4211-1](https://usn.ubuntu.com/usn/usn-4211-1)
*   [CVE-2018-20784](https://people.canonical.com/~ubuntu-security/cve/CVE-2018-20784)
*   [CVE-2019-17075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17075)
*   [CVE-2019-17133](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17133)

  
  
from Ubuntu Security Notices https://ift.tt/35XiFmC