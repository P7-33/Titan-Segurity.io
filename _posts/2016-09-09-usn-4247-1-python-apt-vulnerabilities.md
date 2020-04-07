---
title: 'USN-4247-1: python-apt vulnerabilities'
date: 2020-01-23T01:21:00+01:00
draft: false
---

python-apt vulnerabilities
--------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in python-apt.

### Software Description

*   python-apt - Python interface to libapt-pkg

### Details

It was discovered that python-apt would still use MD5 hashes to validate certain downloaded packages. If a remote attacker were able to perform a man-in-the-middle attack, this flaw could potentially be used to install altered packages. (CVE-2019-15795)

It was discovered that python-apt could install packages from untrusted repositories, contrary to expectations. (CVE-2019-15796)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[python-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.9.0ubuntu1.2](https://launchpad.net/ubuntu/+source/python-apt/1.9.0ubuntu1.2)

[python3-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.9.0ubuntu1.2](https://launchpad.net/ubuntu/+source/python-apt/1.9.0ubuntu1.2)

Ubuntu 19.04

[python-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.8.5~ubuntu0.2](https://launchpad.net/ubuntu/+source/python-apt/1.8.5~ubuntu0.2)

[python3-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.8.5~ubuntu0.2](https://launchpad.net/ubuntu/+source/python-apt/1.8.5~ubuntu0.2)

Ubuntu 18.04 LTS

[python-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.6.5ubuntu0.1](https://launchpad.net/ubuntu/+source/python-apt/1.6.5ubuntu0.1)

[python3-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.6.5ubuntu0.1](https://launchpad.net/ubuntu/+source/python-apt/1.6.5ubuntu0.1)

Ubuntu 16.04 LTS

[python-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.1.0~beta1ubuntu0.16.04.7](https://launchpad.net/ubuntu/+source/python-apt/1.1.0~beta1ubuntu0.16.04.7)

[python3-apt](https://launchpad.net/ubuntu/+source/python-apt) - [1.1.0~beta1ubuntu0.16.04.7](https://launchpad.net/ubuntu/+source/python-apt/1.1.0~beta1ubuntu0.16.04.7)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

In general, a standard system update will make all the necessary changes.

References
----------

*   [CVE-2019-15795](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15795)
*   [CVE-2019-15796](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-15796)

  
  
from Ubuntu Security Notices https://ift.tt/3ayRrFV