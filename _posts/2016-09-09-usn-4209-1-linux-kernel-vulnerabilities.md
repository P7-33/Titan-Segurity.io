---
title: 'USN-4209-1: Linux kernel vulnerabilities'
date: 2019-12-03T04:22:00+01:00
draft: false
---

linux, linux-aws, linux-aws-5.0, linux-gcp, linux-gke-5.0, linux-hwe, linux-kvm, linux-oem-osp1, linux-oracle, linux-oracle-5.0, linux-raspi2 vulnerabilities
-------------------------------------------------------------------------------------------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.04
*   Ubuntu 18.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux - Linux kernel
*   linux-aws - Linux kernel for Amazon Web Services (AWS) systems
*   linux-gcp - Linux kernel for Google Cloud Platform (GCP) systems
*   linux-kvm - Linux kernel for cloud environments
*   linux-oracle - Linux kernel for Oracle Cloud systems
*   linux-raspi2 - Linux kernel for Raspberry Pi 2
*   linux-aws-5.0 - Linux kernel for Amazon Web Services (AWS) systems
*   linux-gke-5.0 - Linux kernel for Google Container Engine (GKE) systems
*   linux-hwe - Linux hardware enablement (HWE) kernel
*   linux-oem-osp1 - Linux kernel for OEM processors
*   linux-oracle-5.0 - Linux kernel for Oracle Cloud systems

### Details

Jann Horn discovered that the OverlayFS and ShiftFS Drivers in the Linux kernel did not properly handle reference counting during memory mapping operations when used in conjunction with AUFS. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-15794)

It was discovered that a buffer overflow existed in the 802.11 Wi-Fi configuration interface for the Linux kernel when handling beacon settings. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-16746)

It was discovered that there was a memory leak in the Advanced Buffer Management functionality of the Netronome NFP4000/NFP6000 NIC Driver in the Linux kernel during certain error scenarios. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19076)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.04

[linux-image-5.0.0-1008-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [5.0.0-1008.13](https://launchpad.net/ubuntu/+source/linux-oracle/5.0.0-1008.13)

[linux-image-5.0.0-1022-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [5.0.0-1022.25](https://launchpad.net/ubuntu/+source/linux-aws/5.0.0-1022.25)

[linux-image-5.0.0-1023-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.0.0-1023.25](https://launchpad.net/ubuntu/+source/linux-kvm/5.0.0-1023.25)

[linux-image-5.0.0-1023-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [5.0.0-1023.24](https://launchpad.net/ubuntu/+source/linux-raspi2/5.0.0-1023.24)

[linux-image-5.0.0-1026-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1026.27](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1026.27)

[linux-image-5.0.0-37-generic](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-37.40](https://launchpad.net/ubuntu/+source/linux/5.0.0-37.40)

[linux-image-5.0.0-37-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-37.40](https://launchpad.net/ubuntu/+source/linux/5.0.0-37.40)

[linux-image-5.0.0-37-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-37.40](https://launchpad.net/ubuntu/+source/linux/5.0.0-37.40)

linux-image-aws - 5.0.0.1022.24

linux-image-gcp - 5.0.0.1026.51

linux-image-generic - 5.0.0.37.39

linux-image-generic-lpae - 5.0.0.37.39

linux-image-gke - 5.0.0.1026.51

linux-image-kvm - 5.0.0.1023.24

linux-image-lowlatency - 5.0.0.37.39

linux-image-oracle - 5.0.0.1008.34

linux-image-raspi2 - 5.0.0.1023.21

linux-image-virtual - 5.0.0.37.39

Ubuntu 18.04 LTS

[linux-image-5.0.0-1008-oracle](https://launchpad.net/ubuntu/+source/linux-oracle-5.0) - [5.0.0-1008.13~18.04.1](https://launchpad.net/ubuntu/+source/linux-oracle-5.0/5.0.0-1008.13~18.04.1)

[linux-image-5.0.0-1022-aws](https://launchpad.net/ubuntu/+source/linux-aws-5.0) - [5.0.0-1022.25~18.04.1](https://launchpad.net/ubuntu/+source/linux-aws-5.0/5.0.0-1022.25~18.04.1)

[linux-image-5.0.0-1026-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1026.27~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1026.27~18.04.1)

[linux-image-5.0.0-1026-gke](https://launchpad.net/ubuntu/+source/linux-gke-5.0) - [5.0.0-1026.27~18.04.2](https://launchpad.net/ubuntu/+source/linux-gke-5.0/5.0.0-1026.27~18.04.2)

[linux-image-5.0.0-1030-oem-osp1](https://launchpad.net/ubuntu/+source/linux-oem-osp1) - [5.0.0-1030.34](https://launchpad.net/ubuntu/+source/linux-oem-osp1/5.0.0-1030.34)

[linux-image-5.0.0-37-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-37.40~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-37.40~18.04.1)

[linux-image-5.0.0-37-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-37.40~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-37.40~18.04.1)

[linux-image-5.0.0-37-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-37.40~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-37.40~18.04.1)

linux-image-aws-edge - 5.0.0.1022.36

linux-image-gcp - 5.0.0.1026.30

linux-image-generic-hwe-18.04 - 5.0.0.37.95

linux-image-generic-lpae-hwe-18.04 - 5.0.0.37.95

linux-image-gke-5.0 - 5.0.0.1026.15

linux-image-lowlatency-hwe-18.04 - 5.0.0.37.95

linux-image-oem-osp1 - 5.0.0.1030.34

linux-image-oracle-edge - 5.0.0.1008.7

linux-image-snapdragon-hwe-18.04 - 5.0.0.37.95

linux-image-virtual-hwe-18.04 - 5.0.0.37.95

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2019-15794](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15794)
*   [CVE-2019-16746](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16746)
*   [CVE-2019-19076](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19076)

  
  
from Ubuntu Security Notices https://ift.tt/2YajOEr