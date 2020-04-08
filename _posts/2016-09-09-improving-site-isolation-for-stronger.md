---
title: 'Improving Site Isolation for Stronger Browser Security'
date: 2019-10-17T17:12:00+01:00
draft: false
---

Posted by Charlie Reis, Site Isolator

The Chrome Security team values having multiple lines of defense. Web browsers are complex, and malicious web pages may try to find and exploit browser bugs to steal data. Additional lines of defense, like [sandboxes](https://blog.chromium.org/2008/10/new-approach-to-browser-security-google.html), make it harder for attackers to access your computer, even if bugs in the browser are exploited. With [Site Isolation](https://www.chromium.org/Home/chromium-security/site-isolation), Chrome has gained a new line of defense that helps protect your accounts on the Web as well.

Site Isolation ensures that pages from different sites end up in different sandboxed processes in the browser. Chrome can thus limit the entire process to accessing data from only one site, making it harder for an attacker to steal cross-site data. We started isolating all sites [for desktop users back in Chrome 67](https://security.googleblog.com/2018/07/mitigating-spectre-with-site-isolation.html), and now we’re excited to enable it on Android for sites that users log into [in Chrome 77](https://blog.chromium.org/2019/10/recent-site-isolation-improvements.html). We've also strengthened Site Isolation on desktop to help defend against even fully compromised processes.

Site Isolation helps defend against two types of threats. First, attackers may try to use advanced "side channel" attacks to leak sensitive data from a process through unexpected means. For example, [Spectre](https://security.googleblog.com/2018/07/mitigating-spectre-with-site-isolation.html) attacks take advantage of CPU performance features to access data that should be off limits. With Site Isolation, it is harder for the attacker to get cross-site data into their process in the first place.

Second, even more powerful attackers may discover security bugs in the browser, allowing them to completely hijack the sandboxed process. On desktop platforms, Site Isolation can now catch these misbehaving processes and limit their access to cross-site data. We're working to bring this level of hijacked process protection to Android in the future as well.

Thanks to this extra line of defense, Chrome can now help keep your web accounts even more secure. We are still making improvements to get the full benefits of Site Isolation, but this change gives Chrome a solid foundation for protecting your data.

If you’d like to learn more, check out our [technical write up](https://blog.chromium.org/2019/10/recent-site-isolation-improvements.html) on the Chromium blog.

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=KcbSi0IOYs0:OXGT3OH33iw:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=KcbSi0IOYs0:OXGT3OH33iw:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=KcbSi0IOYs0:OXGT3OH33iw:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/KcbSi0IOYs0)  
  
from Google Online Security Blog https://ift.tt/2VRNN3a  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)