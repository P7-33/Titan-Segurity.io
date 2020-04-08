---
title: 'Dnscrypt-proxy 2 – A flexible DNS proxy with support for encrypted DNS protocols'
date: 2019-10-02T07:46:00+01:00
draft: false
---

[](https://github.com/DNSCrypt/dnscrypt-proxy)[![dnscrypt-proxy 2](https://camo.githubusercontent.com/bfb4b6307f78352fe882bc353d6bd8cfa992a316/68747470733a2f2f7261772e6769746875622e636f6d2f646e7363727970742f646e7363727970742d70726f78792f6d61737465722f6c6f676f2e706e673f33)](https://camo.githubusercontent.com/bfb4b6307f78352fe882bc353d6bd8cfa992a316/68747470733a2f2f7261772e6769746875622e636f6d2f646e7363727970742f646e7363727970742d70726f78792f6d61737465722f6c6f676f2e706e673f33)
===============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

[![Financial Contributors on Open Collective](https://camo.githubusercontent.com/05014716c0f44cf9809a3126f6d3911606b1f25e/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f616c6c2f62616467652e7376673f6c6162656c3d66696e616e6369616c2b636f6e7472696275746f7273)](https://opencollective.com/dnscrypt) [![DNSCrypt-Proxy Release](https://camo.githubusercontent.com/96e4cd79c1fc6524836fd47e90b71e0e344dd016/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f646e7363727970742f646e7363727970742d70726f78792e7376673f6c6162656c3d4c617465737425323052656c65617365267374796c653d706f706f7574)](https://github.com/dnscrypt/dnscrypt-proxy/releases/latest) [![Build Status](https://camo.githubusercontent.com/47ee76034c353f9b54e3d187cacd482dcdbd2974/68747470733a2f2f7472617669732d63692e6f72672f646e7363727970742f646e7363727970742d70726f78792e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/dnscrypt/dnscrypt-proxy?branch=master) [![#dnscrypt-proxy:matrix.org](https://camo.githubusercontent.com/9dd61b2a7f09c1248864ad757c04fe50d6c1aefe/68747470733a2f2f696d672e736869656c64732e696f2f6d61747269782f646e7363727970742d70726f78793a6d61747269782e6f72672e7376673f6c6162656c3d444e5343727970742d50726f78792532304d617472697825323043686174267365727665725f6671646e3d6d61747269782e6f7267267374796c653d706f706f7574)](https://matrix.to/#/#dnscrypt-proxy:matrix.org)

[](https://github.com/DNSCrypt/dnscrypt-proxy#overview)Overview
---------------------------------------------------------------

A flexible DNS proxy, with support for modern encrypted DNS protocols such as [DNSCrypt v2](https://dnscrypt.info/protocol) and [DNS-over-HTTPS](https://www.rfc-editor.org/rfc/rfc8484.txt).

Available as source code and pre-built binaries for most operating systems and architectures (see below).

[](https://github.com/DNSCrypt/dnscrypt-proxy#features)Features
---------------------------------------------------------------

*   DNS traffic encryption and authentication. Supports DNS-over-HTTPS (DoH) using TLS 1.3, and DNSCrypt.
*   DNS query monitoring, with separate log files for regular and suspicious queries
*   Filtering: block ads, malware, and other unwanted content. Compatible with all DNS services
*   Time-based filtering, with a flexible weekly schedule
*   Transparent redirection of specific domains to specific resolvers
*   DNS caching, to reduce latency and improve privacy
*   Local IPv6 blocking to reduce latency on IPv4-only networks
*   Load balancing: pick a set of resolvers, dnscrypt-proxy will automatically measure and keep track of their speed, and balance the traffic across the fastest available ones.
*   Cloaking: like a `HOSTS` file on steroids, that can return preconfigured addresses for specific names, or resolve and return the IP address of other names. This can be used for local development as well as to enforce safe search results on Google, Yahoo and Bing.
*   Automatic background updates of resolvers lists
*   Can force outgoing connections to use TCP
*   Supports SOCKS proxies
*   Compatible with DNSSEC

[](https://github.com/DNSCrypt/dnscrypt-proxy#pre-built-binaries)Pre-built binaries
-----------------------------------------------------------------------------------

Up-to-date, pre-built binaries are available for:

*   Android/arm
*   Android/arm64
*   Android/x86
*   Android/x86\_64
*   Dragonfly BSD
*   FreeBSD/arm
*   FreeBSD/x86
*   FreeBSD/x86\_64
*   Linux/arm
*   Linux/arm64
*   Linux/mips
*   Linux/mipsle
*   Linux/mips64
*   Linux/mips64le
*   Linux/x86
*   Linux/x86\_64
*   MacOS X
*   NetBSD/x86
*   NetBSD/x86\_64
*   OpenBSD/x86
*   OpenBSD/x86\_64
*   Windows
*   Windows 64 bit

How to use these files, as well as how to verify their signatures, are documented in the [installation instructions](https://github.com/dnscrypt/dnscrypt-proxy/wiki/installation).

[](https://github.com/DNSCrypt/dnscrypt-proxy#contributors)Contributors
-----------------------------------------------------------------------

### [](https://github.com/DNSCrypt/dnscrypt-proxy#code-contributors)Code Contributors

This project exists thanks to all the people who contribute. \[[Contribute](https://github.com/DNSCrypt/dnscrypt-proxy/blob/master/CONTRIBUTING.md)\]. [![](https://camo.githubusercontent.com/ff6c8283c9f02a40f4690bcc096a4fe0547dd951/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f636f6e7472696275746f72732e7376673f77696474683d38393026627574746f6e3d66616c7365)](https://github.com/dnscrypt/dnscrypt-proxy/graphs/contributors)

### [](https://github.com/DNSCrypt/dnscrypt-proxy#financial-contributors)Financial Contributors

Become a financial contributor and help us sustain our community. \[[Contribute](https://opencollective.com/dnscrypt/contribute)\]

#### [](https://github.com/DNSCrypt/dnscrypt-proxy#individuals)Individuals

[![](https://camo.githubusercontent.com/91e9d6413e64a6b9529bcdecf7e5dd0caf5501e5/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f696e646976696475616c732e7376673f77696474683d383930)](https://opencollective.com/dnscrypt)

#### [](https://github.com/DNSCrypt/dnscrypt-proxy#organizations)Organizations

Support this project with your organization. Your logo will show up here with a link to your website. \[[Contribute](https://opencollective.com/dnscrypt/contribute)\]

[![](https://camo.githubusercontent.com/8a00c62f54f3c802f635595d1a362bcc47208711/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f302f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/0/website) [![](https://camo.githubusercontent.com/2908d6e394986c325b8a84fde772ad87e8397795/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f312f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/1/website) [![](https://camo.githubusercontent.com/07ca51ed2c5c319b7810b4294c6eb8d0740e7a93/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f322f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/2/website) [![](https://camo.githubusercontent.com/ca4e2a387ffe747f583836b823efe6e694f90d18/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f332f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/3/website) [![](https://camo.githubusercontent.com/b76bcc100c124d922306eb61c27448ca26757d1c/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f342f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/4/website) [![](https://camo.githubusercontent.com/ba69aa267b980d5e1eab082d6d213500aac683fe/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f352f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/5/website) [![](https://camo.githubusercontent.com/12506f8f76cc04b73eee4fab96a834b4bfce7487/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f362f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/6/website) [![](https://camo.githubusercontent.com/5815921cc66ffc7863cd922be1a764b5129f94e9/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f372f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/7/website) [![](https://camo.githubusercontent.com/a284f7ae25f152bb9ffe42cbd8dd2a9da0250ba3/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f382f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/8/website) [![](https://camo.githubusercontent.com/78f4119a46b7fc77ecec7dffb5c7e1293ceec112/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f646e7363727970742f6f7267616e697a6174696f6e2f392f6176617461722e737667)](https://opencollective.com/dnscrypt/organization/9/website)

  
  
from Hacker News https://ift.tt/2OddjOs