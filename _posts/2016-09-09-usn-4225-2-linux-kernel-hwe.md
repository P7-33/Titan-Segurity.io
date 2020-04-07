---
title: 'USN-4225-2: Linux kernel (HWE) vulnerabilities'
date: 2020-01-19T01:29:00+01:00
draft: false
---

linux-hwe vulnerabilities
-------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 18.04 LTS

### Summary

Several security issues were fixed in the Linux kernel.

### Software Description

*   linux-hwe - Linux hardware enablement (HWE) kernel

### Details

USN-4225-1 fixed vulnerabilities in the Linux kernel for Ubuntu 19.10. This update provides the corresponding updates for the Linux Hardware Enablement (HWE) kernel from Ubuntu 19.10 for Ubuntu 18.04 LTS.

It was discovered that a heap-based buffer overflow existed in the Marvell WiFi-Ex Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14895, CVE-2019-14901)

It was discovered that a heap-based buffer overflow existed in the Marvell Libertas WLAN Driver for the Linux kernel. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-14896, CVE-2019-14897)

It was discovered that the Fujitsu ES network device driver for the Linux kernel did not properly check for errors in some situations, leading to a NULL pointer dereference. A local attacker could use this to cause a denial of service. (CVE-2019-16231)

Anthony Steinhauser discovered that the Linux kernel did not properly perform Spectre\_RSB mitigations to all processors for PowerPC architecture systems in some situations. A local attacker could use this to expose sensitive information. (CVE-2019-18660)

It was discovered that the Mellanox Technologies Innova driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19045)

It was discovered that the Intel WiMAX 2400 driver in the Linux kernel did not properly deallocate memory in certain situations. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19051)

It was discovered that Geschwister Schneider USB CAN interface driver in the Linux kernel did not properly deallocate memory in certain failure conditions. A physically proximate attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19052)

It was discovered that the netlink-based 802.11 configuration interface in the Linux kernel did not deallocate memory in certain error conditions. A local attacker could possibly use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19055)

It was discovered that the event tracing subsystem of the Linux kernel did not properly deallocate memory in certain error conditions. A local attacker could use this to cause a denial of service (kernel memory exhaustion). (CVE-2019-19072)

It was discovered that the driver for memoryless force-feedback input devices in the Linux kernel contained a use-after-free vulnerability. A physically proximate attacker could possibly use this to cause a denial of service (system crash) or execute arbitrary code. (CVE-2019-19524)

It was discovered that the Microchip CAN BUS Analyzer driver in the Linux kernel contained a use-after-free vulnerability on device disconnect. A physically proximate attacker could use this to cause a denial of service (system crash) or possibly execute arbitrary code. (CVE-2019-19529)

It was discovered that the PEAK-System Technik USB driver in the Linux kernel did not properly sanitize memory before sending it to the device. A physically proximate attacker could use this to expose sensitive information (kernel memory). (CVE-2019-19534)

It was discovered that the DesignWare USB3 controller driver in the Linux kernel did not properly deallocate memory in some error conditions. A local attacker could possibly use this to cause a denial of service (memory exhaustion). (CVE-2019-18813)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 18.04 LTS

[linux-image-5.3.0-26-generic](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0-26.28~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

[linux-image-5.3.0-26-generic-lpae](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0-26.28~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

[linux-image-5.3.0-26-lowlatency](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0-26.28~18.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

[linux-image-generic-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.26.95](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

[linux-image-generic-lpae-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.26.95](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

[linux-image-lowlatency-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.26.95](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

[linux-image-snapdragon-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.26.95](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

[linux-image-virtual-hwe-18.04](https://launchpad.net/ubuntu/+source/linux-hwe) - [5.3.0.26.95](https://launchpad.net/ubuntu/+source/linux-hwe/5.3.0-26.28~18.04.1)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to reboot your computer to make all the necessary changes.

ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-generic, linux-generic-lts-RELEASE, linux-virtual, linux-powerpc), a standard system upgrade will automatically perform this as well.

References
----------

*   [USN-4225-1](https://usn.ubuntu.com/usn/usn-4225-1)
*   [CVE-2019-14895](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14895)
*   [CVE-2019-14896](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14896)
*   [CVE-2019-14897](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14897)
*   [CVE-2019-14901](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14901)
*   [CVE-2019-16231](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16231)
*   [CVE-2019-18660](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18660)
*   [CVE-2019-18813](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18813)
*   [CVE-2019-19045](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19045)
*   [CVE-2019-19051](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19051)
*   [CVE-2019-19052](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19052)
*   [CVE-2019-19055](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19055)
*   [CVE-2019-19072](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19072)
*   [CVE-2019-19524](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19524)
*   [CVE-2019-19529](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19529)
*   [CVE-2019-19534](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19534)

  
  
from Ubuntu Security Notices https://ift.tt/3ahfpp7