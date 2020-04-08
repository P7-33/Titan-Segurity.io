---
title: 'Security Bulletin:'
date: 2019-12-06T01:38:00+01:00
draft: false
---

CVEID:   CVE-2019-12410 DESCRIPTION:   While investigating UBSAN errors in https://ift.tt/2WY0euH it was discovered Apache Arrow versions 0.12.0 to 0.14.1, left memory Array data uninitialized when reading RLE null data from parquet. This affected the C++, Python, Ruby and R implementations. The uninitialized memory could potentially be shared if are transmitted over the wire (for instance with Flight) or persisted in the streaming IPC and file formats.CVSS Base score: 7.5CVSS Temporal Score: See: https://ift.tt/2YlOliG for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N) CVEID:   CVE-2019-12408 DESCRIPTION:   It was discovered that the C++ implementation (which underlies the R, Python and Ruby implementations) of Apache Arrow 0.14.0 to 0.14.1 had a uninitialized memory bug when building arrays with null values in some cases. This can lead to uninitialized memory being unintentionally shared if Arrow Arrays are transmitted over the wire (for instance with Flight) or persisted in the streaming IPC and file formats.CVSS Base score: 7.5CVSS Temporal Score: See: https://ift.tt/2Rq9ebk for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N) [...read more](https://www.ibm.com/blogs/psirt/security-bulletin-2/)

  
  
from IBM Product Security Incident Response Team https://ift.tt/2DOuuPI