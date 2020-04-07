---
title: 'USN-4246-1: zlib vulnerabilities'
date: 2020-01-23T01:21:00+01:00
draft: false
---

zlib vulnerabilities
--------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in zlib

### Software Description

*   zlib - Lossless data-compression library

### Details

It was discovered that zlib incorrectly handled pointer arithmetic. An attacker could use this issue to cause zlib to crash, resulting in a denial of service, or possibly execute arbitrary code. (CVE-2016-9840, CVE-2016-9841)

It was discovered that zlib incorrectly handled vectors involving left shifts of negative integers. An attacker could use this issue to cause zlib to crash, resulting in a denial of service, or possibly execute arbitrary code. (CVE-2016-9842)

It was discovered that zlib incorrectly handled vectors involving big-endian CRC calculation. An attacker could use this issue to cause zlib to crash, resulting in a denial of service, or possibly execute arbitrary code. (CVE-2016-9843)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 16.04 LTS

[lib32z1](https://launchpad.net/ubuntu/+source/zlib) - [1:1.2.8.dfsg-2ubuntu4.3](https://launchpad.net/ubuntu/+source/zlib/1:1.2.8.dfsg-2ubuntu4.3)

[lib64z1](https://launchpad.net/ubuntu/+source/zlib) - [1:1.2.8.dfsg-2ubuntu4.3](https://launchpad.net/ubuntu/+source/zlib/1:1.2.8.dfsg-2ubuntu4.3)

[libn32z1](https://launchpad.net/ubuntu/+source/zlib) - [1:1.2.8.dfsg-2ubuntu4.3](https://launchpad.net/ubuntu/+source/zlib/1:1.2.8.dfsg-2ubuntu4.3)

[libx32z1](https://launchpad.net/ubuntu/+source/zlib) - [1:1.2.8.dfsg-2ubuntu4.3](https://launchpad.net/ubuntu/+source/zlib/1:1.2.8.dfsg-2ubuntu4.3)

[zlib1g](https://launchpad.net/ubuntu/+source/zlib) - [1:1.2.8.dfsg-2ubuntu4.3](https://launchpad.net/ubuntu/+source/zlib/1:1.2.8.dfsg-2ubuntu4.3)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

In general, a standard system update will make all the necessary changes.

References
----------

*   [CVE-2016-9840](https://people.canonical.com/~ubuntu-security/cve/CVE-2016-9840)
*   [CVE-2016-9841](https://people.canonical.com/~ubuntu-security/cve/CVE-2016-9841)
*   [CVE-2016-9842](https://people.canonical.com/~ubuntu-security/cve/CVE-2016-9842)
*   [CVE-2016-9843](https://people.canonical.com/~ubuntu-security/cve/CVE-2016-9843)

  
  
from Ubuntu Security Notices https://ift.tt/2TJAClL