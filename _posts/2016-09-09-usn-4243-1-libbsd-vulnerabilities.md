---
title: 'USN-4243-1: libbsd vulnerabilities'
date: 2020-01-21T01:29:00+01:00
draft: false
---

libbsd vulnerabilities
----------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS
*   Ubuntu 14.04 ESM
*   Ubuntu 12.04 ESM

### Summary

Several security issues were fixed in libbsd.

### Software Description

*   libbsd - utility functions from BSD systems - development files

### Details

It was discovered that libbsd incorrectly handled certain inputs. An attacker could possibly use this issue to execute arbitrary code. This issue only affected Ubuntu 14.04 ESM. (CVE-2016-2090)

It was discovered that libbsd incorrectly handled certain strings. An attacker could possibly use this issue to access sensitive information. (CVE-2019-20367)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.04

[libbsd0](https://launchpad.net/ubuntu/+source/libbsd) - [0.9.1-2ubuntu0.1](https://launchpad.net/ubuntu/+source/libbsd/0.9.1-2ubuntu0.1)

Ubuntu 18.04 LTS

[libbsd0](https://launchpad.net/ubuntu/+source/libbsd) - [0.8.7-1ubuntu0.1](https://launchpad.net/ubuntu/+source/libbsd/0.8.7-1ubuntu0.1)

Ubuntu 16.04 LTS

[libbsd0](https://launchpad.net/ubuntu/+source/libbsd) - [0.8.2-1ubuntu0.1](https://launchpad.net/ubuntu/+source/libbsd/0.8.2-1ubuntu0.1)

Ubuntu 14.04 ESM

libbsd0 - 0.6.0-2ubuntu1+esm1

Ubuntu 12.04 ESM

libbsd0 - 0.3.0-2ubuntu0.1

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

In general, a standard system update will make all the necessary changes.

References
----------

*   [CVE-2016-2090](https://people.canonical.com/~ubuntu-security/cve/CVE-2016-2090)
*   [CVE-2019-20367](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-20367)

  
  
from Ubuntu Security Notices https://ift.tt/30ELSB4