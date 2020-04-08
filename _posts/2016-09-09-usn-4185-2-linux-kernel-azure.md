---
title: 'USN-4185-2: Linux kernel (Azure) vulnerabilities'
date: 2019-11-13T03:23:00+01:00
draft: false
---

linux-azure vulnerabilities
---------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 14.04 ESM

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux-azure - Linux kernel for Microsoft Azure Cloud systems

### Details

Stephan van Schaik, Alyssa Milburn, Sebastian Österlund, Pietro Frigo, Kaveh Razavi, Herbert Bos, Cristiano Giuffrida, Giorgi Maisuradze, Moritz Lipp, Michael Schwarz, Daniel Gruss, and Jo Van Bulck discovered that Intel processors using Transactional Synchronization Extensions (TSX) could expose memory contents previously stored in microarchitectural buffers to a malicious process that is executing on the same CPU core. A local attacker could use this to expose sensitive information. (CVE-2019-11135)

Deepak Gupta discovered that on certain Intel processors, the Linux kernel did not properly perform invalidation on page table updates by virtual guest operating systems. A local attacker in a guest VM could use this to cause a denial of service (host system crash). (CVE-2018-12207)

Ori Nimron discovered that the AX25 network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17052)

Ori Nimron discovered that the IEEE 802.15.4 Low-Rate Wireless network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17053)

Ori Nimron discovered that the Appletalk network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17054)

Ori Nimron discovered that the modular ISDN network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17055)

Ori Nimron discovered that the Near field Communication (NFC) network protocol implementation in the Linux kernel did not properly perform permissions checks. A local attacker could use this to create a raw socket. (CVE-2019-17056)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 14.04 ESM

linux-image-4.15.0-1063-azure - 4.15.0-1063.68~14.04.1

linux-image-azure - 4.15.0.1063.49

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

Please note that mitigating the TSX (CVE-2019-11135) issue requires a corresponding Intel processor microcode update.

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4185-1](https://usn.ubuntu.com/usn/usn-4185-1)
*   [CVE-2018-12207](https://people.canonical.com/~ubuntu-security/cve/CVE-2018-12207)
*   [CVE-2019-11135](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11135)
*   [CVE-2019-17052](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17052)
*   [CVE-2019-17053](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17053)
*   [CVE-2019-17054](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17054)
*   [CVE-2019-17055](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17055)
*   [CVE-2019-17056](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17056)
*   [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA\_MCEPSC\_i915](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA_MCEPSC_i915)

  
  
from Ubuntu Security Notices https://ift.tt/2CEieAX