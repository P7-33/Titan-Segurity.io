---
title: 'USN-4191-1: QEMU vulnerabilities'
date: 2019-11-14T02:03:00+01:00
draft: false
---

qemu vulnerabilities
--------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in QEMU.

### Software Description

*   qemu - Machine emulator and virtualizer

### Details

It was discovered that the LSI SCSI adapter emulator implementation in QEMU did not properly validate executed scripts. A local attacker could use this to cause a denial of service. (CVE-2019-12068)

Sergej Schumilo, Cornelius Aschermann and Simon Wörner discovered that the qxl paravirtual graphics driver implementation in QEMU contained a null pointer dereference. A local attacker in a guest could use this to cause a denial of service. (CVE-2019-12155)

Riccardo Schirone discovered that the QEMU bridge helper did not properly validate network interface names. A local attacker could possibly use this to bypass ACL restrictions. (CVE-2019-13164)

It was discovered that a heap-based buffer overflow existed in the SLiRP networking implementation of QEMU. A local attacker in a guest could use this to cause a denial of service or possibly execute arbitrary code in the host. (CVE-2019-14378)

It was discovered that a use-after-free vulnerability existed in the SLiRP networking implementation of QEMU. A local attacker in a guest could use this to cause a denial of service. (CVE-2019-15890)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[qemu](https://launchpad.net/ubuntu/+source/qemu) - [1:4.0+dfsg-0ubuntu9.1](https://launchpad.net/ubuntu/+source/qemu/1:4.0+dfsg-0ubuntu9.1)

[qemu-kvm](https://launchpad.net/ubuntu/+source/qemu) - [1:4.0+dfsg-0ubuntu9.1](https://launchpad.net/ubuntu/+source/qemu/1:4.0+dfsg-0ubuntu9.1)

[qemu-system-common](https://launchpad.net/ubuntu/+source/qemu) - [1:4.0+dfsg-0ubuntu9.1](https://launchpad.net/ubuntu/+source/qemu/1:4.0+dfsg-0ubuntu9.1)

[qemu-system-gui](https://launchpad.net/ubuntu/+source/qemu) - [1:4.0+dfsg-0ubuntu9.1](https://launchpad.net/ubuntu/+source/qemu/1:4.0+dfsg-0ubuntu9.1)

[qemu-system-x86](https://launchpad.net/ubuntu/+source/qemu) - [1:4.0+dfsg-0ubuntu9.1](https://launchpad.net/ubuntu/+source/qemu/1:4.0+dfsg-0ubuntu9.1)

[qemu-user-static](https://launchpad.net/ubuntu/+source/qemu) - [1:4.0+dfsg-0ubuntu9.1](https://launchpad.net/ubuntu/+source/qemu/1:4.0+dfsg-0ubuntu9.1)

[qemu-utils](https://launchpad.net/ubuntu/+source/qemu) - [1:4.0+dfsg-0ubuntu9.1](https://launchpad.net/ubuntu/+source/qemu/1:4.0+dfsg-0ubuntu9.1)

Ubuntu 19.04

[qemu](https://launchpad.net/ubuntu/+source/qemu) - [1:3.1+dfsg-2ubuntu3.6](https://launchpad.net/ubuntu/+source/qemu/1:3.1+dfsg-2ubuntu3.6)

[qemu-kvm](https://launchpad.net/ubuntu/+source/qemu) - [1:3.1+dfsg-2ubuntu3.6](https://launchpad.net/ubuntu/+source/qemu/1:3.1+dfsg-2ubuntu3.6)

[qemu-system-common](https://launchpad.net/ubuntu/+source/qemu) - [1:3.1+dfsg-2ubuntu3.6](https://launchpad.net/ubuntu/+source/qemu/1:3.1+dfsg-2ubuntu3.6)

[qemu-system-gui](https://launchpad.net/ubuntu/+source/qemu) - [1:3.1+dfsg-2ubuntu3.6](https://launchpad.net/ubuntu/+source/qemu/1:3.1+dfsg-2ubuntu3.6)

[qemu-system-x86](https://launchpad.net/ubuntu/+source/qemu) - [1:3.1+dfsg-2ubuntu3.6](https://launchpad.net/ubuntu/+source/qemu/1:3.1+dfsg-2ubuntu3.6)

[qemu-user-static](https://launchpad.net/ubuntu/+source/qemu) - [1:3.1+dfsg-2ubuntu3.6](https://launchpad.net/ubuntu/+source/qemu/1:3.1+dfsg-2ubuntu3.6)

[qemu-utils](https://launchpad.net/ubuntu/+source/qemu) - [1:3.1+dfsg-2ubuntu3.6](https://launchpad.net/ubuntu/+source/qemu/1:3.1+dfsg-2ubuntu3.6)

Ubuntu 18.04 LTS

[qemu](https://launchpad.net/ubuntu/+source/qemu) - [1:2.11+dfsg-1ubuntu7.20](https://launchpad.net/ubuntu/+source/qemu/1:2.11+dfsg-1ubuntu7.20)

[qemu-kvm](https://launchpad.net/ubuntu/+source/qemu) - [1:2.11+dfsg-1ubuntu7.20](https://launchpad.net/ubuntu/+source/qemu/1:2.11+dfsg-1ubuntu7.20)

[qemu-system-common](https://launchpad.net/ubuntu/+source/qemu) - [1:2.11+dfsg-1ubuntu7.20](https://launchpad.net/ubuntu/+source/qemu/1:2.11+dfsg-1ubuntu7.20)

[qemu-system-x86](https://launchpad.net/ubuntu/+source/qemu) - [1:2.11+dfsg-1ubuntu7.20](https://launchpad.net/ubuntu/+source/qemu/1:2.11+dfsg-1ubuntu7.20)

[qemu-user-static](https://launchpad.net/ubuntu/+source/qemu) - [1:2.11+dfsg-1ubuntu7.20](https://launchpad.net/ubuntu/+source/qemu/1:2.11+dfsg-1ubuntu7.20)

[qemu-utils](https://launchpad.net/ubuntu/+source/qemu) - [1:2.11+dfsg-1ubuntu7.20](https://launchpad.net/ubuntu/+source/qemu/1:2.11+dfsg-1ubuntu7.20)

Ubuntu 16.04 LTS

[qemu](https://launchpad.net/ubuntu/+source/qemu) - [1:2.5+dfsg-5ubuntu10.42](https://launchpad.net/ubuntu/+source/qemu/1:2.5+dfsg-5ubuntu10.42)

[qemu-kvm](https://launchpad.net/ubuntu/+source/qemu) - [1:2.5+dfsg-5ubuntu10.42](https://launchpad.net/ubuntu/+source/qemu/1:2.5+dfsg-5ubuntu10.42)

[qemu-system-common](https://launchpad.net/ubuntu/+source/qemu) - [1:2.5+dfsg-5ubuntu10.42](https://launchpad.net/ubuntu/+source/qemu/1:2.5+dfsg-5ubuntu10.42)

[qemu-system-x86](https://launchpad.net/ubuntu/+source/qemu) - [1:2.5+dfsg-5ubuntu10.42](https://launchpad.net/ubuntu/+source/qemu/1:2.5+dfsg-5ubuntu10.42)

[qemu-user-static](https://launchpad.net/ubuntu/+source/qemu) - [1:2.5+dfsg-5ubuntu10.42](https://launchpad.net/ubuntu/+source/qemu/1:2.5+dfsg-5ubuntu10.42)

[qemu-utils](https://launchpad.net/ubuntu/+source/qemu) - [1:2.5+dfsg-5ubuntu10.42](https://launchpad.net/ubuntu/+source/qemu/1:2.5+dfsg-5ubuntu10.42)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to restart all QEMU virtual machines to make all the necessary changes.

References
----------

*   [CVE-2019-12068](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-12068)
*   [CVE-2019-12155](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-12155)
*   [CVE-2019-13164](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-13164)
*   [CVE-2019-14378](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14378)
*   [CVE-2019-15890](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15890)

  
  
from Ubuntu Security Notices https://ift.tt/2KkYG8X