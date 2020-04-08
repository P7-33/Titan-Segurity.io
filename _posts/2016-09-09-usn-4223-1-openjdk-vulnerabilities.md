---
title: 'USN-4223-1: OpenJDK vulnerabilities'
date: 2019-12-18T01:28:00+01:00
draft: false
---

openjdk-8, openjdk-lts vulnerabilities
--------------------------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

Several security issues were fixed in OpenJDK.

### Software Description

*   openjdk-lts - Open Source Java implementation
*   openjdk-8 - Open Source Java implementation

### Details

Jan Jancar, Petr Svenda, and Vladimir Sedlacek discovered that a side- channel vulnerability existed in the ECDSA implementation in OpenJDK. An Attacker could use this to expose sensitive information. (CVE-2019-2894)

It was discovered that the Socket implementation in OpenJDK did not properly restrict the creation of subclasses with a custom Socket implementation. An attacker could use this to specially create a Java class that could possibly bypass Java sandbox restrictions. (CVE-2019-2945)

Rob Hamm discovered that the Kerberos implementation in OpenJDK did not properly handle proxy credentials. An attacker could possibly use this to impersonate another user. (CVE-2019-2949)

It was discovered that a NULL pointer dereference existed in the font handling implementation in OpenJDK. An attacker could use this to cause a denial of service (application crash). (CVE-2019-2962)

It was discovered that the Concurrency subsystem in OpenJDK did not properly bound stack consumption when compiling regular expressions. An attacker could use this to cause a denial of service (application crash). (CVE-2019-2964)

It was discovered that the JAXP subsystem in OpenJDK did not properly handle XPath expressions in some situations. An attacker could use this to cause a denial of service (application crash). (CVE-2019-2973, CVE-2019-2981)

It was discovered that the Nashorn JavaScript subcomponent in OpenJDK did not properly handle regular expressions in some situations. An attacker could use this to cause a denial of service (application crash). (CVE-2019-2975)

It was discovered that the String class in OpenJDK contained an out-of- bounds access vulnerability. An attacker could use this to cause a denial of service (application crash) or possibly expose sensitive information. This issue only affected OpenJDK 11 in Ubuntu 18.04 LTS, Ubuntu 19.04, and Ubuntu 19.10. (CVE-2019-2977)

It was discovered that the Jar URL handler in OpenJDK did not properly handled nested Jar URLs in some situations. An attacker could use this to cause a denial of service (application crash). (CVE-2019-2978)

It was discovered that the Serialization component of OpenJDK did not properly handle deserialization of certain object attributes. An attacker could use this to cause a denial of service (application crash). (CVE-2019-2983)

It was discovered that the FreetypeFontScaler class in OpenJDK did not properly validate dimensions of glyph bitmap images read from font files. An attacker could specially craft a font file that could cause a denial of service (application crash). (CVE-2019-2987)

It was discovered that a buffer overflow existed in the SunGraphics2D class in OpenJDK. An attacker could possibly use this to cause a denial of service (excessive memory consumption or application crash). (CVE-2019-2988)

It was discovered that the Networking component in OpenJDK did not properly handle certain responses from HTTP proxies. An attacker controlling a malicious HTTP proxy could possibly use this to inject content into a proxied HTTP connection. (CVE-2019-2989)

It was discovered that the font handling implementation in OpenJDK did not properly validate TrueType font files in some situations. An attacker could specially craft a font file that could cause a denial of service (excessive memory consumption). (CVE-2019-2992)

It was discovered that the JavaDoc generator in OpenJDK did not properly filter out some HTML elements properly, including documentation comments in Java source code. An attacker could possibly use this to craft a Cross-Site Scripting attack. (CVE-2019-2999)

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[openjdk-11-jdk](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1)

[openjdk-11-jre](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1)

[openjdk-11-jre-headless](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1)

[openjdk-11-jre-zero](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1)

Ubuntu 19.04

[openjdk-11-jdk](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~19.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~19.04)

[openjdk-11-jre](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~19.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~19.04)

[openjdk-11-jre-headless](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~19.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~19.04)

[openjdk-11-jre-zero](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~19.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~19.04)

Ubuntu 18.04 LTS

[openjdk-11-jdk](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~18.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~18.04)

[openjdk-11-jre](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~18.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~18.04)

[openjdk-11-jre-headless](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~18.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~18.04)

[openjdk-11-jre-zero](https://launchpad.net/ubuntu/+source/openjdk-lts) - [11.0.5+10-0ubuntu1.1~18.04](https://launchpad.net/ubuntu/+source/openjdk-lts/11.0.5+10-0ubuntu1.1~18.04)

Ubuntu 16.04 LTS

[openjdk-8-jdk](https://launchpad.net/ubuntu/+source/openjdk-8) - [8u232-b09-0ubuntu1~16.04.1](https://launchpad.net/ubuntu/+source/openjdk-8/8u232-b09-0ubuntu1~16.04.1)

[openjdk-8-jre](https://launchpad.net/ubuntu/+source/openjdk-8) - [8u232-b09-0ubuntu1~16.04.1](https://launchpad.net/ubuntu/+source/openjdk-8/8u232-b09-0ubuntu1~16.04.1)

[openjdk-8-jre-headless](https://launchpad.net/ubuntu/+source/openjdk-8) - [8u232-b09-0ubuntu1~16.04.1](https://launchpad.net/ubuntu/+source/openjdk-8/8u232-b09-0ubuntu1~16.04.1)

[openjdk-8-jre-jamvm](https://launchpad.net/ubuntu/+source/openjdk-8) - [8u232-b09-0ubuntu1~16.04.1](https://launchpad.net/ubuntu/+source/openjdk-8/8u232-b09-0ubuntu1~16.04.1)

[openjdk-8-jre-zero](https://launchpad.net/ubuntu/+source/openjdk-8) - [8u232-b09-0ubuntu1~16.04.1](https://launchpad.net/ubuntu/+source/openjdk-8/8u232-b09-0ubuntu1~16.04.1)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

This update uses a new upstream release, which includes additional bug fixes. After a standard system update you need to restart any Java applications or applets to make all the necessary changes.

References
----------

*   [CVE-2019-2894](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2894)
*   [CVE-2019-2945](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2945)
*   [CVE-2019-2949](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2949)
*   [CVE-2019-2962](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2962)
*   [CVE-2019-2964](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2964)
*   [CVE-2019-2973](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2973)
*   [CVE-2019-2975](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2975)
*   [CVE-2019-2977](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2977)
*   [CVE-2019-2978](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2978)
*   [CVE-2019-2981](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2981)
*   [CVE-2019-2983](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2983)
*   [CVE-2019-2987](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2987)
*   [CVE-2019-2988](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2988)
*   [CVE-2019-2989](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2989)
*   [CVE-2019-2992](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2992)
*   [CVE-2019-2999](https://people.canonical.com/~ubuntu-security/cve/CVE-2019-2999)

  
  
from Ubuntu Security Notices https://ift.tt/35z7RuS