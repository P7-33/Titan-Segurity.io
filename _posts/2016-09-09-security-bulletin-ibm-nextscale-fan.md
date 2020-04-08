---
title: 'Security Bulletin: IBM NeXtScale Fan Power Controller (FPC) is affected by vulnerability in OpenSSL (CVE-2019-1559)'
date: 2019-11-13T02:57:00+01:00
draft: false
---

CVEID:   CVE-2019-1559 DESCRIPTION:   If an application encounters a fatal protocol error and then calls SSL\_shutdown() twice (once to send a close\_notify, and once to receive one) then OpenSSL can respond differently to the calling application if a 0 byte record is received with invalid padding compared to if a 0 byte record is received with an invalid MAC. If the application then behaves differently based on that in a way that is detectable to the remote peer, then this amounts to a padding oracle that could be used to decrypt data. In order for this to be exploitable "non-stitched" ciphersuites must be in use. Stitched ciphersuites are optimised implementations of certain commonly used ciphersuites. Also the application must call SSL\_shutdown() twice even if a protocol error has occurred (applications should not do this but some do anyway). Fixed in OpenSSL 1.0.2r (Affected 1.0.2-1.0.2q).CVSS Base score: 5.8CVSS Temporal Score: See: https://ift.tt/2X61wnw for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:C/C:L/I:N/A:N) [...read more](https://www.ibm.com/blogs/psirt/security-bulletin-ibm-nextscale-fan-power-controller-fpc-is-affected-by-vulnerability-in-openssl-cve-2019-1559/)

  
  
from IBM Product Security Incident Response Team https://ift.tt/2X7jjKS