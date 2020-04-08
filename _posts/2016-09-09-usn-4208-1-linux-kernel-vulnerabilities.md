---
title: 'USN-4208-1: Linux kernel vulnerabilities'
date: 2019-12-03T04:22:00+01:00
draft: false
---

linux, linux-aws, linux-gcp, linux-gcp-5.3, linux-kvm, linux-oracle vulnerabilities
-----------------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 18.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux - Linux kernel
*   linux-aws - Linux kernel for Amazon Web Services (AWS) systems
*   linux-gcp - Linux kernel for Google Cloud Platform (GCP) systems
*   linux-kvm - Linux kernel for cloud environments
*   linux-oracle - Linux kernel for Oracle Cloud systems
*   linux-gcp-5.3 - Linux kernel for Google Cloud Platform (GCP) systems

### Details

Jann Horn discovered that the OverlayFS and ShiftFS Drivers in the Linux kernel did not properly handle reference counting during memory mapping operations when used in conjunction with AUFS. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-15794)

Nicolas Waisman discovered that the WiFi driver stack in the Linux kernel did not properly validate SSID lengths. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-17133)

It was discovered that the ARM Komeda display driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-18810)

It was discovered that the VirtualBox guest driver implementation in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19048)

It was discovered that the ADIS16400 IIO IMU Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19060, CVE-2019-19061)

It was discovered that the Intel OPA Gen1 Infiniband Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19065)

It was discovered that the AMD Audio CoProcessor Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker with the ability to load modules could use this to cause a denial of service (memory exhaustion). (CVE-2019-19067)

It was discovered in the Qualcomm FastRPC Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19069)

It was discovered that the Cascoda CA8210 SPI 802.15.4 wireless controller driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19075)

It was discovered that the AMD Display Engine Driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attack could use this to cause a denial of service (memory exhaustion). (CVE-2019-19083)

Nicolas Waisman discovered that the Chelsio T4/T5 RDMA Driver for the Linux kernel performed DMA from a kernel stack. A local attacker could use this to cause a denial of service (system crash). (CVE-2019-17075)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[linux-image-5.3.0-1007-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [5.3.0-1007.8](https://launchpad.net/ubuntu/+source/linux-oracle/5.3.0-1007.8)

[linux-image-5.3.0-1008-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [5.3.0-1008.9](https://launchpad.net/ubuntu/+source/linux-aws/5.3.0-1008.9)

[linux-image-5.3.0-1008-kvm](https://launchpad.net/ubuntu/+source/linux-aws) - [5.3.0-1008.9](https://launchpad.net/ubuntu/+source/linux-aws/5.3.0-1008.9)

[linux-image-5.3.0-1009-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.3.0-1009.10](https://launchpad.net/ubuntu/+source/linux-gcp/5.3.0-1009.10)

[linux-image-5.3.0-24-generic](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-24.26](https://launchpad.net/ubuntu/+source/linux/5.3.0-24.26)

[linux-image-5.3.0-24-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-24.26](https://launchpad.net/ubuntu/+source/linux/5.3.0-24.26)

[linux-image-5.3.0-24-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-24.26](https://launchpad.net/ubuntu/+source/linux/5.3.0-24.26)

[linux-image-5.3.0-24-snapdragon](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-24.26](https://launchpad.net/ubuntu/+source/linux/5.3.0-24.26)

linux-image-aws - 5.3.0.1008.10

linux-image-gcp - 5.3.0.1009.10

linux-image-generic - 5.3.0.24.28

linux-image-generic-lpae - 5.3.0.24.28

linux-image-gke - 5.3.0.1009.10

linux-image-kvm - 5.3.0.1008.10

linux-image-lowlatency - 5.3.0.24.28

linux-image-oracle - 5.3.0.1007.8

linux-image-snapdragon - 5.3.0.24.28

linux-image-virtual - 5.3.0.24.28

Ubuntu 18.04 LTS

[linux-image-5.3.0-1009-gcp](https://launchpad.net/ubuntu/+source/linux-gcp-5.3) - [5.3.0-1009.10~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp-5.3/5.3.0-1009.10~18.04.1)

[linux-image-gcp-edge](https://launchpad.net/ubuntu/+source/linux-gcp-5.3) - [5.3.0.1009.9](https://launchpad.net/ubuntu/+source/linux-gcp-5.3/5.3.0-1009.10~18.04.1)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2019-15794](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15794)
*   [CVE-2019-17075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17075)
*   [CVE-2019-17133](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17133)
*   [CVE-2019-18810](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18810)
*   [CVE-2019-19048](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19048)
*   [CVE-2019-19060](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19060)
*   [CVE-2019-19061](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19061)
*   [CVE-2019-19065](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19065)
*   [CVE-2019-19067](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19067)
*   [CVE-2019-19069](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19069)
*   [CVE-2019-19075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19075)
*   [CVE-2019-19083](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19083)

  
  
from Ubuntu Security Notices https://ift.tt/2LgLsuy