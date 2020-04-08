---
title: 'Security Bulletin: IBM Watson Discovery for IBM Cloud Pak for Data affected by vulnerability in FasterXML jackson-databind'
date: 2019-12-07T01:38:00+01:00
draft: false
---

CVEID:   CVE-2019-16943 DESCRIPTION:   A Polymorphic Typing issue was discovered in FasterXML jackson-databind 2.0.0 through 2.9.10. When Default Typing is enabled (either globally or for a specific property) for an externally exposed JSON endpoint and the service has the p6spy (3.8.6) jar in the classpath, and an attacker can find an RMI service endpoint to access, it is possible to make the service execute a malicious payload. This issue exists because of com.p6spy.engine.spy.P6DataSource mishandling.CVSS Base score: 9.8CVSS Temporal Score: See: https://ift.tt/2OgOu2f for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H) CVEID:   CVE-2019-16942 DESCRIPTION:   A Polymorphic Typing issue was discovered in FasterXML jackson-databind 2.0.0 through 2.9.10. When Default Typing is enabled (either globally or for a specific property) for an externally exposed JSON endpoint and the service has the commons-dbcp (1.4) jar in the classpath, and an attacker can find an RMI service endpoint to access, it is possible to make the service execute a malicious payload. This issue exists because of org.apache.commons.dbcp.datasources.SharedPoolDataSource and org.apache.commons.dbcp.datasources.PerUserPoolDataSource mishandling.CVSS Base score: 9.8CVSS Temporal Score: See: https://ift.tt/2KksMcv for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H) [...read more](https://www.ibm.com/blogs/psirt/security-bulletin-ibm-watson-discovery-for-ibm-cloud-pak-for-data-affected-by-vulnerability-in-fasterxml-jackson-databind-4/)

  
  
from IBM Product Security Incident Response Team https://ift.tt/2Yof6TO