---
title: 'TPM–Fail: TPM Meets Timing and Lattice Attacks'
date: 2019-11-13T03:13:00+01:00
draft: false
---

Am I affected by these vulnerabilities?
---------------------------------------

There is a high chance that you are affected. This depends if any of your computing devices (laptop, tablet, desktop, etc.) use Intel fTPM or STMicroelectronics TPM chips.

Which computing devices are affected?
-------------------------------------

Desktop, laptop and server workstations manufactured by various vendors such as Dell, Lenovo, HP, etc. may use one of these affected TPM products. Please ask your OEM or consult an expert to see if your systems are affected by TPM-FAIL.

What can a hacker do with this?
-------------------------------

A hacker can use these vulnerabilities to forge digital signatures. If your operating system or any of the applications on your computer use the TPM to issue such digital signatures, the private signing key used for signature generation can be compromised. Compromised signing keys can be used to forge signatures for bypassing Authentication, tampering the OS, and other bad things depending on what the digital signatures are used for.

Can I rely on security certificates to protect my customers?
------------------------------------------------------------

This research shows that even rigorous testing as required by Common Criteria certification is not flawless and may miss attacks that have explicitly been checked for. The STMicroelectronics TPM chip is Common Criteria certified at EAL4+ for the TPM protection profiles and FIPS 140-2 certified at level 2, while the Intel TPM is certified according to FIPS 140-2. However, the certification has failed to protect the product against an attack that is considered by the protection profile.

What is Common Criteria Certification?
--------------------------------------

Common Criteria certification is obtained via independent evaluation and is meant to provide security assurance including resistance to physical side-channel and timing attacks.

How practical are these attacks?
--------------------------------

They are practical. A local adversary can recover the ECDSA key from Intel fTPM in 4-20 minutes depending on the access level. We even show that these attacks can be performed remotely on fast networks, by recovering the authentication key of a virtual private network (VPN) server in 5 hours.

Is there any patch for these vulnerabilities?
---------------------------------------------

Intel upgraded their fTPM firmware to fix the reported vulnerabilities.

STMicroelectronics issued a new TPM chip and we have verified that it is resistant against TPM-FAIL.

Is there any CVE identifier for these vulnerabilities?
------------------------------------------------------

Yes. [CVE-2019-11090](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-11090) for Intel fTPM vulnerabilities and [CVE-2019-16863](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16863) for STMicroelectronics TPM chip.

What is a Common Vulnerability Exposure (CVE)?
----------------------------------------------

_[CVE](https://cve.mitre.org/) is a list containing identification number, a description, and at least one public reference for publicly known cybersecurity vulnerabilities._ It is a common practice by the security industry to assign CVE identifiers to track the status of vulnerabilities.

How can I learn more about TPM-FAIL?
------------------------------------

You can read the technical paper

[here](http://tpm.fail/TPM-FAIL.pdf)

. We are also presenting this work at the

[Real World Crypto 2020, New York (January 8-10, 2020)](https://rwc.iacr.org/2020/contributed.html)

and the

[29th USENIX Security Symposium, Boston (August 12-14, 2020)](https://www.usenix.org/conference/usenixsecurity20/presentation/moghimi)

.

  
  
from Hacker News http://tpm.fail/