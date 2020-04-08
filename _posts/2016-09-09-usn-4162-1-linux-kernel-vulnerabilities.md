---
title: 'USN-4162-1: Linux kernel vulnerabilities'
date: 2019-10-22T04:19:00+01:00
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

It was discovered that the RSI 91x Wi-Fi driver in the Linux kernel did not did not handle detach operations correctly, leading to a use-after-free vulnerability. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2018-21008)

Wen Huang discovered that the Marvell Wi-Fi device driver in the Linux kernel did not properly perform bounds checking, leading to a heap overflow. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14814, CVE-2019-14815, CVE-2019-14816)

Matt Delco discovered that the KVM hypervisor implementation in the Linux kernel did not properly perform bounds checking when handling coalesced MMIO write operations. A local attacker with write access to /dev/kvm could use this to cause a denial of service (system crash). (CVE-2019-14821)

Hui Peng and Mathias Payer discovered that the USB audio driver for the Linux kernel did not properly validate device meta data. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15117)

Hui Peng and Mathias Payer discovered that the USB audio driver for the Linux kernel improperly performed recursion while handling device meta data. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-15118)

It was discovered that the Technisat DVB-S/S2 USB device driver in the Linux kernel contained a buffer overread. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly expose sensitive information. (CVE-2019-15505)

Brad Spengler discovered that a Spectre mitigation was improperly implemented in the ptrace susbsystem of the Linux kernel. A local attacker could possibly use this to expose sensitive information. (CVE-2019-15902)

It was discovered that the SMB networking file system implementation in the Linux kernel contained a buffer overread. An attacker could use this to expose sensitive information (kernel memory). (CVE-2019-15918)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS

[linux-image-4.15.0-1027-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [4.15.0-1027.30](https://launchpad.net/ubuntu/+source/linux-oracle/4.15.0-1027.30)

[linux-image-4.15.0-1046-gke](https://launchpad.net/ubuntu/+source/linux-gke-4.15) - [4.15.0-1046.49](https://launchpad.net/ubuntu/+source/linux-gke-4.15/4.15.0-1046.49)

[linux-image-4.15.0-1048-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [4.15.0-1048.48](https://launchpad.net/ubuntu/+source/linux-kvm/4.15.0-1048.48)

[linux-image-4.15.0-1049-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [4.15.0-1049.53](https://launchpad.net/ubuntu/+source/linux-raspi2/4.15.0-1049.53)

[linux-image-4.15.0-1052-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [4.15.0-1052.54](https://launchpad.net/ubuntu/+source/linux-aws/4.15.0-1052.54)

[linux-image-4.15.0-1059-oem](https://launchpad.net/ubuntu/+source/linux-oem) - [4.15.0-1059.68](https://launchpad.net/ubuntu/+source/linux-oem/4.15.0-1059.68)

[linux-image-4.15.0-1066-snapdragon](https://launchpad.net/ubuntu/+source/linux-snapdragon) - [4.15.0-1066.73](https://launchpad.net/ubuntu/+source/linux-snapdragon/4.15.0-1066.73)

[linux-image-4.15.0-66-generic](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-66.75](https://launchpad.net/ubuntu/+source/linux/4.15.0-66.75)

[linux-image-4.15.0-66-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-66.75](https://launchpad.net/ubuntu/+source/linux/4.15.0-66.75)

[linux-image-4.15.0-66-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-66.75](https://launchpad.net/ubuntu/+source/linux/4.15.0-66.75)

linux-image-aws - 4.15.0.1052.51

linux-image-generic - 4.15.0.66.68

linux-image-generic-lpae - 4.15.0.66.68

linux-image-gke - 4.15.0.1046.49

linux-image-gke-4.15 - 4.15.0.1046.49

linux-image-kvm - 4.15.0.1048.48

linux-image-lowlatency - 4.15.0.66.68

linux-image-oem - 4.15.0.1059.63

linux-image-oracle - 4.15.0.1027.30

linux-image-powerpc-e500mc - 4.15.0.66.68

linux-image-powerpc-smp - 4.15.0.66.68

linux-image-powerpc64-emb - 4.15.0.66.68

linux-image-powerpc64-smp - 4.15.0.66.68

linux-image-raspi2 - 4.15.0.1049.47

linux-image-snapdragon - 4.15.0.1066.69

linux-image-virtual - 4.15.0.66.68

Ubuntu 16.04 LTS

[linux-image-4.15.0-1027-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [4.15.0-1027.30~16.04.1](https://launchpad.net/ubuntu/+source/linux-oracle/4.15.0-1027.30~16.04.1)

[linux-image-4.15.0-1047-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [4.15.0-1047.50](https://launchpad.net/ubuntu/+source/linux-gcp/4.15.0-1047.50)

[linux-image-4.15.0-1052-aws](https://launchpad.net/ubuntu/+source/linux-aws-hwe) - [4.15.0-1052.54~16.04.1](https://launchpad.net/ubuntu/+source/linux-aws-hwe/4.15.0-1052.54~16.04.1)

[linux-image-4.15.0-1061-azure](https://launchpad.net/ubuntu/+source/linux-azure) - [4.15.0-1061.66](https://launchpad.net/ubuntu/+source/linux-azure/4.15.0-1061.66)

[linux-image-4.15.0-66-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-66.75~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-66.75~16.04.1)

[linux-image-4.15.0-66-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-66.75~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-66.75~16.04.1)

[linux-image-4.15.0-66-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-66.75~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-66.75~16.04.1)

linux-image-aws-hwe - 4.15.0.1052.52

linux-image-azure - 4.15.0.1061.64

linux-image-gcp - 4.15.0.1047.61

linux-image-generic-hwe-16.04 - 4.15.0.66.86

linux-image-generic-lpae-hwe-16.04 - 4.15.0.66.86

linux-image-gke - 4.15.0.1047.61

linux-image-lowlatency-hwe-16.04 - 4.15.0.66.86

linux-image-oem - 4.15.0.66.86

linux-image-oracle - 4.15.0.1027.20

linux-image-virtual-hwe-16.04 - 4.15.0.66.86

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2018-21008](https://people.canonical.com/~ubuntu-security/cve/CVE-2018-21008)
*   [CVE-2019-14814](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14814)
*   [CVE-2019-14815](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14815)
*   [CVE-2019-14816](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14816)
*   [CVE-2019-14821](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14821)
*   [CVE-2019-15117](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15117)
*   [CVE-2019-15118](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15118)
*   [CVE-2019-15505](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15505)
*   [CVE-2019-15902](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15902)
*   [CVE-2019-15918](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15918)

  
  
from Ubuntu Security Notices https://ift.tt/32BVdKm