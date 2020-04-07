---
title: 'USN-4227-1: Linux kernel vulnerabilities'
date: 2020-01-07T05:47:00+01:00
draft: false
---

linux, linux-aws, linux-aws-hwe, linux-azure, linux-gcp, linux-gke-4.15, linux-hwe, linux-kvm, linux-oem, linux-oracle, linux-raspi2, linux-snapdragon vulnerabilities
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux - Linux kernel
*   linux-aws - Linux kernel for Amazon Web Services (AWS) systems
*   linux-gke-4.15 - Linux kernel for Google Container Engine (GKE) systems
*   linux-kvm - Linux kernel for cloud environments
*   linux-oem - Linux kernel for OEM processors
*   linux-oracle - Linux kernel for Oracle Cloud systems
*   linux-raspi2 - Linux kernel for Raspberry Pi 2
*   linux-snapdragon - Linux kernel for Snapdragon processors
*   linux-aws-hwe - Linux kernel for Amazon Web Services (AWS-HWE) systems
*   linux-azure - Linux kernel for Microsoft Azure Cloud systems
*   linux-gcp - Linux kernel for Google Cloud Platform (GCP) systems
*   linux-hwe - Linux hardware enablement (HWE) kernel

### Details

It was discovered that a heap-based buffer overflow existed in the Marvell WiFi-Ex Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14895, CVE-2019-14901)

It was discovered that a heap-based buffer overflow existed in the Marvell Libertas WLAN Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14896, CVE-2019-14897)

It was discovered that the Fujitsu ES network device driver for the Linux kernel did not properly check for errors in some situations, leading to a NULL pointer dereference. A local attacker could use this to cause a denial of service. (CVE-2019-16231)

It was discovered that the QLogic Fibre Channel driver in the Linux kernel did not properly check for error, leading to a NULL pointer dereference. A local attacker could possibly use this to cause a denial of service (system crash). (CVE-2019-16233)

Anthony Steinhauser discovered that the Linux kernel did not properly perform Spectre\_RSB mitigations to all processors for PowerPC architecture systems in some situations. A local attacker could use this to expose sensitive information. (CVE-2019-18660)

It was discovered that the Mellanox Technologies Innova driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19045)

It was discovered that Geschwister Schneider USB CAN interface driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A physically proximate attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19052)

It was discovered that the AMD Display Engine Driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attack could use this to cause a denial of service (memory exhaustion). (CVE-2019-19083)

It was discovered that the driver for memoryless force-feedback input devices in the Linux kernel contained a use-after-free vulnerability. A physically proximate attacker could possibly use this to cause a denial of service (system crash) or execute arbitrary code. (CVE-2019-19524)

It was discovered that the Microchip CAN BUS Analyzer driver in the Linux kernel contained a use-after-free vulnerability on device disconnect. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19529)

It was discovered that the PEAK-System Technik USB driver in the Linux kernel did not properly sanitize memory before sending it to the device. A physically proximate attacker could use this to expose sensitive information (kernel memory). (CVE-2019-19534)

Tristan Madani discovered that the ALSA timer implementation in the Linux kernel contained a use-after-free vulnerability. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19807)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS

