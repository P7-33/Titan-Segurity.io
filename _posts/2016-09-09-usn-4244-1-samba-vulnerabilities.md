---
title: 'USN-4244-1: Samba vulnerabilities'
date: 2020-01-22T01:21:00+01:00
draft: false
---

samba vulnerabilities
---------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in Samba.

### Software Description

*   samba - SMB/CIFS file, print, and login server for Unix

### Details

It was discovered that Samba did not automatically replicate ACLs set to inherit down a subtree on AD Directory, contrary to expectations. This issue was only addressed in Ubuntu 18.04 LTS, Ubuntu 19.04 and Ubuntu 19.10. (CVE-2019-14902)

Robert Święcki discovered that Samba incorrectly handled certain character conversions when the log level is set to 3 or above. In certain environments, a remote attacker could possibly use this issue to cause Samba to crash, resulting in a denial of service. (CVE-2019-14907)

Christian Naumer discovered that Samba incorrectly handled DNS zone scavenging. This issue could possibly result in some incorrect data being written to the DB. This issue only applied to Ubuntu 19.04 and Ubuntu 19.10. (CVE-2019-19344)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[samba](https://launchpad.net/ubuntu/+source/samba) - [2:4.10.7+dfsg-0ubuntu2.4](https://launchpad.net/ubuntu/+source/samba/2:4.10.7+dfsg-0ubuntu2.4)

Ubuntu 19.04

[samba](https://launchpad.net/ubuntu/+source/samba) - [2:4.10.0+dfsg-0ubuntu2.8](https://launchpad.net/ubuntu/+source/samba/2:4.10.0+dfsg-0ubuntu2.8)

Ubuntu 18.04 LTS

[samba](https://launchpad.net/ubuntu/+source/samba) - [2:4.7.6+dfsg~ubuntu-0ubuntu2.15](https://launchpad.net/ubuntu/+source/samba/2:4.7.6+dfsg~ubuntu-0ubuntu2.15)

Ubuntu 16.04 LTS

[samba](https://launchpad.net/ubuntu/+source/samba) - [2:4.3.11+dfsg-0ubuntu0.16.04.25](https://launchpad.net/ubuntu/+source/samba/2:4.3.11+dfsg-0ubuntu0.16.04.25)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

In general, a standard system update will make all the necessary changes.

References
----------

*   [CVE-2019-14902](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14902)
*   [CVE-2019-14907](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-14907)
*   [CVE-2019-19344](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19344)

  
  
from Ubuntu Security Notices https://ift.tt/36i2rUC