---
title: 'Why does 1.1.1.1 not resolve archive.is?'
date: 2019-10-04T07:01:00+01:00
draft: false
---

![](https://cdn.sstatic.net/Sites/webapps/img/apple-touch-icon@2.png?v=f700edad5c7b "dns - Why does 1.1.1.1 not resolve archive.is? - Web Applications Stack Exchange")  

Official Statement
==================

**_archive.today_** had this to say about the issue:

[https://twitter.com/archiveis/status/1017902875949793285](https://twitter.com/archiveis/status/1017902875949793285)

> 2018-07-13T1545: yes, unlike other public DNS services, 1.1.1.1 does not support EDNS Client Subnet

[https://twitter.com/archiveis/status/1018691421182791680](https://twitter.com/archiveis/status/1018691421182791680)

> 2018-07-15T1958: "Having to do" is not so direct here. Absence of EDNS and massive mismatch (not only on AS/Country, but even on the continent level) of where DNS and related HTTP requests come from causes so many troubles so I consider EDNS-less requests from Cloudflare as invalid.

* * *

Technical Verification
======================

From a [technical perspective](https://serverfault.com/a/560059/110020), the claim could easily be verified by running the following commands; one can notice that the vast majority of public resolvers, other than 1.1.1.1, indeed do provide an `"edns0-client-subnet XX.XX.XX.0/24"` answer, which is necessary in order for the various CDN functionalities to work their best.

```
% dig +nocmd @dns.google. -t txt o-o.myaddr.l.google.com +nocomments +noall +answer +stats o-o.myaddr.l.google.com. 59 IN TXT "172.217.34.2" o-o.myaddr.l.google.com. 59 IN TXT "edns0-client-subnet XX.XX.XX.0/24" ;; Query time: 28 msec ;; SERVER: 8.8.4.4#53(8.8.4.4) ;; WHEN: Thu Oct 3 17:41:29 2019 ;; MSG SIZE rcvd: 113 % dig +nocmd @resolver1.opendns.com. -t txt o-o.myaddr.l.google.com +nocomments +noall +answer +stats o-o.myaddr.l.google.com. 60 IN TXT "2620:0:cc7::68" o-o.myaddr.l.google.com. 60 IN TXT "edns0-client-subnet XX.XX.XX.0/24" ;; Query time: 20 msec ;; SERVER: 208.67.222.222#53(208.67.222.222) ;; WHEN: Thu Oct 3 17:41:32 2019 ;; MSG SIZE rcvd: 115 % dig +nocmd @one.one.one.one. -t txt o-o.myaddr.l.google.com +nocomments +noall +answer +stats o-o.myaddr.l.google.com. 60 IN TXT "162.158.82.18" ;; Query time: 23 msec ;; SERVER: 1.0.0.1#53(1.0.0.1) ;; WHEN: Thu Oct 3 17:41:42 2019 ;; MSG SIZE rcvd: 67 % host 162.158.82.18 Host 18.82.158.162.in-addr.arpa not found: 2(SERVFAIL) % 
```

Even the less popular public resolvers that don't provide ECS, still qualify under archive.today's exception where the geolocation of the resolver is trivial to determine in a programmatic way:

```
% dig +nocmd @a.resolvers.level3.net -t txt o-o.myaddr.l.google.com +nocomments +noall +answer +stats o-o.myaddr.l.google.com. 60 IN TXT "8.0.18.0" ;; Query time: 14 msec ;; SERVER: 4.2.2.1#53(4.2.2.1) ;; WHEN: Thu Oct 3 19:24:44 2019 ;; MSG SIZE rcvd: 62 % host 8.0.18.0 0.18.0.8.in-addr.arpa domain name pointer cns1.Frankfurt1.Level3.net. % % dig +nocmd @ordns.he.net -t txt o-o.myaddr.l.google.com +nocomments +noall +answer +stats o-o.myaddr.l.google.com. 60 IN TXT "216.66.80.30" ;; Query time: 16 msec ;; SERVER: 74.82.42.42#53(74.82.42.42) ;; WHEN: Thu Oct 3 19:26:56 2019 ;; MSG SIZE rcvd: 66 % host 216.66.80.30 30.80.66.216.in-addr.arpa domain name pointer tserv1.fra1.he.net. % 
```

* * *

Conflict of Interest
====================

If you're a savvy internet operator, it doesn't take long to see a conflict of interest at play as well.

*   Cloudflare's main line of business is as a Content Delivery Network, as well as associated services like DDoS-protection and bot hinderance.
    
    To be most effective, they require their customers (website owners) to completely give up control over the technical setup of their website. For example, this includes a mandatory requirement of delegating your domain name, `example.org`, to a unique set of `cloudflare.com.` nameservers — Cloudflare does not allow their customers to make any assumptions about any IP addresses of any services at all — no IP address hardcoding. This applies not just to HTTP/HTTPS servers, but also to the authoritative DNS as well.
    
    Basically, unlike Linode and HE.net, they at Cloudflare don't even let you whitelabel their NS servers for free (i.e., use Cloudflare's IP addresses with your own domain name, like `ns1.example.org.` if you're the owner of `example.org`); this is done in order for Cloudflare to have the maximum and complete control over all available DoS remediation techniques, to be able to **_change any IP address of any service as seen by any client at any given time_**, as well as to facilitate request tracking for data collection, machine learning and traffic anomaly analysis.
    
    As such, with their new 1.1.1.1 service, free to end users, and subsidised out of their massive CDN business, Cloudflare's decision to deny their competitors and non-customers from having access to the very same level of information for their decision making that Cloudflare itself always has had access to — archive.today runs their own CDN network here — doesn't seem exactly like a level-playing field.
    
    This effectively forces operators like archive.today to either succumb to DoS attacks by not having all the tools available at their disposal to protect themselves against such attack (by giving misbehaving clients or subnets a distinct name resolution, as well as doing anomaly detection), or to become a Cloudflare CDN customer — how convenient for Cloudflare!
    
    Cloudflare touts their decision to omit EDNS Client Subnet as a privacy initiative (which is a rather disingenuous claim, as ECS is only specific to a `/24` (`/56` with IPv6), and [after the DNS resolution is complete, you'd still have to issue your HTTP/HTTPS request from your own IP address anyways](https://blog.powerdns.com/2019/09/25/centralised-doh-is-bad-for-privacy-in-2019-and-beyond/)), but I think it's easy to read between the lines that the only known monetisation from 1.1.1.1 would be tracking, machine-learning and upselling of Cloudflare's CDN offering.
    
    Failing to provide EDNS Client Subnet makes it significantly more difficult for someone like _archive.today_ to do the exact same things in their own CDN that Cloudflare itself enjoys on doing in their acclaimed commercial offering.
    
*   Does archive.is have a CoI as well? Perhaps. Bot-hindering CDNs like Cloudflare has had a net-positive effect for website owners at the price of a significant net-negative effect on certain less common internet users, where some [unlucky ones](https://www.slashgeek.net/2016/05/17/cloudflare-is-ruining-the-internet-for-me/) may now be required to [solve captchas on a daily basis all day long](https://www.slashgeek.net/2016/06/07/cloudflare-making-internet-little-bit-faster-select-group-people/). Obviously, it's easy to see how Cloudflare's oblivious captchas may have a significant negative effects on website archiving, too.
    

Nothing is exactly black and white, so, I'll leave you the reader to form your own conclusion.

  
  
from Hacker News https://ift.tt/2oNliHg