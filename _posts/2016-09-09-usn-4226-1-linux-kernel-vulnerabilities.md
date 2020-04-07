---
title: 'USN-4226-1: Linux kernel vulnerabilities'
date: 2020-01-07T05:47:00+01:00
draft: false
---

linux, linux-aws, linux-aws-5.0, linux-azure, linux-gcp, linux-gke-5.0, linux-kvm, linux-oem-osp1, linux-oracle, linux-oracle-5.0, linux-raspi2 vulnerabilities
---------------------------------------------------------------------------------------------------------------------------------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.04
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
*   linux-aws-5.0 - Linux kernel for Amazon Web Services (AWS) systems
*   linux-gke-5.0 - Linux kernel for Google Container Engine (GKE) systems
*   linux-oem-osp1 - Linux kernel for OEM processors
*   linux-oracle-5.0 - Linux kernel for Oracle Cloud systems

### Details

Michael Hanselmann discovered that the CIFS implementation in the Linux kernel did not sanitize paths returned by an SMB server. An attacker controlling an SMB server could use this to overwrite arbitrary files. (CVE-2019-10220)

It was discovered that a heap-based buffer overflow existed in the Marvell WiFi-Ex Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14895, CVE-2019-14901)

It was discovered that a heap-based buffer overflow existed in the Marvell Libertas WLAN Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14896, CVE-2019-14897)

It was discovered that the Fujitsu ES network device driver for the Linux kernel did not properly check for errors in some situations, leading to a NULL pointer dereference. A local attacker could use this to cause a denial of service. (CVE-2019-16231)

It was discovered that the QLogic Fibre Channel driver in the Linux kernel did not properly check for error, leading to a NULL pointer dereference. A local attacker could possibly use this to cause a denial of service (system crash). (CVE-2019-16233)

Nicolas Waisman discovered that the WiFi driver stack in the Linux kernel did not properly validate SSID lengths. A physically proximate attacker could use this to cause a denial of service (system crash). (CVE-2019-17133)

Anthony Steinhauser discovered that the Linux kernel did not properly perform Spectre\_RSB mitigations to all processors for PowerPC architecture systems in some situations. A local attacker could use this to expose sensitive information. (CVE-2019-18660)

It was discovered that the Mellanox Technologies Innova driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19045)

It was discovered that the VirtualBox guest driver implementation in the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19048)

It was discovered that Geschwister Schneider USB CAN interface driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A physically proximate attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19052)

It was discovered that the netlink-based 802.11 configuration interface in the Linux kernel did not deallocate memory in certain error conditions. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19055)

It was discovered that the ADIS16400 IIO IMU Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19060)

It was discovered that the Intel OPA Gen1 Infiniband Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19065)

It was discovered that the AMD Audio CoProcessor Driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker with the ability to load modules could use this to cause a denial of service (memory exhaustion). (CVE-2019-19067)

It was discovered that the event tracing subsystem of the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19072)

It was discovered that the Cascoda CA8210 SPI 802.15.4 wireless controller driver for the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (memory exhaustion). (CVE-2019-19075)

It was discovered that the AMD Display Engine Driver in the Linux kernel did not properly deallocate memory in certain error conditions. A local attack could use this to cause a denial of service (memory exhaustion). (CVE-2019-19083)

It was discovered that the driver for memoryless force-feedback input devices in the Linux kernel contained a use-after-free vulnerability. A physically proximate attacker could possibly use this to cause a denial of service (system crash) or execute arbitrary code. (CVE-2019-19524)

It was discovered that the NXP PN533 NFC USB driver in the Linux kernel did not properly free resources after a late probe error, leading to a use- after-free vulnerability. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19526)

It was discovered that the Microchip CAN BUS Analyzer driver in the Linux kernel contained a use-after-free vulnerability on device disconnect. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19529)

It was discovered that multiple USB HID device drivers in the Linux kernel did not properly validate device metadata on attachment, leading to out-of- bounds writes. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19532)

It was discovered that the PEAK-System Technik USB driver in the Linux kernel did not properly sanitize memory before sending it to the device. A physically proximate attacker could use this to expose sensitive information (kernel memory). (CVE-2019-19534)

It was discovered that in some situations the fair scheduler in the Linux kernel did not permit a process to use its full quota time slice. A local attacker could use this to cause a denial of service. (CVE-2019-19922)

It was discovered that the binder IPC implementation in the Linux kernel did not properly perform bounds checking in some situations, leading to an out-of-bounds write. A local attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-2214)

Nicolas Waisman discovered that the Chelsio T4/T5 RDMA Driver for the Linux kernel performed DMA from a kernel stack. A local attacker could use this to cause a denial of service (system crash). (CVE-2019-17075)

It was discovered that the DesignWare USB3 controller driver in the Linux kernel did not properly deallocate memory in some error conditions. A local attacker could possibly use this to cause a denial of service (memory exhaustion). (CVE-2019-18813)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.04

