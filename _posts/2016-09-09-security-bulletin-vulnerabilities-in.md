---
title: 'Security Bulletin: Vulnerabilities in OpenSSL affect AIX (CVE-2019-1547, CVE-2019-1563)'
date: 2019-11-27T01:08:00+01:00
draft: false
---

Nov 26, 2019 7:00 pm EST

Categorized: [Medium Severity](https://www.ibm.com/blogs/psirt/category/severity-med/)

Share this post:

There are vulnerabilities in OpenSSL used by AIX.

**Affected product(s) and affected version(s):**

Affected Product(s)

Version(s)

AIX

7.1

AIX

7.2

VIOS

2.2

VIOS

3.1

The following fileset levels are vulnerable:

key\_fileset = osrcaix

Fileset

Lower Level

Upper Level

Key

openssl.base

1.0.2.500

1.0.2.1801

key\_w\_fs

openssl.base

20.13.102.1000

20.16.102.1801

key\_w\_fs

Note:

        A. 0.9.8, 1.0.1 OpenSSL versions are out-of-support. Customers are advised to upgrade to currently supported OpenSSL 1.0.2 version.

        B. Latest level of OpenSSL fileset is available from the web download site:

To find out whether the affected filesets are installed on your systems, refer to the lslpp command found in the AIX user's guide.

Example:  lslpp -L | grep -i openssl.base

**Refer to the following reference URLs for remediation and additional vulnerability details:  **  
Source Bulletin: [https://www.ibm.com/support/pages/node/1116033](https://www.ibm.com/support/pages/node/1116033)

  
  
from IBM Product Security Incident Response Team https://ift.tt/2QThpfZ