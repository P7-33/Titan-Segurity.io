---
title: 'USN-4200-1: Redmine vulnerabilities'
date: 2019-11-26T03:16:00+01:00
draft: false
---

redmine vulnerabilities
-----------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in redmine.

### Software Description

*   redmine - flexible project management web application

### Details

It was discovered that Redmine incorrectly handle certain inputs that could cause textile formatting errors. An attacker could possibly use this issue to cause a XSS attack. (CVE-2019-17427)

It was discovered that an SQL injection could allow users to access protected information via a crafted object query. (CVE-2019-18890)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.04

[redmine](https://launchpad.net/ubuntu/+source/redmine) - [4.0.1-2ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/4.0.1-2ubuntu0.1)

[redmine-mysql](https://launchpad.net/ubuntu/+source/redmine) - [4.0.1-2ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/4.0.1-2ubuntu0.1)

[redmine-pgsql](https://launchpad.net/ubuntu/+source/redmine) - [4.0.1-2ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/4.0.1-2ubuntu0.1)

[redmine-sqlite](https://launchpad.net/ubuntu/+source/redmine) - [4.0.1-2ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/4.0.1-2ubuntu0.1)

Ubuntu 18.04 LTS

[redmine](https://launchpad.net/ubuntu/+source/redmine) - [3.4.4-1ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/3.4.4-1ubuntu0.1)

[redmine-mysql](https://launchpad.net/ubuntu/+source/redmine) - [3.4.4-1ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/3.4.4-1ubuntu0.1)

[redmine-pgsql](https://launchpad.net/ubuntu/+source/redmine) - [3.4.4-1ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/3.4.4-1ubuntu0.1)

[redmine-sqlite](https://launchpad.net/ubuntu/+source/redmine) - [3.4.4-1ubuntu0.1](https://launchpad.net/ubuntu/+source/redmine/3.4.4-1ubuntu0.1)

Ubuntu 16.04 LTS

[redmine](https://launchpad.net/ubuntu/+source/redmine) - [3.2.1-2ubuntu0.2](https://launchpad.net/ubuntu/+source/redmine/3.2.1-2ubuntu0.2)

[redmine-mysql](https://launchpad.net/ubuntu/+source/redmine) - [3.2.1-2ubuntu0.2](https://launchpad.net/ubuntu/+source/redmine/3.2.1-2ubuntu0.2)

[redmine-pgsql](https://launchpad.net/ubuntu/+source/redmine) - [3.2.1-2ubuntu0.2](https://launchpad.net/ubuntu/+source/redmine/3.2.1-2ubuntu0.2)

[redmine-sqlite](https://launchpad.net/ubuntu/+source/redmine) - [3.2.1-2ubuntu0.2](https://launchpad.net/ubuntu/+source/redmine/3.2.1-2ubuntu0.2)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

In general, a standard system update will make all the necessary changes.

References
----------

*   [CVE-2019-17427](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-17427)
*   [CVE-2019-18890](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-18890)

  
  
from Ubuntu Security Notices https://ift.tt/2pVftbO