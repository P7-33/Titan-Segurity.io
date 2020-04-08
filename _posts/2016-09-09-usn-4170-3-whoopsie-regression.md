---
title: 'USN-4170-3: Whoopsie regression'
date: 2019-11-05T05:37:00+01:00
draft: false
---

whoopsie regression
-------------------

A security issue affects these releases of Ubuntu and its derivatives:

*   Ubuntu 19.10
*   Ubuntu 19.04
*   Ubuntu 18.04 LTS
*   Ubuntu 16.04 LTS

### Summary

USN-4170-2 caused a regression in Whoopsie

### Software Description

*   whoopsie - Ubuntu error tracker submission

### Details

USN-4170-1 fixed a vulnerability in Whoopsie and USN-4170-2 fixed a subsequent regression. That update was incomplete and could still result in Whoopsie potentially crashing when uploading crash reports on some architectures. This update fixes the problem.

We apologize for the inconvenience.

Original advisory details:

Kevin Backhouse discovered Whoopsie incorrectly handled very large crash reports. A local attacker could possibly use this issue to cause a denial of service, expose sensitive information or execute code as the whoopsie user.

Update instructions
-------------------

The problem can be corrected by updating your system to the following package versions:

Ubuntu 19.10

[libwhoopsie0](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.66ubuntu0.3](https://launchpad.net/ubuntu/+source/whoopsie/0.2.66ubuntu0.3)

[whoopsie](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.66ubuntu0.3](https://launchpad.net/ubuntu/+source/whoopsie/0.2.66ubuntu0.3)

Ubuntu 19.04

[libwhoopsie0](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.64ubuntu0.4](https://launchpad.net/ubuntu/+source/whoopsie/0.2.64ubuntu0.4)

[whoopsie](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.64ubuntu0.4](https://launchpad.net/ubuntu/+source/whoopsie/0.2.64ubuntu0.4)

Ubuntu 18.04 LTS

[libwhoopsie0](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.62ubuntu0.4](https://launchpad.net/ubuntu/+source/whoopsie/0.2.62ubuntu0.4)

[whoopsie](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.62ubuntu0.4](https://launchpad.net/ubuntu/+source/whoopsie/0.2.62ubuntu0.4)

Ubuntu 16.04 LTS

[libwhoopsie0](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.52.5ubuntu0.4](https://launchpad.net/ubuntu/+source/whoopsie/0.2.52.5ubuntu0.4)

[whoopsie](https://launchpad.net/ubuntu/+source/whoopsie) - [0.2.52.5ubuntu0.4](https://launchpad.net/ubuntu/+source/whoopsie/0.2.52.5ubuntu0.4)

To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

In general, a standard system update will make all the necessary changes.

References
----------

*   [USN-4170-1](https://usn.ubuntu.com/usn/usn-4170-1)
*   [LP: 1850608](https://launchpad.net/bugs/1850608)

  
  
from Ubuntu Security Notices https://ift.tt/2JMAufm