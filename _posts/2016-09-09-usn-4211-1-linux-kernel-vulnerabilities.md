---
title: 'USN-4211-1: Linux kernel vulnerabilities'
date: 2019-12-03T04:22:00+01:00
draft: false
---

linux, linux-aws, linux-kvm, linux-raspi2, linux-snapdragon vulnerabilities
---------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux - Linux kernel
*   linux-aws - Linux kernel for Amazon Web Services (AWS) systems
*   linux-kvm - Linux kernel for cloud environments
*   linux-raspi2 - Linux kernel for Raspberry Pi 2
*   linux-snapdragon - Linux kernel for Snapdragon processors

### Details

Zhipeng Xie discovered that an infinite loop could be triggered in the CFS Linux kernel process scheduler. A local attacker could possibly use this to cause a denial of service. (CVE-2018-20784)

Nicolas Waisman discovered that the WiFi driver stack in the Linux kernel did not properly validate SSID lengths. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-17133)

Nicolas Waisman discovered that the Chelsio T4/T5 RDMA Driver for the Linux kernel performed DMA from a kernel stack. A local attacker could use this to cause a denial of service (system crash). (CVE-2019-17075)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 16.04 LTS

[linux-image-4.4.0-1063-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [4.4.0-1063.70](https://launchpad.net/ubuntu/+source/linux-kvm/4.4.0-1063.70)

[linux-image-4.4.0-1099-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [4.4.0-1099.110](https://launchpad.net/ubuntu/+source/linux-aws/4.4.0-1099.110)

[linux-image-4.4.0-1126-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [4.4.0-1126.135](https://launchpad.net/ubuntu/+source/linux-raspi2/4.4.0-1126.135)

[linux-image-4.4.0-1130-snapdragon](https://launchpad.net/ubuntu/+source/linux-snapdragon) - [4.4.0-1130.138](https://launchpad.net/ubuntu/+source/linux-snapdragon/4.4.0-1130.138)

[linux-image-4.4.0-170-generic](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-170.199](https://launchpad.net/ubuntu/+source/linux/4.4.0-170.199)

[linux-image-4.4.0-170-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-170.199](https://launchpad.net/ubuntu/+source/linux/4.4.0-170.199)

[linux-image-4.4.0-170-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-170.199](https://launchpad.net/ubuntu/+source/linux/4.4.0-170.199)

[linux-image-4.4.0-170-powerpc-e500mc](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-170.199](https://launchpad.net/ubuntu/+source/linux/4.4.0-170.199)

[linux-image-4.4.0-170-powerpc-smp](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-170.199](https://launchpad.net/ubuntu/+source/linux/4.4.0-170.199)

[linux-image-4.4.0-170-powerpc64-emb](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-170.199](https://launchpad.net/ubuntu/+source/linux/4.4.0-170.199)

[linux-image-4.4.0-170-powerpc64-smp](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-170.199](https://launchpad.net/ubuntu/+source/linux/4.4.0-170.199)

linux-image-aws - 4.4.0.1099.103

linux-image-generic - 4.4.0.170.178

linux-image-generic-lpae - 4.4.0.170.178

linux-image-kvm - 4.4.0.1063.63

linux-image-lowlatency - 4.4.0.170.178

linux-image-powerpc-e500mc - 4.4.0.170.178

linux-image-powerpc-smp - 4.4.0.170.178

linux-image-powerpc64-emb - 4.4.0.170.178

linux-image-powerpc64-smp - 4.4.0.170.178

linux-image-raspi2 - 4.4.0.1126.126

linux-image-snapdragon - 4.4.0.1130.122

linux-image-virtual - 4.4.0.170.178

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2018-20784](https://people.canonical.com/~ubuntu-security/cve/CVE-2018-20784)
*   [CVE-2019-17075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17075)
*   [CVE-2019-17133](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17133)

  
  
from Ubuntu Security Notices https://ift.tt/2rRXinG