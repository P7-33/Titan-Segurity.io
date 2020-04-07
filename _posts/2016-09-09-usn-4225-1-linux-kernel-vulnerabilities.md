---
title: 'USN-4225-1: Linux kernel vulnerabilities'
date: 2020-01-07T05:47:00+01:00
draft: false
---

linux, linux-aws, linux-azure, linux-azure-5.3, linux-gcp, linux-gcp-5.3, linux-kvm, linux-oracle, linux-raspi2 vulnerabilities
-------------------------------------------------------------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
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
*   linux-azure-5.3 - Linux kernel for Microsoft Azure Cloud systems
*   linux-gcp-5.3 - Linux kernel for Google Cloud Platform (GCP) systems

### Details

It was discovered that a heap-based buffer overflow existed in the Marvell WiFi-Ex Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14895, CVE-2019-14901)

It was discovered that a heap-based buffer overflow existed in the Marvell Libertas WLAN Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14896, CVE-2019-14897)

It was discovered that the Fujitsu ES network device driver for the Linux kernel did not properly check for errors in some situations, leading to a NULL pointer dereference. A local attacker could use this to cause a denial of service. (CVE-2019-16231)

Anthony Steinhauser discovered that the Linux kernel did not properly perform Spectre\_RSB mitigations to all processors for PowerPC architecture systems in some situations. A local attacker could use this to expose sensitive information. (CVE-2019-18660)

It was discovered that the Broadcom V3D DRI driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19044)

It was discovered that the Mellanox Technologies Innova driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19045)

It was discovered that the Mellanox Technologies ConnectX driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19047)

It was discovered that the Intel WiMAX 2400 driver in the Linux kernel did not properly deallocate memory in certain situations. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19051)

It was discovered that Geschwister Schneider USB CAN interface driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A physically proximate attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19052)

It was discovered that the netlink-based 802.11 configuration interface in the Linux kernel did not deallocate memory in certain error conditions. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19055)

It was discovered that the event tracing subsystem of the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19072)

It was discovered that the driver for memoryless force-feedback input devices in the Linux kernel contained a use-after-free vulnerability. A physically proximate attacker could possibly use this to cause a denial of service (system crash) or execute arbitrary code. (CVE-2019-19524)

It was discovered that the Microchip CAN BUS Analyzer driver in the Linux kernel contained a use-after-free vulnerability on device disconnect. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19529)

It was discovered that the PEAK-System Technik USB driver in the Linux kernel did not properly sanitize memory before sending it to the device. A physically proximate attacker could use this to expose sensitive information (kernel memory). (CVE-2019-19534)

Tristan Madani discovered that the ALSA timer implementation in the Linux kernel contained a use-after-free vulnerability. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19807)

It was discovered that the DesignWare USB3 controller driver in the Linux kernel did not properly deallocate memory in some error conditions. A local attacker could possibly use this to cause a denial of service (memory exhaustion). (CVE-2019-18813)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[linux-image-5.3.0-1008-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [5.3.0-1008.9](https://launchpad.net/ubuntu/+source/linux-oracle/5.3.0-1008.9)

[linux-image-5.3.0-1009-aws](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.3.0-1009.10](https://launchpad.net/ubuntu/+source/linux-kvm/5.3.0-1009.10)

[linux-image-5.3.0-1009-azure](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.3.0-1009.10](https://launchpad.net/ubuntu/+source/linux-kvm/5.3.0-1009.10)

[linux-image-5.3.0-1009-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.3.0-1009.10](https://launchpad.net/ubuntu/+source/linux-kvm/5.3.0-1009.10)

[linux-image-5.3.0-1011-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.3.0-1011.12](https://launchpad.net/ubuntu/+source/linux-gcp/5.3.0-1011.12)

[linux-image-5.3.0-1015-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [5.3.0-1015.17](https://launchpad.net/ubuntu/+source/linux-raspi2/5.3.0-1015.17)

[linux-image-5.3.0-26-generic](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-26.28](https://launchpad.net/ubuntu/+source/linux/5.3.0-26.28)

[linux-image-5.3.0-26-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-26.28](https://launchpad.net/ubuntu/+source/linux/5.3.0-26.28)

[linux-image-5.3.0-26-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-26.28](https://launchpad.net/ubuntu/+source/linux/5.3.0-26.28)

[linux-image-5.3.0-26-snapdragon](https://launchpad.net/ubuntu/+source/linux) - [5.3.0-26.28](https://launchpad.net/ubuntu/+source/linux/5.3.0-26.28)

linux-image-aws - 5.3.0.1009.11

linux-image-azure - 5.3.0.1009.27

linux-image-gcp - 5.3.0.1011.12

linux-image-generic - 5.3.0.26.30

linux-image-generic-lpae - 5.3.0.26.30

linux-image-gke - 5.3.0.1011.12

linux-image-kvm - 5.3.0.1009.11

linux-image-lowlatency - 5.3.0.26.30

linux-image-oracle - 5.3.0.1008.9

linux-image-raspi2 - 5.3.0.1015.12

linux-image-snapdragon - 5.3.0.26.30

linux-image-virtual - 5.3.0.26.30

Ubuntu 18.04 LTS

[linux-image-5.3.0-1009-azure](https://launchpad.net/ubuntu/+source/linux-azure-5.3) - [5.3.0-1009.10~18.04.1](https://launchpad.net/ubuntu/+source/linux-azure-5.3/5.3.0-1009.10~18.04.1)

[linux-image-5.3.0-1010-gcp](https://launchpad.net/ubuntu/+source/linux-gcp-5.3) - [5.3.0-1010.11~18.04.1](https://launchpad.net/ubuntu/+source/linux-gcp-5.3/5.3.0-1010.11~18.04.1)

linux-image-azure-edge - 5.3.0.1009.9

linux-image-gcp-edge - 5.3.0.1010.10

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
*   [CVE-2019-18660](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18660)
*   [CVE-2019-18813](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18813)
*   [CVE-2019-19044](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19044)
*   [CVE-2019-19045](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19045)
*   [CVE-2019-19047](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19047)
*   [CVE-2019-19051](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19051)
*   [CVE-2019-19052](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19052)
*   [CVE-2019-19055](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19055)
*   [CVE-2019-19072](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19072)
*   [CVE-2019-19524](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19524)
*   [CVE-2019-19529](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19529)
*   [CVE-2019-19534](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19534)
*   [CVE-2019-19807](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19807)

  
  
from Ubuntu Security Notices https://ift.tt/2Qv1R1i