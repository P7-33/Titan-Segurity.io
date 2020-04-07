---
title: 'Security Bulletin: IBM has announced a release for IBM Security Identity Governance and Intelligence in response to security vulnerability (CVE-2019-3815)'
date: 2020-01-30T01:33:00+01:00
draft: false
---

IBM has announced a release for IBM Security Identity Governance and Intelligence (IGI) in response to security vulnerability. The systemd packages contain systemd, a system and service manager for Linux, compatible with the SysV and LSB init scripts. A memory leak was discovered in the backport of fixes for CVE-2018-16864 in Red Hat Enterprise Linux. Function dispatch\_message\_real() in journald-server.c does not free the memory allocated by set\_iovec\_field\_free() to store the \`\_CMDLINE=\` entry. A local attacker may use this flaw to make systemd-journald crash.

**Affected product(s) and affected version(s):**

Affected Product(s)

Version(s)

IBM Security Identity Governance and Intelligence

5.2.4

IBM Security Identity Governance and Intelligence

5.2.5

**Refer to the following reference URLs for remediation and additional vulnerability details:  **  
Source Bulletin: [https://www.ibm.com/support/pages/node/1284766](https://www.ibm.com/support/pages/node/1284766)

The post [Security Bulletin: IBM has announced a release for IBM Security Identity Governance and Intelligence in response to security vulnerability (CVE-2019-3815)](https://www.ibm.com/blogs/psirt/security-bulletin-ibm-has-announced-a-release-for-ibm-security-identity-governance-and-intelligence-in-response-to-security-vulnerability-cve-2019-3815/) appeared first on [IBM PSIRT Blog](https://www.ibm.com/blogs/psirt).

  
  
from IBM Product Security Incident Response Team https://ift.tt/2RZhC07