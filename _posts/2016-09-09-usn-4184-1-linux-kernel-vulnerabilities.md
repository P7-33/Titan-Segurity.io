---
title: 'USN-4184-1: Linux kernel vulnerabilities'
date: 2019-11-13T03:23:00+01:00
draft: false
---

linux, linux-aws, linux-azure, linux-gcp, linux-gke-5.0, linux-hwe, linux-kvm, linux-oem-osp1, linux-oracle, linux-raspi2 vulnerabilities
-----------------------------------------------------------------------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.04
*   Ubuntu 18.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux - Linux kernel
*   linux-aws - Linux kernel for Amazon Web Services (AWS) systems
*   linux-azure - Linux kernel for Microsoft Azure Cloud systems
*   linux-gcp - Linux kernel for Google Cloud Platform (GCP) systems
*   linux-kvm - Linux kernel for cloud environments
*   linux-oracle - Linux kernel for Oracle Cloud systems
*   linux-raspi2 - Linux kernel for Raspberry Pi 2
*   linux-gke-5.0 - Linux kernel for Google Container Engine (GKE) systems
*   linux-hwe - Linux hardware enablement (HWE) kernel
*   linux-oem-osp1 - Linux kernel for OEM processors

### Details

Stephan van Schaik, Alyssa Milburn, Sebastian Österlund, Pietro Frigo, Kaveh Razavi, Herbert Bos, Cristiano Giuffrida, Giorgi Maisuradze, Moritz Lipp, Michael Schwarz, Daniel Gruss, and Jo Van Bulck discovered that Intel processors using Transactional Synchronization Extensions (TSX) could expose memory contents previously stored in microarchitectural buffers to a malicious process that is executing on the same CPU core. A local attacker could use this to expose sensitive information. (CVE-2019-11135)

It was discovered that the Intel i915 graphics chipsets allowed userspace to modify page table entries via writes to MMIO from the Blitter Command Streamer and expose kernel memory information. A local attacker could use this to expose sensitive information or possibly elevate privileges. (CVE-2019-0155)

Deepak Gupta discovered that on certain Intel processors, the Linux kernel did not properly perform invalidation on page table updates by virtual guest operating systems. A local attacker in a guest VM could use this to cause a denial of service (host system crash). (CVE-2018-12207)

It was discovered that the Intel i915 graphics chipsets could cause a system hang when userspace performed a read from GT memory mapped input output (MMIO) when the product is in certain low power states. A local attacker could use this to cause a denial of service. (CVE-2019-0154)

Hui Peng discovered that the Atheros AR6004 USB Wi-Fi device driver for the Linux kernel did not properly validate endpoint descriptors returned by the device. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15098)

Jann Horn discovered a reference count underflow in the shiftfs implementation in the Linux kernel. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-15791)

Jann Horn discovered a type confusion vulnerability in the shiftfs implementation in the Linux kernel. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-15792)

Jann Horn discovered that the shiftfs implementation in the Linux kernel did not use the correct file system uid/gid when the user namespace of a lower file system is not in the init user namespace. A local attacker could use this to possibly bypass DAC permissions or have some other unspecified impact. (CVE-2019-15793)

Ori Nimron discovered that the AX25 network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17052)

Ori Nimron discovered that the IEEE 802.15.4 Low-Rate Wireless network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17053)

Ori Nimron discovered that the Appletalk network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17054)

Ori Nimron discovered that the modular ISDN network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17055)

Ori Nimron discovered that the Near field Communication (NFC) network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17056)

Nico Waisman discovered that a buffer overflow existed in the Realtek Wi-Fi driver for the Linux kernel when handling Notice of Absence frames. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-17666)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.04

