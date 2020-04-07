---
title: 'USN-4254-2: Linux kernel (Xenial HWE) vulnerabilities'
date: 2020-01-29T02:34:00+01:00
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

USN-4254-1 fixed vulnerabilities in the Linux kernel for Ubuntu 16.04 LTS. This update provides the corresponding updates for the Linux Hardware Enablement (HWE) kernel from Ubuntu 16.04 LTS for Ubuntu 14.04 ESM.

It was discovered that the Linux kernel did not properly clear data structures on context switches for certain Intel graphics processors. A local attacker could use this to expose sensitive information. (CVE-2019-14615)

It was discovered that a race condition existed in the Virtual Video Test Driver in the Linux kernel. An attacker with write access to /dev/video0 on a system with the vivid module loaded could possibly use this to gain administrative privileges. (CVE-2019-18683)

It was discovered that the btrfs file system in the Linux kernel did not properly validate metadata, leading to a NULL pointer dereference. An attacker could use this to specially craft a file system image that, when mounted, could cause a denial of service (system crash). (CVE-2019-18885)

It was discovered that multiple memory leaks existed in the Marvell WiFi-Ex Driver for the Linux kernel. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19057)

It was discovered that the crypto subsystem in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19062)

It was discovered that the Realtek rtlwifi USB device driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19063)

Dan Carpenter discovered that the AppleTalk networking subsystem of the Linux kernel did not properly handle certain error conditions, leading to a NULL pointer dereference. A local attacker could use this to cause a denial of service (system crash). (CVE-2019-19227)

It was discovered that the KVM hypervisor implementation in the Linux kernel did not properly handle ioctl requests to get emulated CPUID features. An attacker with access to /dev/kvm could use this to cause a denial of service (system crash). (CVE-2019-19332)

It was discovered that the B2C2 FlexCop USB device driver in the Linux kernel did not properly validate device metadata. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15291)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 14.04 ESM

linux-image-4.4.0-1061-aws - 4.4.0-1061.65

linux-image-4.4.0-173-generic - 4.4.0-173.203~14.04.1

linux-image-4.4.0-173-generic-lpae - 4.4.0-173.203~14.04.1

linux-image-4.4.0-173-lowlatency - 4.4.0-173.203~14.04.1

linux-image-4.4.0-173-powerpc-e500mc - 4.4.0-173.203~14.04.1

linux-image-4.4.0-173-powerpc-smp - 4.4.0-173.203~14.04.1

linux-image-4.4.0-173-powerpc64-emb - 4.4.0-173.203~14.04.1

linux-image-4.4.0-173-powerpc64-smp - 4.4.0-173.203~14.04.1

linux-image-aws - 4.4.0.1061.62

linux-image-generic-lpae-lts-xenial - 4.4.0.173.152

linux-image-generic-lts-xenial - 4.4.0.173.152

linux-image-lowlatency-lts-xenial - 4.4.0.173.152

linux-image-powerpc-e500mc-lts-xenial - 4.4.0.173.152

linux-image-powerpc-smp-lts-xenial - 4.4.0.173.152

linux-image-powerpc64-emb-lts-xenial - 4.4.0.173.152

linux-image-powerpc64-smp-lts-xenial - 4.4.0.173.152

linux-image-virtual-lts-xenial - 4.4.0.173.152

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4254-1](https://usn.ubuntu.com/usn/usn-4254-1)
*   [CVE-2019-14615](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14615)
*   [CVE-2019-15291](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15291)
*   [CVE-2019-18683](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18683)
*   [CVE-2019-18885](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18885)
*   [CVE-2019-19057](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19057)
*   [CVE-2019-19062](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19062)
*   [CVE-2019-19063](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19063)
*   [CVE-2019-19227](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19227)
*   [CVE-2019-19332](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19332)

  
  
from Ubuntu Security Notices https://ift.tt/2U0k0q1