---
title: 'USN-4210-1: Linux kernel vulnerabilities'
date: 2019-12-03T04:22:00+01:00
draft: false
---

linux, linux-aws, linux-aws-hwe, linux-gcp, linux-gke-4.15, linux-hwe, linux-kvm, linux-oem, linux-oracle, linux-raspi2, linux-snapdragon vulnerabilities
---------------------------------------------------------------------------------------------------------------------------------------------------------

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
*   linux-gcp - Linux kernel for Google Cloud Platform (GCP) systems
*   linux-hwe - Linux hardware enablement (HWE) kernel

### Details

It was discovered that a buffer overflow existed in the 802.11 Wi-Fi configuration interface for the Linux kernel when handling beacon settings. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-16746)

Nicolas Waisman discovered that the WiFi driver stack in the Linux kernel did not properly validate SSID lengths. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-17133)

It was discovered that the ADIS16400 IIO IMU Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19060)

It was discovered that the Intel OPA Gen1 Infiniband Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19065)

It was discovered that the Cascoda CA8210 SPI 802.15.4 wireless controller driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19075)

Nicolas Waisman discovered that the Chelsio T4/T5 RDMA Driver for the Linux kernel performed DMA from a kernel stack. A local attacker could use this to cause a denial of service (system crash). (CVE-2019-17075)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS

[linux-image-4.15.0-1030-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [4.15.0-1030.33](https://launchpad.net/ubuntu/+source/linux-oracle/4.15.0-1030.33)

[linux-image-4.15.0-1049-gke](https://launchpad.net/ubuntu/+source/linux-gke-4.15) - [4.15.0-1049.52](https://launchpad.net/ubuntu/+source/linux-gke-4.15/4.15.0-1049.52)

[linux-image-4.15.0-1051-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [4.15.0-1051.51](https://launchpad.net/ubuntu/+source/linux-kvm/4.15.0-1051.51)

[linux-image-4.15.0-1052-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [4.15.0-1052.56](https://launchpad.net/ubuntu/+source/linux-raspi2/4.15.0-1052.56)

[linux-image-4.15.0-1056-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [4.15.0-1056.58](https://launchpad.net/ubuntu/+source/linux-aws/4.15.0-1056.58)

[linux-image-4.15.0-1065-oem](https://launchpad.net/ubuntu/+source/linux-oem) - [4.15.0-1065.75](https://launchpad.net/ubuntu/+source/linux-oem/4.15.0-1065.75)

[linux-image-4.15.0-1069-snapdragon](https://launchpad.net/ubuntu/+source/linux-snapdragon) - [4.15.0-1069.76](https://launchpad.net/ubuntu/+source/linux-snapdragon/4.15.0-1069.76)

[linux-image-4.15.0-72-generic](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-72.81](https://launchpad.net/ubuntu/+source/linux/4.15.0-72.81)

[linux-image-4.15.0-72-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-72.81](https://launchpad.net/ubuntu/+source/linux/4.15.0-72.81)

[linux-image-4.15.0-72-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [4.15.0-72.81](https://launchpad.net/ubuntu/+source/linux/4.15.0-72.81)

linux-image-aws - 4.15.0.1056.57

linux-image-aws-lts-18.04 - 4.15.0.1056.57

linux-image-generic - 4.15.0.72.74

linux-image-generic-lpae - 4.15.0.72.74

linux-image-gke - 4.15.0.1049.52

linux-image-gke-4.15 - 4.15.0.1049.52

linux-image-kvm - 4.15.0.1051.51

linux-image-lowlatency - 4.15.0.72.74

linux-image-oem - 4.15.0.1065.69

linux-image-oracle - 4.15.0.1030.35

linux-image-oracle-lts-18.04 - 4.15.0.1030.35

linux-image-powerpc-e500mc - 4.15.0.72.74

linux-image-powerpc-smp - 4.15.0.72.74

linux-image-powerpc64-emb - 4.15.0.72.74

linux-image-powerpc64-smp - 4.15.0.72.74

linux-image-raspi2 - 4.15.0.1052.50

linux-image-snapdragon - 4.15.0.1069.72

linux-image-virtual - 4.15.0.72.74

Ubuntu 16.04 LTS

[linux-image-4.15.0-1030-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [4.15.0-1030.33~16.04.1](https://launchpad.net/ubuntu/+source/linux-oracle/4.15.0-1030.33~16.04.1)

[linux-image-4.15.0-1050-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [4.15.0-1050.53](https://launchpad.net/ubuntu/+source/linux-gcp/4.15.0-1050.53)

[linux-image-4.15.0-1056-aws](https://launchpad.net/ubuntu/+source/linux-aws-hwe) - [4.15.0-1056.58~16.04.1](https://launchpad.net/ubuntu/+source/linux-aws-hwe/4.15.0-1056.58~16.04.1)

[linux-image-4.15.0-72-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-72.81~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-72.81~16.04.1)

[linux-image-4.15.0-72-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-72.81~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-72.81~16.04.1)

[linux-image-4.15.0-72-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [4.15.0-72.81~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.15.0-72.81~16.04.1)

linux-image-aws-hwe - 4.15.0.1056.56

linux-image-gcp - 4.15.0.1050.64

linux-image-generic-hwe-16.04 - 4.15.0.72.92

linux-image-generic-lpae-hwe-16.04 - 4.15.0.72.92

linux-image-gke - 4.15.0.1050.64

linux-image-lowlatency-hwe-16.04 - 4.15.0.72.92

linux-image-oem - 4.15.0.72.92

linux-image-oracle - 4.15.0.1030.23

linux-image-virtual-hwe-16.04 - 4.15.0.72.92

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2019-16746](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16746)
*   [CVE-2019-17075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17075)
*   [CVE-2019-17133](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17133)
*   [CVE-2019-19060](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19060)
*   [CVE-2019-19065](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19065)
*   [CVE-2019-19075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19075)

  
  
from Ubuntu Security Notices https://ift.tt/2P6EadL