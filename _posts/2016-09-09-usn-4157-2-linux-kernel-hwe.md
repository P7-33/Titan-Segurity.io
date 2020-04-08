---
title: 'USN-4157-2: Linux kernel (HWE) vulnerabilities'
date: 2019-10-22T04:19:00+01:00
draft: false
---

linux-hwe, linux-azure, linux-gcp, linux-gke-5.0 vulnerabilities
----------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 18.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux-azure - Linux kernel for Microsoft Azure Cloud systems
*   linux-gcp - Linux kernel for Google Cloud Platform (GCP) systems
*   linux-gke-5.0 - Linux kernel for Google Container Engine (GKE) systems
*   linux-hwe - Linux hardware enablement (HWE) kernel

### Details

USN-4157-1 fixed vulnerabilities in the Linux kernel for Ubuntu 19.04. This update provides the corresponding updates for the Linux Hardware Enablement (HWE) kernel from Ubuntu 19.04 for Ubuntu 18.04 LTS.

Wen Huang discovered that the Marvell Wi-Fi device driver in the Linux kernel did not properly perform bounds checking, leading to a heap overflow. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14814, CVE-2019-14815, CVE-2019-14816)

Matt Delco discovered that the KVM hypervisor implementation in the Linux kernel did not properly perform bounds checking when handling coalesced MMIO write operations. A local attacker with write access to /dev/kvm could use this to cause a denial of service (system crash). (CVE-2019-14821)

Hui Peng and Mathias Payer discovered that the 91x Wi-Fi driver in the Linux kernel did not properly handle error conditions on initialization, leading to a double-free vulnerability. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15504)

It was discovered that the Technisat DVB-S/S2 USB device driver in the Linux kernel contained a buffer overread. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly expose sensitive information. (CVE-2019-15505)

Brad Spengler discovered that a Spectre mitigation was improperly implemented in the ptrace susbsystem of the Linux kernel. A local attacker could possibly use this to expose sensitive information. (CVE-2019-15902)

It was discovered that the IPv6 RDS implementation in the Linux kernel did not properly initialize fields in a data structure returned to user space. A local attacker could use this to expose sensitive information (kernel memory). Please note that the RDS protocol is blacklisted in Ubuntu by default. (CVE-2019-16714)

It was discovered that an integer overflow existed in the Binder implementation of the Linux kernel, leading to a buffer overflow. A local attacker could use this to escalate privileges. (CVE-2019-2181)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS

[linux-image-5.0.0-1021-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1021.21~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1021.21~18.04.1)

[linux-image-5.0.0-1023-azure](https://launchpad.net/ubuntu/+source/linux-azure) - [5.0.0-1023.24~18.04.1](https://launchpad.net/ubuntu/+source/linux-azure/5.0.0-1023.24~18.04.1)

[linux-image-5.0.0-1023-gke](https://launchpad.net/ubuntu/+source/linux-gke-5.0) - [5.0.0-1023.23~18.04.2](https://launchpad.net/ubuntu/+source/linux-gke-5.0/5.0.0-1023.23~18.04.2)

[linux-image-5.0.0-32-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-32.34~18.04.2](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-32.34~18.04.2)

[linux-image-5.0.0-32-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-32.34~18.04.2](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-32.34~18.04.2)

[linux-image-5.0.0-32-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.0.0-32.34~18.04.2](https://launchpad.net/ubuntu/+source/linux-hwe/5.0.0-32.34~18.04.2)

linux-image-azure - 5.0.0.1023.33

linux-image-gcp - 5.0.0.1021.26

linux-image-generic-hwe-18.04 - 5.0.0.32.89

linux-image-generic-lpae-hwe-18.04 - 5.0.0.32.89

linux-image-gke-5.0 - 5.0.0.1023.12

linux-image-lowlatency-hwe-18.04 - 5.0.0.32.89

linux-image-snapdragon-hwe-18.04 - 5.0.0.32.89

linux-image-virtual-hwe-18.04 - 5.0.0.32.89

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4157-1](https://usn.ubuntu.com/usn/usn-4157-1)
*   [CVE-2019-14814](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14814)
*   [CVE-2019-14815](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14815)
*   [CVE-2019-14816](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14816)
*   [CVE-2019-14821](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14821)
*   [CVE-2019-15504](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15504)
*   [CVE-2019-15505](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15505)
*   [CVE-2019-15902](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15902)
*   [CVE-2019-16714](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16714)
*   [CVE-2019-2181](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2181)

  
  
from Ubuntu Security Notices https://ift.tt/2W3wRXp