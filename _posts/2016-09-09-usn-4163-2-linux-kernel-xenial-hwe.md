---
title: 'USN-4163-2: Linux kernel (Xenial HWE) vulnerabilities'
date: 2019-10-23T05:38:00+01:00
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

USN-4163-1 fixed vulnerabilities in the Linux kernel for Ubuntu 16.04 LTS. This update provides the corresponding updates for the Linux Hardware Enablement (HWE) kernel from Ubuntu 16.04 LTS for Ubuntu 14.04 ESM.

It was discovered that a race condition existed in the ARC EMAC ethernet driver for the Linux kernel, resulting in a use-after-free vulnerability. An attacker could use this to cause a denial of service (system crash). (CVE-2016-10906)

It was discovered that a race condition existed in the Serial Attached SCSI (SAS) implementation in the Linux kernel when handling certain error conditions. A local attacker could use this to cause a denial of service (kernel deadlock). (CVE-2017-18232)

It was discovered that the RSI 91x Wi-Fi driver in the Linux kernel did not did not handle detach operations correctly, leading to a use-after-free vulnerability. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2018-21008)

Wen Huang discovered that the Marvell Wi-Fi device driver in the Linux kernel did not properly perform bounds checking, leading to a heap overflow. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14814, CVE-2019-14816)

Matt Delco discovered that the KVM hypervisor implementation in the Linux kernel did not properly perform bounds checking when handling coalesced MMIO write operations. A local attacker with write access to /dev/kvm could use this to cause a denial of service (system crash). (CVE-2019-14821)

Hui Peng and Mathias Payer discovered that the USB audio driver for the Linux kernel did not properly validate device meta data. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15117)

Hui Peng and Mathias Payer discovered that the USB audio driver for the Linux kernel improperly performed recursion while handling device meta data. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15118)

It was discovered that the Technisat DVB-S/S2 USB device driver in the Linux kernel contained a buffer overread. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly expose sensitive information. (CVE-2019-15505)

Brad Spengler discovered that a Spectre mitigation was improperly implemented in the ptrace susbsystem of the Linux kernel. A local attacker could possibly use this to expose sensitive information. (CVE-2019-15902)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 14.04 ESM

linux-image-4.4.0-1056-aws - 4.4.0-1056.60

linux-image-4.4.0-166-generic - 4.4.0-166.195~14.04.1

linux-image-4.4.0-166-generic-lpae - 4.4.0-166.195~14.04.1

linux-image-4.4.0-166-lowlatency - 4.4.0-166.195~14.04.1

linux-image-4.4.0-166-powerpc-e500mc - 4.4.0-166.195~14.04.1

linux-image-4.4.0-166-powerpc-smp - 4.4.0-166.195~14.04.1

linux-image-4.4.0-166-powerpc64-emb - 4.4.0-166.195~14.04.1

linux-image-4.4.0-166-powerpc64-smp - 4.4.0-166.195~14.04.1

linux-image-aws - 4.4.0.1056.57

linux-image-generic-lpae-lts-xenial - 4.4.0.166.145

linux-image-generic-lts-xenial - 4.4.0.166.145

linux-image-lowlatency-lts-xenial - 4.4.0.166.145

linux-image-powerpc-e500mc-lts-xenial - 4.4.0.166.145

linux-image-powerpc-smp-lts-xenial - 4.4.0.166.145

linux-image-powerpc64-emb-lts-xenial - 4.4.0.166.145

linux-image-powerpc64-smp-lts-xenial - 4.4.0.166.145

linux-image-virtual-lts-xenial - 4.4.0.166.145

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4163-1](https://usn.ubuntu.com/usn/usn-4163-1)
*   [CVE-2016-10906](https://people.canonical.com/~ubuntu-security/cve/CVE-2016-10906)
*   [CVE-2017-18232](https://people.canonical.com/~ubuntu-security/cve/CVE-2017-18232)
*   [CVE-2018-21008](https://people.canonical.com/~ubuntu-security/cve/CVE-2018-21008)
*   [CVE-2019-14814](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14814)
*   [CVE-2019-14816](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14816)
*   [CVE-2019-14821](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14821)
*   [CVE-2019-15117](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15117)
*   [CVE-2019-15118](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15118)
*   [CVE-2019-15505](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15505)
*   [CVE-2019-15902](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15902)

  
  
from Ubuntu Security Notices https://ift.tt/31BPrXJ