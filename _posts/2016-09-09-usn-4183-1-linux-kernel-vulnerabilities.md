---
title: 'USN-4183-1: Linux kernel vulnerabilities'
date: 2019-11-13T03:23:00+01:00
draft: false
---

linux, linux-aws, linux-azure, linux-gcp, linux-kvm, linux-oracle, linux-raspi2 vulnerabilities
-----------------------------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10

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

### Details

Stephan van Schaik, Alyssa Milburn, Sebastian Österlund, Pietro Frigo, Kaveh Razavi, Herbert Bos, Cristiano Giuffrida, Giorgi Maisuradze, Moritz Lipp, Michael Schwarz, Daniel Gruss, and Jo Van Bulck discovered that Intel processors using Transactional Synchronization Extensions (TSX) could expose memory contents previously stored in microarchitectural buffers to a malicious process that is executing on the same CPU core. A local attacker could use this to expose sensitive information. (CVE-2019-11135)

It was discovered that the Intel i915 graphics chipsets allowed userspace to modify page table entries via writes to MMIO from the Blitter Command Streamer and expose kernel memory information. A local attacker could use this to expose sensitive information or possibly elevate privileges. (CVE-2019-0155)

Deepak Gupta discovered that on certain Intel processors, the Linux kernel did not properly perform invalidation on page table updates by virtual guest operating systems. A local attacker in a guest VM could use this to cause a denial of service (host system crash). (CVE-2018-12207)

It was discovered that the Intel i915 graphics chipsets could cause a system hang when userspace performed a read from GT memory mapped input output (MMIO) when the product is in certain low power states. A local attacker could use this to cause a denial of service. (CVE-2019-0154)

Jann Horn discovered a reference count underflow in the shiftfs implementation in the Linux kernel. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-15791)

Jann Horn discovered a type confusion vulnerability in the shiftfs implementation in the Linux kernel. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-15792)

Jann Horn discovered that the shiftfs implementation in the Linux kernel did not use the correct file system uid/gid when the user namespace of a lower file system is not in the init user namespace. A local attacker could use this to possibly bypass DAC permissions or have some other unspecified impact. (CVE-2019-15793)

It was discovered that a buffer overflow existed in the 802.11 Wi-Fi configuration interface for the Linux kernel when handling beacon settings. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-16746)

Nico Waisman discovered that a buffer overflow existed in the Realtek Wi-Fi driver for the Linux kernel when handling Notice of Absence frames. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-17666)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[linux-image-5.3.0-1006-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [5.3.0-1006.7](https://launchpad.net/ubuntu/+source/linux-oracle/5.3.0-1006.7)

[linux-image-5.3.0-1007-aws](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.3.0-1007.8](https://launchpad.net/ubuntu/+source/linux-kvm/5.3.0-1007.8)

[linux-image-5.3.0-1007-azure](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.3.0-1007.8](https://launchpad.net/ubuntu/+source/linux-kvm/5.3.0-1007.8)

[linux-image-5.3.0-1007-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.3.0-1007.8](https://launchpad.net/ubuntu/+source/linux-kvm/5.3.0-1007.8)

[linux-image-5.3.0-1008-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.3.0-1008.9](https://launchpad.net/ubuntu/+source/linux-gcp/5.3.0-1008.9)

[linux-image-5.3.0-1012-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [5.3.0-1012.14](https://launchpad.net/ubuntu/+source/linux-raspi2/5.3.0-1012.14)

[linux-image-5.3.0-22-generic](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-22.24](https://launchpad.net/ubuntu/+source/linux/5.3.0-22.24)

[linux-image-5.3.0-22-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-22.24](https://launchpad.net/ubuntu/+source/linux/5.3.0-22.24)

[linux-image-5.3.0-22-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-22.24](https://launchpad.net/ubuntu/+source/linux/5.3.0-22.24)

[linux-image-5.3.0-22-snapdragon](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-22.24](https://launchpad.net/ubuntu/+source/linux/5.3.0-22.24)

linux-image-aws - 5.3.0.1007.9

linux-image-azure - 5.3.0.1007.25

linux-image-gcp - 5.3.0.1008.9

linux-image-generic - 5.3.0.22.26

linux-image-generic-lpae - 5.3.0.22.26

linux-image-gke - 5.3.0.1008.9

linux-image-kvm - 5.3.0.1007.9

linux-image-lowlatency - 5.3.0.22.26

linux-image-oracle - 5.3.0.1006.7

linux-image-raspi2 - 5.3.0.1012.9

linux-image-snapdragon - 5.3.0.22.26

linux-image-virtual - 5.3.0.22.26

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
*   [CVE-2019-15791](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15791)
*   [CVE-2019-15792](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15792)
*   [CVE-2019-15793](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15793)
*   [CVE-2019-16746](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16746)
*   [CVE-2019-17666](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17666)
*   [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA\_MCEPSC\_i915](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA_MCEPSC_i915)

  
  
from Ubuntu Security Notices https://ift.tt/2X64qIW