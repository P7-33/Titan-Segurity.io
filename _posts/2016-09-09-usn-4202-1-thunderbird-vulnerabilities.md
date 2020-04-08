---
title: 'USN-4202-1: Thunderbird vulnerabilities'
date: 2019-11-27T01:16:00+01:00
draft: false
---

thunderbird vulnerabilities
---------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 18.04 LTS

### Summary

Several security issues were fixed in Thunderbird.

### Software Description

*   thunderbird - Mozilla Open Source mail and newsgroup client

### Details

It was discovered that a specially crafted S/MIME message with an inner encryption layer could be displayed as having a valid signature in some circumstances, even if the signer had no access to the encrypted message. An attacker could potentially exploit this to spoof the message author. (CVE-2019-11755)

Multiple security issues were discovered in Thunderbird. If a user were tricked in to opening a specially crafted website in a browsing context, an attacker could potentially exploit these to cause a denial of service, bypass security restrictions, bypass same-origin restrictions, conduct cross-site scripting (XSS) attacks, or execute arbitrary code. (CVE-2019-11757, CVE-2019-11758, CVE-2019-11759, CVE-2019-11760, CVE-2019-11761, CVE-2019-11762, CVE-2019-11763, CVE-2019-11764)

A heap overflow was discovered in the expat library in Thunderbird. If a user were tricked in to opening a specially crafted message, an attacker could potentially exploit this to cause a denial of service, or execute arbitrary code. (CVE-2019-15903)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[thunderbird](https://launchpad.net/ubuntu/+source/thunderbird) - [1:68.2.1+build1-0ubuntu0.19.10.1](https://launchpad.net/ubuntu/+source/thunderbird/1:68.2.1+build1-0ubuntu0.19.10.1)

Ubuntu 18.04 LTS

[thunderbird](https://launchpad.net/ubuntu/+source/thunderbird) - [1:68.2.1+build1-0ubuntu0.18.04.1](https://launchpad.net/ubuntu/+source/thunderbird/1:68.2.1+build1-0ubuntu0.18.04.1)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

After a standard system update you need to restart Thunderbird to make all the necessary changes.

References
----------

*   [CVE-2019-11755](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11755)
*   [CVE-2019-11757](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11757)
*   [CVE-2019-11758](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11758)
*   [CVE-2019-11759](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11759)
*   [CVE-2019-11760](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11760)
*   [CVE-2019-11761](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11761)
*   [CVE-2019-11762](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11762)
*   [CVE-2019-11763](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11763)
*   [CVE-2019-11764](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-11764)
*   [CVE-2019-15903](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15903)

  
  
from Ubuntu Security Notices https://ift.tt/2DmaTq8