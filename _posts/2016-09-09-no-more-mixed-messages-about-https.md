---
title: 'No More Mixed Messages About HTTPS'
date: 2019-10-03T17:21:00+01:00
draft: false
---

Posted by Emily Stark and Carlos Joan Rafael Ibarra Lopez, Chrome security team  
Today we’re announcing that Chrome will gradually start ensuring that https:// pages can only load secure https:// subresources. In a series of steps outlined below, we’ll start blocking [mixed content](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content) (insecure http:// subresources on https:// pages) by default. This change will improve user privacy and security on the web, and present a clearer browser security UX to users.  
In the past several years, the web has made great [progress](https://transparencyreport.google.com/https/overview?hl=en) in transitioning to HTTPS: Chrome users now spend over 90% of their browsing time on HTTPS on all major platforms. We’re now turning our attention to making sure that HTTPS configurations across the web are secure and up-to-date.  
HTTPS pages commonly suffer from a problem called mixed content, where subresources on the page are loaded insecurely over http://. Browsers block many types of mixed content by default, like scripts and iframes, but images, audio, and video are still allowed to load, which threatens users’ privacy and security. For example, an attacker could tamper with a mixed image of a stock chart to mislead investors, or inject a tracking cookie into a mixed resource load. Loading mixed content also leads to a confusing browser security UX, where the page is presented as neither secure nor insecure but somewhere in between.  
In a series of steps starting in Chrome 79, **Chrome will gradually move to blocking all mixed content by default**. To minimize breakage, we will autoupgrade mixed resources to https://, so sites will continue to work if their subresources are already available over https://. Users will be able to enable a setting to opt out of mixed content blocking on particular websites, and below we’ll describe the resources available to developers to help them find and fix mixed content.  
**Timeline**  
Instead of blocking all mixed content all at once, we’ll be rolling out this change in a series of steps.  

*   In **Chrome 79**, releasing to stable channel in December 2019, we’ll introduce a new setting to unblock mixed content on specific sites. This setting will apply to mixed scripts, iframes, and other types of content that Chrome currently blocks by default. Users can toggle this setting by clicking the lock icon on any https:// page and clicking Site Settings. This will replace the shield icon that shows up at the right side of the omnibox for unblocking mixed content in previous versions of desktop Chrome.

![](https://lh3.googleusercontent.com/7QBYFZr2x_in7tqRuOejwicVglv56SQDmEahs804FytS_dut5VwY3JeaPhqaOIgkVxeO0hc6SLbICZQ9DjQAEvP3X1wVjMWLPgJ4-yyfaqmuUnZsLHmxd0F8sYZKMhLabsAFd9dI)

  

  

_Accessing Site settings, from which users will be able to unblock mixed content loads in Chrome 79._

*   In **Chrome 80**, mixed audio and video resources will be autoupgraded to https://, and Chrome will block them by default if they fail to load over https://. Chrome 80 will be released to early release channels in January 2020. Users can unblock affected audio and video resources with the setting described above.
*   Also in **Chrome 80**, mixed images will still be allowed to load, but they will cause Chrome to show a “Not Secure” chip in the omnibox. We anticipate that this is a clearer security UI for users and that it will motivate websites to migrate their images to HTTPS. Developers can use the [upgrade-insecure-requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Upgrade-Insecure-Requests) or [block-all-mixed-content](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/block-all-mixed-content) Content Security Policy directives to avoid this warning. 

  

![](https://lh5.googleusercontent.com/jvfl8cszpNDLQxRMfz52dVZXE9uBE6UtxdEWrwz6yfbLrW9ELHZuZOP0Xyq8lhV7-yIR6TA0WY99oI6TroZ6i6VT-MJy1dsBFGfviF3hPu1uQDx9LtxmLcSrre0sjiZ0fWTTMkuc)

__Omnibox treatment for websites that load mixed images in Chrome 80._ _

  

*   In **Chrome 81**, mixed images will be autoupgraded to https://, and Chrome will block them by default if they fail to load over https://. Chrome 81 will be released to early release channels in February 2020.

**Resources for developers**  
Developers should migrate their mixed content to https:// immediately to avoid warnings and breakage. Here are some resources:  

*   Use [Content Security Policy](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/fixing-mixed-content) and [Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/mixed-content)’s mixed content audit to discover and fix mixed content on your site.
*   See [this guide](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/enable-https) for general advice on migrating servers to HTTPS.
*   Check with your CDN, web host, or content management system to see if they have special tools for debugging mixed content. For example, Cloudflare offers a [tool](https://support.cloudflare.com/hc/en-us/articles/227227647) to rewrite mixed content to https://, and WordPress [plugins](https://en-gb.wordpress.org/plugins/ssl-insecure-content-fixer/) are available as well.

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=1yPqmvclA5w:_8NZTWygurA:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=1yPqmvclA5w:_8NZTWygurA:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=1yPqmvclA5w:_8NZTWygurA:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/1yPqmvclA5w)  
  
from Google Online Security Blog https://ift.tt/2M8ollu  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)