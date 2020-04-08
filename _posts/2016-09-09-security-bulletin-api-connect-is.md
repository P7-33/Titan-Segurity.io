---
title: 'Security Bulletin: API Connect is impacted by credential caching'
date: 2019-12-14T01:22:00+01:00
draft: false
---

CVEID:   CVE-2019-11246 DESCRIPTION:   The kubectl cp command allows copying files between containers and the user machine. To copy files from a container, Kubernetes runs tar inside the container to create a tar archive, copies it over the network, and kubectl unpacks it on the user?s machine. If the tar binary in the container is malicious, it could run any code and output unexpected, malicious results. An attacker could use this to write files to any path on the user?s machine when kubectl cp is called, limited only by the system permissions of the local user. Kubernetes affected versions include versions prior to 1.12.9, versions prior to 1.13.6, versions prior to 1.14.2, and versions 1.1, 1.2, 1.4, 1.4, 1.5, 1.6, 1.7, 1.8, 1.9, 1.10, 1.11.CVSS Base score: 5.3CVSS Temporal Score: See: https://ift.tt/2sp4CaZ for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:N/I:H/A:N) [...read more](https://www.ibm.com/blogs/psirt/security-bulletin-a-security-vulnerability-has-been-identified-in-kubernetes-shipped-with-powerai-vision/)

  
  
from IBM Product Security Incident Response Team https://ift.tt/38FNX3E