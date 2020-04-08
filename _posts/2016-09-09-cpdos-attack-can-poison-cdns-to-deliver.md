---
title: 'CPDoS attack can poison CDNs to deliver error pages instead of legitimate sites'
date: 2019-10-23T05:02:00+01:00
draft: false
---

![CPDoS](https://zdnet1.cbsistatic.com/hub/i/2019/10/23/e8d3d064-ab1d-48c7-95d3-5f296f7a4bb8/7fd41bc5c6db8418f1baa0bf4b9b2688/cpdos.png)

Two academics from the Technical University of Cologne (TH Koln) have disclosed this week a new type of web attack that can poison content delivery networks (CDNs) into caching and then serving error pages instead of legitimate websites.

The new attack has been named CPDoS (Cache-Poisoned Denial-of-Service), has three variants, and has been deemed practical in the real world ([unlike most other web cache attacks](https://portswigger.net/research/practical-web-cache-poisoning)).

### How CPDoS attacks work

CPDoS attacks are aimed at two components of the modern web -- (1) web servers and (2) content delivery networks.

Web servers store the original website and its content, while CDNs store a cached copy of the website that is only refreshed at certain time intervals.

Despite their simplistic role, CDNs are a crucial part of the modern internet, as they can alleviate the load on web servers. Instead of a web server computing the same user request over and over again, a CDN can provide some of the incoming users with a copy of the website, until the CDN refreshes itself with a new version.

CDNs are widey used. Any attack on a CDN system can have devastating consequences on a website's availability, and, hence, it's profitability.

In this context, the CPDoS work like so:

*   An attacker connects to a website until his request is the ones that generates a new CDN entry
*   The attacker's request contains a malicious oversized HTTP header
*   The CDN allows this header to pass through to the legitimate site, so it can be processed and generate a web page for the CDN to cache
*   The oversized header crashes the web server
*   The server generates an error page (a "400 Bad Request" error)
*   The error page is cached on the CDN
*   Other users accessing the site get the error page instead of the actual website
*   The cached error spreads to other nodes of the CDN's network, creating a fake outage at a legitimate site

![cpdos-scheme.png](https://www.zdnet.com/article/cpdos-attack-can-poison-cdns-to-deliver-error-pages-instead-of-legitimate-sites/#ftag=RSSbaffb68)

<span><img src="https://zdnet2.cbsistatic.com/hub/i/2019/10/23/b36a514b-5ac9-4772-ab99-a68bcbee6d94/6566af605029963627a4e89a4fbb5765/cpdos-scheme.png" alt="cpdos-scheme.png" /></span>

Image: Nguyen et al.

According to the research team, three variants of the CPDoS attack exist, depending on the HTTP header type attackers decide to use:

*   HTTP Header Oversize (HHO)
*   HTTP Meta Character (HMC)
*   HTTP Method Override (HMO)

We won't discuss the technical differences of each attack, since this is out of this article's scope. More details and demos are available [on this website](https://cpdos.org/), or in the researcher's [CPDoS white paper](https://cpdos.org/paper/Your_Cache_Has_Fallen__Cache_Poisoned_Denial_of_Service_Attack__Preprint_.pdf).

### CPDoS attacks deemed practical

During the research into the practicality of CPDoS attacks, the TH Koln team said they managed to carry out widespread cache poisoning attacks against a test website hosted on the network of several CDN providers.

For example, the map below shows an attacker (hazard symbol) launch an attack against a legitimate site's CDN server (blue marker), which then spread the cached error page to other CDN servers (red markers), poisoning a large portion of a CDN provider's network.

![cpdos-map.png](https://www.zdnet.com/article/cpdos-attack-can-poison-cdns-to-deliver-error-pages-instead-of-legitimate-sites/#ftag=RSSbaffb68)

<span><img src="https://zdnet1.cbsistatic.com/hub/i/2019/10/23/69341e4f-de02-43d4-87da-ca03e68f67f7/175e83b2714f3cf43fd06dff3b1e61f8/cpdos-map.png" alt="cpdos-map.png" /></span>

Image: Nguyen et al.

Such atacks as the one portrayed above can create prolonged downtime for legitimate sites, incurring financial losses to the website's owner.

The good news is that not all web servers (HTTP protocol implementations) and CDN networks are vulnerable.

The table below shows which server+CDN combinations are vulnerable, according to the researchers' tests.

![cpdos-table.png](https://www.zdnet.com/article/cpdos-attack-can-poison-cdns-to-deliver-error-pages-instead-of-legitimate-sites/#ftag=RSSbaffb68)

<span><img src="https://zdnet4.cbsistatic.com/hub/i/2019/10/23/dc9d8452-2d9b-4dbc-abf7-2e639b6f812b/f9cdd52f712eafab6373feb831565cd1/cpdos-table.png" alt="cpdos-table.png" /></span>

Image: Nguyen et al.

### Mitigations exist

Mitigations against CPDoS attacks, fortunately, exist. The simplest solution is that website owners configure their CDN service to not cache HTTP error pages by default.

Many CDN service providers include such settings in their dashboards, so this won't be a difficult step to take.

If website owners don't have controls in their CDN web dashboard to disable the caching of error pages, they can disable this from within their server's configuration files by adding the "Cache-Control: no-store" HTTP header to every error page type.

The more complicated solution to deal with CPDoS attacks resides with the CDN providers themselves, which will likely need to modify how their products work.

To explain -- and according to the research team -- the reason that some CDN providers are vulnerable to CPDoS attacks is because they don't follow internet caching protocols.

"The web caching standard only allows \[CDNs\] to cache the error codes _404 Not Found_, _405 Method Not Allowed_, _410 Gone_ and _501 Not Implemented_," the research team said, pointing out that CDNs shouldn't be caching the "400 Bad Request" error pages generated by CPDoS attacks.

"Hence, caching error pages according to the policies of the HTTP standard is the first step to avoid CPDoS attacks," they said.

Taking this approach is more complex and requires some work being done in the backend of many CDN providers. Until then, the first countermeasures are easier to apply.

Since CPDoS attacks are practically possible, with some minimal effort most website owners should be able to secure their servers against any possible abuse.

Researchers warn webmasters not to ignore the issue. According to their tests, 30% ofthe Alexa Top 500 websites, 11% of the Department of Defense domains, and 16% of the URLs from a 365 million URL sample obtained from a Google Big Query archive were potentially vulnerable to CPDoS attacks.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2BwtIWJ