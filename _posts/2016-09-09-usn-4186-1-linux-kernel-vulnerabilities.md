---
title: 'USN-4186-1: Linux kernel vulnerabilities'
date: 2019-11-13T03:23:00+01:00
draft: false
---

linux, linux-aws, linux-kvm vulnerabilities
-------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux - Linux kernel
*   linux-aws - Linux kernel for Amazon Web Services (AWS) systems
*   linux-kvm - Linux kernel for cloud environments

### Details

Stephan van Schaik, Alyssa Milburn, Sebastian Österlund, Pietro Frigo, Kaveh Razavi, Herbert Bos, Cristiano Giuffrida, Giorgi Maisuradze, Moritz Lipp, Michael Schwarz, Daniel Gruss, and Jo Van Bulck discovered that Intel processors using Transactional Synchronization Extensions (TSX) could expose memory contents previously stored in microarchitectural buffers to a malicious process that is executing on the same CPU core. A local attacker could use this to expose sensitive information. (CVE-2019-11135)

It was discovered that the Intel i915 graphics chipsets allowed userspace to modify page table entries via writes to MMIO from the Blitter Command Streamer and expose kernel memory information. A local attacker could use this to expose sensitive information or possibly elevate privileges. (CVE-2019-0155)

Deepak Gupta discovered that on certain Intel processors, the Linux kernel did not properly perform invalidation on page table updates by virtual guest operating systems. A local attacker in a guest VM could use this to cause a denial of service (host system crash). (CVE-2018-12207)

It was discovered that the Intel i915 graphics chipsets could cause a system hang when userspace performed a read from GT memory mapped input output (MMIO) when the product is in certain low power states. A local attacker could use this to cause a denial of service. (CVE-2019-0154)

Hui Peng discovered that the Atheros AR6004 USB Wi-Fi device driver for the Linux kernel did not properly validate endpoint descriptors returned by the device. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15098)

It was discovered that a buffer overflow existed in the 802.11 Wi-Fi configuration interface for the Linux kernel when handling beacon settings. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-16746)

Ori Nimron discovered that the AX25 network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17052)

Ori Nimron discovered that the IEEE 802.15.4 Low-Rate Wireless network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17053)

Ori Nimron discovered that the Appletalk network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17054)

Ori Nimron discovered that the modular ISDN network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17055)

Ori Nimron discovered that the Near field Communication (NFC) network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17056)

Nico Waisman discovered that a buffer overflow existed in the Realtek Wi-Fi driver for the Linux kernel when handling Notice of Absence frames. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-17666)

Maddie Stone discovered that the Binder IPC Driver implementation in the Linux kernel contained a use-after-free vulnerability. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-2215)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 16.04 LTS

[linux-image-4.4.0-1062-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [4.4.0-1062.69](https://launchpad.net/ubuntu/+source/linux-kvm/4.4.0-1062.69)

[linux-image-4.4.0-1098-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [4.4.0-1098.109](https://launchpad.net/ubuntu/+source/linux-aws/4.4.0-1098.109)

[linux-image-4.4.0-168-generic](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-168.197](https://launchpad.net/ubuntu/+source/linux/4.4.0-168.197)

[linux-image-4.4.0-168-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-168.197](https://launchpad.net/ubuntu/+source/linux/4.4.0-168.197)

[linux-image-4.4.0-168-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-168.197](https://launchpad.net/ubuntu/+source/linux/4.4.0-168.197)

[linux-image-4.4.0-168-powerpc-e500mc](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-168.197](https://launchpad.net/ubuntu/+source/linux/4.4.0-168.197)

[linux-image-4.4.0-168-powerpc-smp](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-168.197](https://launchpad.net/ubuntu/+source/linux/4.4.0-168.197)

[linux-image-4.4.0-168-powerpc64-emb](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-168.197](https://launchpad.net/ubuntu/+source/linux/4.4.0-168.197)

[linux-image-4.4.0-168-powerpc64-smp](https://launchpad.net/ubuntu/+source/linux) - [4.4.0-168.197](https://launchpad.net/ubuntu/+source/linux/4.4.0-168.197)

linux-image-aws - 4.4.0.1098.102

linux-image-generic - 4.4.0.168.176

linux-image-generic-lpae - 4.4.0.168.176

linux-image-kvm - 4.4.0.1062.62

linux-image-lowlatency - 4.4.0.168.176

linux-image-powerpc-e500mc - 4.4.0.168.176

linux-image-powerpc-smp - 4.4.0.168.176

linux-image-powerpc64-emb - 4.4.0.168.176

linux-image-powerpc64-smp - 4.4.0.168.176

linux-image-virtual - 4.4.0.168.176

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
*   [CVE-2019-16746](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16746)
*   [CVE-2019-17052](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17052)
*   [CVE-2019-17053](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17053)
*   [CVE-2019-17054](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17054)
*   [CVE-2019-17055](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17055)
*   [CVE-2019-17056](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17056)
*   [CVE-2019-17666](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17666)
*   [CVE-2019-2215](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2215)
*   [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA\_MCEPSC\_i915](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA_MCEPSC_i915)

  
  
from Ubuntu Security Notices https://ift.tt/2KdJbiT