[linux-image-5.0.0-1007-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [5.0.0-1007.12](https://launchpad.net/ubuntu/+source/linux-oracle/5.0.0-1007.12)

[linux-image-5.0.0-1021-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [5.0.0-1021.24](https://launchpad.net/ubuntu/+source/linux-aws/5.0.0-1021.24)

[linux-image-5.0.0-1022-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.0.0-1022.24](https://launchpad.net/ubuntu/+source/linux-kvm/5.0.0-1022.24)

[linux-image-5.0.0-1022-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [5.0.0-1022.23](https://launchpad.net/ubuntu/+source/linux-raspi2/5.0.0-1022.23)

[linux-image-5.0.0-1025-azure](https://launchpad.net/ubuntu/+source/linux-azure) - [5.0.0-1025.27](https://launchpad.net/ubuntu/+source/linux-azure/5.0.0-1025.27)

[linux-image-5.0.0-1025-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1025.26](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1025.26)

[linux-image-5.0.0-35-generic](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-35.38](https://launchpad.net/ubuntu/+source/linux/5.0.0-35.38)

[linux-image-5.0.0-35-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-35.38](https://launchpad.net/ubuntu/+source/linux/5.0.0-35.38)

[linux-image-5.0.0-35-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-35.38](https://launchpad.net/ubuntu/+source/linux/5.0.0-35.38)

linux-image-aws - 5.0.0.1021.23

linux-image-azure - 5.0.0.1025.25

linux-image-gcp - 5.0.0.1025.50

linux-image-generic - 5.0.0.35.37

linux-image-generic-lpae - 5.0.0.35.37

linux-image-gke - 5.0.0.1025.50

linux-image-kvm - 5.0.0.1022.23

linux-image-lowlatency - 5.0.0.35.37

linux-image-oracle - 5.0.0.1007.33

linux-image-raspi2 - 5.0.0.1022.20

linux-image-virtual - 5.0.0.35.37

Ubuntu 18.04 LTS

[linux-image-5.0.0-1025-azure](https://launchpad.net/ubuntu/+source/linux-azure) - [5.0.0-1025.27~18.04.1](https://launchpad.net/ubuntu/+source/linux-azure/5.0.0-1025.27~18.04.1)

[linux-image-5.0.0-1025-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1025.26~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1025.26~18.04.1)

[linux-image-5.0.0-1025-gke](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1025.26~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1025.26~18.04.1)

[linux-image-5.0.0-1027-oem-osp1](https://launchpad.net/ubuntu/+source/linux-oem-osp1) - [5.0.0-1027.31](https://launchpad.net/ubuntu/+source/linux-oem-osp1/5.0.0-1027.31)

[linux-image-5.0.0-35-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-35.38~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-35.38~18.04.1)

[linux-image-5.0.0-35-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-35.38~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-35.38~18.04.1)

[linux-image-5.0.0-35-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-35.38~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-35.38~18.04.1)

linux-image-azure - 5.0.0.1025.36

linux-image-gcp - 5.0.0.1025.29

linux-image-generic-hwe-18.04 - 5.0.0.35.93

linux-image-generic-lpae-hwe-18.04 - 5.0.0.35.93

linux-image-gke-5.0 - 5.0.0.1025.14

linux-image-lowlatency-hwe-18.04 - 5.0.0.35.93

linux-image-oem-osp1 - 5.0.0.1027.31

linux-image-snapdragon-hwe-18.04 - 5.0.0.35.93

linux-image-virtual-hwe-18.04 - 5.0.0.35.93

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

Please note that mitigating the TSX (CVE-2019-11135) and i915 (CVE-2019-0154) issues requires corresponding microcode and graphics firmware updates respectively.

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2018-12207](https://people.canonical.com/~ubuntu-security/cve/CVE-2018-12207)
*   [CVE-2019-0154](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-0154)
*   [CVE-2019-0155](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-0155)
*   [CVE-2019-11135](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11135)
*   [CVE-2019-15098](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15098)
*   [CVE-2019-15791](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15791)
*   [CVE-2019-15792](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15792)
*   [CVE-2019-15793](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15793)
*   [CVE-2019-17052](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17052)
*   [CVE-2019-17053](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17053)
*   [CVE-2019-17054](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17054)
*   [CVE-2019-17055](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17055)
*   [CVE-2019-17056](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17056)
*   [CVE-2019-17666](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17666)
*   [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA\_MCEPSC\_i915](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA_MCEPSC_i915)

  
  
from Ubuntu Security Notices https://ift.tt/34YUqDM