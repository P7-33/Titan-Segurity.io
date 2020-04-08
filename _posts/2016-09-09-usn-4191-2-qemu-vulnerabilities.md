---
title: 'USN-4191-2: QEMU vulnerabilities'
date: 2019-11-14T02:03:00+01:00
draft: false
---

qemu vulnerabilities
--------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 14.04 ESM

### Summary

Several security issues were fixed in QEMU.

### Software Description

*   qemu - Machine emulator and virtualizer

### Details

USN-4191-2 fixed a vulnerability in QEMU. This update provides the corresponding update for Ubuntu 14.04 ESM.

Original advisory details:

It was discovered that the LSI SCSI adapter emulator implementation in QEMU did not properly validate executed scripts. A local attacker could use this to cause a denial of service. (CVE-2019-12068)

Sergej Schumilo, Cornelius Aschermann and Simon Wörner discovered that the qxl paravirtual graphics driver implementation in QEMU contained a null pointer dereference. A local attacker in a guest could use this to cause a denial of service. (CVE-2019-12155)

Riccardo Schirone discovered that the QEMU bridge helper did not properly validate network interface names. A local attacker could possibly use this to bypass ACL restrictions. (CVE-2019-13164)

It was discovered that a heap-based buffer overflow existed in the SLiRP networking implementation of QEMU. A local attacker in a guest could use this to cause a denial of service or possibly execute arbitrary code in the host. (CVE-2019-14378)

It was discovered that a use-after-free vulnerability existed in the SLiRP networking implementation of QEMU. A local attacker in a guest could use this to cause a denial of service. (CVE-2019-15890)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 14.04 ESM

qemu - 2.0.0+dfsg-2ubuntu1.47

qemu-common - 2.0.0+dfsg-2ubuntu1.47

qemu-kvm - 2.0.0+dfsg-2ubuntu1.47

qemu-system-common - 2.0.0+dfsg-2ubuntu1.47

qemu-system-x86 - 2.0.0+dfsg-2ubuntu1.47

qemu-user-static - 2.0.0+dfsg-2ubuntu1.47

qemu-utils - 2.0.0+dfsg-2ubuntu1.47

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to restart all QEMU virtual machines to make all the necessary changes.

References
----------

*   [USN-4191-1](https://usn.ubuntu.com/usn/usn-4191-1)
*   [CVE-2019-12068](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-12068)
*   [CVE-2019-12155](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-12155)
*   [CVE-2019-13164](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-13164)
*   [CVE-2019-14378](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14378)
*   [CVE-2019-15890](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15890)

  
  
from Ubuntu Security Notices https://ift.tt/32LZCcR