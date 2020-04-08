---
title: 'Chrome UI for Deprecating Legacy TLS Versions'
date: 2019-10-01T20:03:00+01:00
draft: false
---

Posted by Chris Thompson, Chrome security team  
_\[Cross-posted from the [Chromium blog](https://blog.chromium.org/2019/10/chrome-ui-for-deprecating-legacy-tls.html?m=1)\]_  
Last October [we announced](https://security.googleblog.com/2018/10/modernizing-transport-security.html) our plans to remove support for TLS 1.0 and 1.1 in Chrome 81. In this post we’re announcing a pre-removal phase in which we’ll introduce a gentler warning UI, and previewing the UI that we’ll use to block TLS 1.0 and 1.1 in Chrome 81. Site administrators should immediately enable TLS 1.2 or later to avoid these UI treatments.  
While legacy TLS usage has decreased, we still see [over 0.5% of page loads](https://chromestatus.com/metrics/feature/timeline/popularity/2634) using these deprecated versions. To ease the transition to the final removal of support and to reduce user surprise when outdated configurations stop working, Chrome will discontinue support in two steps: first, showing new security indicators for sites using these deprecated versions; and second, blocking connections to these sites with a full page warning.  
**Pre-removal warning**  
Starting January 13, 2020, for Chrome 79 and higher, we will show a “Not Secure” indicator for sites using TLS 1.0 or 1.1 to alert users to the outdated configuration:  

[![](https://1.bp.blogspot.com/-jEwM6f5Aefw/XZONAnOOSsI/AAAAAAAAA70/smKkNlbNBocyRmuIbu3zwqivhCO7PlwxQCEwYBhgL/s640/M79-PageInfo.png)](https://1.bp.blogspot.com/-jEwM6f5Aefw/XZONAnOOSsI/AAAAAAAAA70/smKkNlbNBocyRmuIbu3zwqivhCO7PlwxQCEwYBhgL/s1600/M79-PageInfo.png)

_The new security indicator and connection security information that will be shown to users who visit a site using TLS 1.0 or 1.1 starting in January 2020._

When a site uses TLS 1.0 or 1.1, Chrome will downgrade the security indicator and show a more detailed warning message inside Page Info. This change will not block users from visiting or using the page, but will alert them to the downgraded security of the connection.  
Note that Chrome already shows warnings in DevTools to alert site owners that they are using a deprecated version of TLS.  
**Removal UI**  
In Chrome 81, which will be released to the Stable channel in March 2020, we will begin blocking connections to sites using TLS 1.0 or 1.1, showing a full page interstitial warning:  

[![](https://1.bp.blogspot.com/-ulRnRZp-VL0/XZOMvenbFGI/AAAAAAAAA7s/JTK4ZYskNpYHGzQiM2Q3pxjsDucNCzZ4ACEwYBhgL/s640/M81-Interstitial.png)](https://1.bp.blogspot.com/-ulRnRZp-VL0/XZOMvenbFGI/AAAAAAAAA7s/JTK4ZYskNpYHGzQiM2Q3pxjsDucNCzZ4ACEwYBhgL/s1600/M81-Interstitial.png)

_The full screen interstitial warning that will be shown to users who visit a site using TLS 1.0 or 1.1 starting in Chrome 81. Final warning subject to change._

Site administrators should immediately enable TLS 1.2 or later. Depending on server software (such as Apache or nginx), this may be a configuration change or a software update. Additionally, we encourage all sites to revisit their TLS configuration. In [our original announcement](https://security.googleblog.com/2018/10/modernizing-transport-security.html), we outlined our current criteria for modern TLS.  
Enterprise deployments can preview the final removal of TLS 1.0 and 1.1 by setting the SSLVersionMin policy to “tls1.2”. This will prevent clients from connecting over these protocol versions. For enterprise deployments that need more time, this same policy can be used to re-enable TLS 1.0 or TLS 1.1 and disable the warning UIs until January 2021.

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=6xWl6RtenvQ:2YAN-Ca3we8:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=6xWl6RtenvQ:2YAN-Ca3we8:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=6xWl6RtenvQ:2YAN-Ca3we8:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/6xWl6RtenvQ)  
  
from Google Online Security Blog https://ift.tt/2nAIcBg  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)