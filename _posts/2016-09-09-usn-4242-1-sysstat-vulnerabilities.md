---
title: 'USN-4242-1: Sysstat vulnerabilities'
date: 2020-01-21T01:29:00+01:00
draft: false
---

sysstat vulnerabilities
-----------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in Sysstat.

### Software Description

*   sysstat - system performance tools for Linux

### Details

It was discovered that Sysstat incorrectly handled certain inputs. An attacker could possibly use this issue to cause a crash or execute arbitrary code. This issue only affected Ubuntu 19.04 and Ubuntu 19.10. (CVE-2019-16167)

It was discovered that Sysstat incorrectly handled certain inputs. An attacker could possibly use this issue to execute arbitrary code. (CVE-2019-19725)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[sysstat](https://launchpad.net/ubuntu/+source/sysstat) - [12.0.6-1ubuntu0.1](https://launchpad.net/ubuntu/+source/sysstat/12.0.6-1ubuntu0.1)

Ubuntu 19.04

[sysstat](https://launchpad.net/ubuntu/+source/sysstat) - [12.0.1-1ubuntu0.1](https://launchpad.net/ubuntu/+source/sysstat/12.0.1-1ubuntu0.1)

Ubuntu 18.04 LTS

[sysstat](https://launchpad.net/ubuntu/+source/sysstat) - [11.6.1-1ubuntu0.1](https://launchpad.net/ubuntu/+source/sysstat/11.6.1-1ubuntu0.1)

Ubuntu 16.04 LTS

[sysstat](https://launchpad.net/ubuntu/+source/sysstat) - [11.2.0-1ubuntu0.3](https://launchpad.net/ubuntu/+source/sysstat/11.2.0-1ubuntu0.3)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

In general, a standard system update will make all the necessary changes.

References
----------

*   [CVE-2019-16167](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-16167)
*   [CVE-2019-19725](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-19725)

  
  
from Ubuntu Security Notices https://ift.tt/3arqSlX