[linux-image-5.0.0-1009-oracle](https://launchpad.net/ubuntu/+source/linux-oracle) - [5.0.0-1009.14](https://launchpad.net/ubuntu/+source/linux-oracle/5.0.0-1009.14)

[linux-image-5.0.0-1023-aws](https://launchpad.net/ubuntu/+source/linux-aws) - [5.0.0-1023.26](https://launchpad.net/ubuntu/+source/linux-aws/5.0.0-1023.26)

[linux-image-5.0.0-1024-kvm](https://launchpad.net/ubuntu/+source/linux-kvm) - [5.0.0-1024.26](https://launchpad.net/ubuntu/+source/linux-kvm/5.0.0-1024.26)

[linux-image-5.0.0-1024-raspi2](https://launchpad.net/ubuntu/+source/linux-raspi2) - [5.0.0-1024.25](https://launchpad.net/ubuntu/+source/linux-raspi2/5.0.0-1024.25)

[linux-image-5.0.0-1028-azure](https://launchpad.net/ubuntu/+source/linux-azure) - [5.0.0-1028.30](https://launchpad.net/ubuntu/+source/linux-azure/5.0.0-1028.30)

[linux-image-5.0.0-1028-gcp](https://launchpad.net/ubuntu/+source/linux-gcp) - [5.0.0-1028.29](https://launchpad.net/ubuntu/+source/linux-gcp/5.0.0-1028.29)

[linux-image-5.0.0-38-generic](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-38.41](https://launchpad.net/ubuntu/+source/linux/5.0.0-38.41)

[linux-image-5.0.0-38-generic-lpae](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-38.41](https://launchpad.net/ubuntu/+source/linux/5.0.0-38.41)

[linux-image-5.0.0-38-lowlatency](https://launchpad.net/ubuntu/+source/linux) - [5.0.0-38.41](https://launchpad.net/ubuntu/+source/linux/5.0.0-38.41)

linux-image-aws - 5.0.0.1023.25

linux-image-azure - 5.0.0.1028.28

linux-image-gcp - 5.0.0.1028.53

linux-image-generic - 5.0.0.38.40

linux-image-generic-lpae - 5.0.0.38.40

linux-image-gke - 5.0.0.1028.53

linux-image-kvm - 5.0.0.1024.25

linux-image-lowlatency - 5.0.0.38.40

linux-image-oracle - 5.0.0.1009.35

linux-image-raspi2 - 5.0.0.1024.22

linux-image-virtual - 5.0.0.38.40

Ubuntu 18.04 LTS

[linux-image-5.0.0-1009-oracle](https://launchpad.net/ubuntu/+source/linux-oracle-5.0) - [5.0.0-1009.14~18.04.1](https://launchpad.net/ubuntu/+source/linux-oracle-5.0/5.0.0-1009.14~18.04.1)

[linux-image-5.0.0-1023-aws](https://launchpad.net/ubuntu/+source/linux-aws-5.0) - [5.0.0-1023.26~18.04.1](https://launchpad.net/ubuntu/+source/linux-aws-5.0/5.0.0-1023.26~18.04.1)

[linux-image-5.0.0-1027-gke](https://launchpad.net/ubuntu/+source/linux-gke-5.0) - [5.0.0-1027.28~18.04.1](https://launchpad.net/ubuntu/+source/linux-gke-5.0/5.0.0-1027.28~18.04.1)

[linux-image-5.0.0-1028-azure](https://launchpad.net/ubuntu/+source/linux-azure) - [5.0.0-1028.30~18.04.1](https://launchpad.net/ubuntu/+source/linux-azure/5.0.0-1028.30~18.04.1)

[linux-image-5.0.0-1033-oem-osp1](https://launchpad.net/ubuntu/+source/linux-oem-osp1) - [5.0.0-1033.38](https://launchpad.net/ubuntu/+source/linux-oem-osp1/5.0.0-1033.38)

linux-image-aws-edge - 5.0.0.1023.37

linux-image-azure - 5.0.0.1028.39

linux-image-gke-5.0 - 5.0.0.1027.16

linux-image-oem-osp1 - 5.0.0.1033.37

linux-image-oracle-edge - 5.0.0.1009.8

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [CVE-2019-10220](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-10220)
*   [CVE-2019-14895](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14895)
*   [CVE-2019-14896](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14896)
*   [CVE-2019-14897](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14897)
*   [CVE-2019-14901](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14901)
*   [CVE-2019-16231](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16231)
*   [CVE-2019-16233](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16233)
*   [CVE-2019-17075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17075)
*   [CVE-2019-17133](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17133)
*   [CVE-2019-18660](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18660)
*   [CVE-2019-18813](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18813)
*   [CVE-2019-19045](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19045)
*   [CVE-2019-19048](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19048)
*   [CVE-2019-19052](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19052)
*   [CVE-2019-19055](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19055)
*   [CVE-2019-19060](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19060)
*   [CVE-2019-19065](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19065)
*   [CVE-2019-19067](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19067)
*   [CVE-2019-19072](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19072)
*   [CVE-2019-19075](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19075)
*   [CVE-2019-19083](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19083)
*   [CVE-2019-19524](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19524)
*   [CVE-2019-19526](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19526)
*   [CVE-2019-19529](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19529)
*   [CVE-2019-19532](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19532)
*   [CVE-2019-19534](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19534)
*   [CVE-2019-19922](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19922)
*   [CVE-2019-2214](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2214)

  
  
from Ubuntu Security Notices https://ift.tt/2sJkSUQ