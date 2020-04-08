---
title: 'Security Bulletin: OpenSSL vulnerabilites impacting IBM Aspera Connect 3.7.4 and earlier (CVE-2017-3732, CVE-2016-7055)'
date: 2019-11-15T01:31:00+01:00
draft: false
---

CVEID:   CVE-2019-16335 DESCRIPTION:   A Polymorphic Typing issue was discovered in FasterXML jackson-databind before 2.9.10. It is related to com.zaxxer.hikari.HikariDataSource. This is a different vulnerability than CVE-2019-14540.CVSS Base score: 5.3CVSS Temporal Score: See: https://ift.tt/2QkR8GV for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N)  
   
CVEID:   CVE-2019-17267 DESCRIPTION:   A Polymorphic Typing issue was discovered in FasterXML jackson-databind before 2.9.10. It is related to net.sf.ehcache.hibernate.EhcacheJtaTransactionManagerLookup.CVSS Base score: 7.3CVSS Temporal Score: See: https://ift.tt/2OhjGPf for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L)  
   
CVEID:   CVE-2019-16943 DESCRIPTION:   A Polymorphic Typing issue was discovered in FasterXML jackson-databind 2.0.0 through 2.9.10. When Default Typing is enabled (either globally or for a specific property) for an externally exposed JSON endpoint and the service has the p6spy (3.8.6) jar in the classpath, and an attacker can find an RMI service endpoint to access, it is possible to make the service execute a malicious payload. This issue exists because of com.p6spy.engine.spy.P6DataSource mishandling.CVSS Base score: 9.8CVSS Temporal Score: See: https://ift.tt/2OgOu2f for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)  
   
CVEID:   CVE-2019-16942 DESCRIPTION:   A Polymorphic Typing issue was discovered in FasterXML jackson-databind 2.0.0 through 2.9.10. When Default Typing is enabled (either globally or for a specific property) for an externally exposed JSON endpoint and the service has the commons-dbcp (1.4) jar in the classpath, and an attacker can find an RMI service endpoint to access, it is possible to make the service execute a malicious payload. This issue exists because of org.apache.commons.dbcp.datasources.SharedPoolDataSource and org.apache.commons.dbcp.datasources.PerUserPoolDataSource mishandling.CVSS Base score: 9.8CVSS Temporal Score: See: https://ift.tt/2KksMcv for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)  
   
CVEID:   CVE-2019-14540DESCRIPTION:   FasterXML jackson-databind could allow a remote attacker to obtain sensitive information, caused by a polymorphic typing issue in com.zaxxer.hikari.HikariConfig. A remote attacker could exploit this vulnerability to obtain sensitive information.CVSS Base score: 5.3CVSS Temporal Score: See: https://ift.tt/2KmRsBm for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N)  
  [...read more](https://www.ibm.com/blogs/psirt/security-bulletin-security-vulnerabilities-affect-ibm-cloud-object-storage-sdk-java-november-2019-bulletin/)

  
  
from IBM Product Security Incident Response Team https://ift.tt/2Qk0Idf