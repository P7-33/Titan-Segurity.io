---
title: 'Show HN: Localdots – HTTPS domains for localhost with autoconfig and hot reload'
date: 2019-12-28T07:07:00+01:00
draft: false
---

[](https://github.com/luisfarzati/localdots#localdots--https-domains-for-development)localdots — HTTPS domains for development
==============================================================================================================================

[![Docker Cloud Build Status](https://camo.githubusercontent.com/141cfb9d88c107d0aa150fcd6fcbf42696386a5c/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f636c6f75642f6275696c642f726e62772f6c6f63616c646f7473)](https://camo.githubusercontent.com/141cfb9d88c107d0aa150fcd6fcbf42696386a5c/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f636c6f75642f6275696c642f726e62772f6c6f63616c646f7473)

### [](https://github.com/luisfarzati/localdots#important)Important

As the title says, this tool is to be used for development. It is not meant to run at production and it hasn't been tested in CI environments either.

Please help report any issues!

[](https://github.com/luisfarzati/localdots#features)Features
-------------------------------------------------------------

localdots combines [Caddy](https://github.com/caddyserver/caddy) and [smallstep/certificates](https://github.com/smallstep/certificates) with automated configuration and hot reload.

*   Generates SSL/TLS certificates automatically
*   Reloads Caddy automatically with every change

[](https://github.com/luisfarzati/localdots#usage)Usage
-------------------------------------------------------

```
# docker-compose.yaml version: "3" services: proxy: image: rnbw/localdots ports: - 80:80 # for http->https redirection - 443:443 volumes: # contains all vhost files - ./caddy.d:/caddy.d:ro # contains CA config and certs - ~/.caroot:/caroot # only needed for \*.localhost domains extra\_hosts: - "whoami.localhost:127.0.0.1" # example containers whoami: image: jwilder/whoami hello: image: nginxdemos/hello
```

```
# ./caddy.d/whoami.localhost whoami.localhost { proxy / whoami:8000 } # ./caddy.d/hello.dev hello.dev { proxy / hello }
```

```
# run all the things docker-compose up -d # add the domains to your /etc/hosts file # \*.localhost domains shouldn't need to be added 127.0.0.1 hello.dev # after localdots container is up and running, # you will see a .caroot directory in your $HOME. brew install step \\ && step certificate install ~/.caroot/certs/root\_ca.crt # that's it, try open the sites configured above open https://whoami.localhost open https://hello.dev
```

  
  
from Hacker News https://github.com/luisfarzati/localdots