[linux-image-4.15.0-1031-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [4.15.0-1031.34](https://launchpad.net/ubuntu/+source/linux-oracle/4.15.0-1031.34)

[linux-image-4.15.0-1050-gke](https://launchpad.net/ubuntu/+source/linux-gke-4.15) - [4.15.0-1050.53](https://launchpad.net/ubuntu/+source/linux-gke-4.15/4.15.0-1050.53)

[linux-image-4.15.0-1052-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [4.15.0-1052.52](https://launchpad.net/ubuntu/+source/linux-kvm/4.15.0-1052.52)

[linux-image-4.15.0-1053-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [4.15.0-1053.57](https://launchpad.net/ubuntu/+source/linux-raspi2/4.15.0-1053.57)

[linux-image-4.15.0-1057-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [4.15.0-1057.59](https://launchpad.net/ubuntu/+source/linux-aws/4.15.0-1057.59)

[linux-image-4.15.0-1066-oem](https://launchpad.net/ubuntu/+source/linux-oem) - [4.15.0-1066.76](https://launchpad.net/ubuntu/+source/linux-oem/4.15.0-1066.76)

[linux-image-4.15.0-1070-snapdragon](https://launchpad.net/ubuntu/+source/linux-snapdragon) - [4.15.0-1070.77](https://launchpad.net/ubuntu/+source/linux-snapdragon/4.15.0-1070.77)

[linux-image-4.15.0-74-generic](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-74.84](https://launchpad.net/ubuntu/+source/linux/4.15.0-74.84)

[linux-image-4.15.0-74-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-74.84](https://launchpad.net/ubuntu/+source/linux/4.15.0-74.84)

[linux-image-4.15.0-74-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-74.84](https://launchpad.net/ubuntu/+source/linux/4.15.0-74.84)

linux-image-aws - 4.15.0.1057.58

linux-image-aws-lts-18.04 - 4.15.0.1057.58

linux-image-generic - 4.15.0.74.76

linux-image-generic-lpae - 4.15.0.74.76

linux-image-gke - 4.15.0.1050.53

linux-image-gke-4.15 - 4.15.0.1050.53

linux-image-kvm - 4.15.0.1052.52

linux-image-lowlatency - 4.15.0.74.76

linux-image-oem - 4.15.0.1066.70

linux-image-oracle - 4.15.0.1031.36

linux-image-oracle-lts-18.04 - 4.15.0.1031.36

linux-image-powerpc-e500mc - 4.15.0.74.76

linux-image-powerpc-smp - 4.15.0.74.76

linux-image-powerpc64-emb - 4.15.0.74.76

linux-image-powerpc64-smp - 4.15.0.74.76

linux-image-raspi2 - 4.15.0.1053.51

linux-image-snapdragon - 4.15.0.1070.73

linux-image-virtual - 4.15.0.74.76

Ubuntu 16.04 LTS

[linux-image-4.15.0-1031-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [4.15.0-1031.34~16.04.1](https://launchpad.net/ubuntu/+source/linux-oracle/4.15.0-1031.34~16.04.1)

[linux-image-4.15.0-1052-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [4.15.0-1052.56](https://launchpad.net/ubuntu/+source/linux-gcp/4.15.0-1052.56)

[linux-image-4.15.0-1057-aws](https://launchpad.net/ubuntu/+source/linux-aws-hwe) - [4.15.0-1057.59~16.04.1](https://launchpad.net/ubuntu/+source/linux-aws-hwe/4.15.0-1057.59~16.04.1)

[linux-image-4.15.0-1066-azure](https://launchpad.net/ubuntu/+source/linux-azure) - [4.15.0-1066.71](https://launchpad.net/ubuntu/+source/linux-azure/4.15.0-1066.71)

[linux-image-4.15.0-74-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-74.83~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-74.83~16.04.1)

[linux-image-4.15.0-74-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-74.83~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-74.83~16.04.1)

[linux-image-4.15.0-74-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-74.83~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-74.83~16.04.1)

linux-image-aws-hwe - 4.15.0.1057.57

linux-image-azure - 4.15.0.1066.69

linux-image-azure-edge - 4.15.0.1066.69

linux-image-gcp - 4.15.0.1052.66

linux-image-generic-hwe-16.04 - 4.15.0.74.94

linux-image-generic-lpae-hwe-16.04 - 4.15.0.74.94

linux-image-gke - 4.15.0.1052.66

linux-image-lowlatency-hwe-16.04 - 4.15.0.74.94

linux-image-oem - 4.15.0.74.94

linux-image-oracle - 4.15.0.1031.24

linux-image-virtual-hwe-16.04 - 4.15.0.74.94

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2019-14895](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14895)
*   [CVE-2019-14896](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14896)
*   [CVE-2019-14897](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14897)
*   [CVE-2019-14901](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14901)
*   [CVE-2019-16231](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16231)
*   [CVE-2019-16233](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16233)
*   [CVE-2019-18660](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18660)
*   [CVE-2019-19045](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19045)
*   [CVE-2019-19052](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19052)
*   [CVE-2019-19083](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19083)
*   [CVE-2019-19524](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19524)
*   [CVE-2019-19529](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19529)
*   [CVE-2019-19534](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19534)
*   [CVE-2019-19807](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19807)

  
  
from Ubuntu Security Notices https://ift.tt/2MZECKs