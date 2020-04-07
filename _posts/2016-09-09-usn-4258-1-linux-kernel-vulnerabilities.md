---
title: 'USN-4258-1: Linux kernel vulnerabilities'
date: 2020-01-29T02:34:00+01:00
draft: false
---

linux-aws-5.0, linux-gcp, linux-gke-5.0, linux-oracle-5.0 vulnerabilities
-------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 18.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux-aws-5.0 - Linux kernel for Amazon Web Services (AWS) systems
*   linux-gcp - Linux kernel for Google Cloud Platform (GCP) systems
*   linux-gke-5.0 - Linux kernel for Google Container Engine (GKE) systems
*   linux-oracle-5.0 - Linux kernel for Oracle Cloud systems

### Details

It was discovered that the Atheros 802.11ac wireless USB device driver in the Linux kernel did not properly validate device metadata. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15099)

It was discovered that a race condition existed in the Virtual Video Test Driver in the Linux kernel. An attacker with write access to /dev/video0 on a system with the vivid module loaded could possibly use this to gain administrative privileges. (CVE-2019-18683)

It was discovered that the btrfs file system in the Linux kernel did not properly validate metadata, leading to a NULL pointer dereference. An attacker could use this to specially craft a file system image that, when mounted, could cause a denial of service (system crash). (CVE-2019-18885)

It was discovered that the crypto subsystem in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19050, CVE-2019-19062)

It was discovered that the RSI 91x WLAN device driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19071)

It was discovered that the Broadcom Netxtreme HCA device driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19077)

It was discovered that the Atheros 802.11ac wireless USB device driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19078)

It was discovered that the Qualcomm IPC Router TUN device driver in the Linux kernel did not properly deallocate memory in certain situations. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19079)

It was discovered that the AMD GPU device drivers in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to possibly cause a denial of service (kernel memory exhaustion). (CVE-2019-19082)

Dan Carpenter discovered that the AppleTalk networking subsystem of the Linux kernel did not properly handle certain error conditions, leading to a NULL pointer dereference. A local attacker could use this to cause a denial of service (system crash). (CVE-2019-19227)

Or Cohen discovered that the virtual console subsystem in the Linux kernel did not properly restrict writes to unimplemented vcsu (unicode) devices. A local attacker could possibly use this to cause a denial of service (system crash) or have other unspecified impacts. (CVE-2019-19252)

It was discovered that the KVM hypervisor implementation in the Linux kernel did not properly handle ioctl requests to get emulated CPUID features. An attacker with access to /dev/kvm could use this to cause a denial of service (system crash). (CVE-2019-19332)

It was discovered that the ext4 file system implementation in the Linux kernel did not properly handle certain conditions. An attacker could use this to specially craft an ext4 file system that, when mounted, could cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19767)

It was discovered that the B2C2 FlexCop USB device driver in the Linux kernel did not properly validate device metadata. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15291)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS

[linux-image-5.0.0-1010-oracle](https://launchpad.net/ubuntu/+source/linux-oracle-5.0) - [5.0.0-1010.15~18.04.1](https://launchpad.net/ubuntu/+source/linux-oracle-5.0/5.0.0-1010.15~18.04.1)

[linux-image-5.0.0-1024-aws](https://launchpad.net/ubuntu/+source/linux-aws-5.0) - [5.0.0-1024.27~18.04.1](https://launchpad.net/ubuntu/+source/linux-aws-5.0/5.0.0-1024.27~18.04.1)

[linux-image-5.0.0-1029-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1029.30~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1029.30~18.04.1)

[linux-image-5.0.0-1029-gke](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1029.30~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1029.30~18.04.1)

linux-image-aws-edge - 5.0.0.1024.38

linux-image-gcp - 5.0.0.1029.33

linux-image-gke-5.0 - 5.0.0.1029.17

linux-image-oracle-edge - 5.0.0.1010.9

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2019-15099](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15099)
*   [CVE-2019-15291](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15291)
*   [CVE-2019-18683](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18683)
*   [CVE-2019-18885](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18885)
*   [CVE-2019-19050](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19050)
*   [CVE-2019-19062](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19062)
*   [CVE-2019-19071](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19071)
*   [CVE-2019-19077](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19077)
*   [CVE-2019-19078](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19078)
*   [CVE-2019-19079](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19079)
*   [CVE-2019-19082](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19082)
*   [CVE-2019-19227](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19227)
*   [CVE-2019-19252](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19252)
*   [CVE-2019-19332](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19332)
*   [CVE-2019-19767](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19767)

  
  
from Ubuntu Security Notices https://ift.tt/36AIngk