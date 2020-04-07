---
title: 'Protecting users from insecure downloads in Google Chrome'
date: 2020-02-06T19:42:00+01:00
draft: false
---

Posted by Joe DeBlasio, Chrome security team  
Today we’re announcing that Chrome will gradually ensure that secure (HTTPS) pages only download secure files. In a series of steps outlined below, we’ll start blocking "mixed content downloads" (non-HTTPS downloads started on secure pages). This move follows a [plan we announced last year](https://blog.chromium.org/2019/10/no-more-mixed-messages-about-https.html) to start blocking all insecure subresources on secure pages.  
Insecurely-downloaded files are a risk to users' security and privacy. For instance, insecurely-downloaded programs can be swapped out for malware by attackers, and eavesdroppers can read users' insecurely-downloaded bank statements. To address these risks, we plan to eventually remove support for insecure downloads in Chrome.  
As a first step, we are focusing on insecure downloads started on secure pages. These cases are especially concerning because Chrome currently gives no indication to the user that their privacy and security are at risk.  
Starting in Chrome 82 (to be released April 2020), Chrome will gradually start warning on, and later blocking, these mixed content downloads. File types that pose the most risk to users (e.g., executables) will be impacted first, with subsequent releases covering more file types. This gradual rollout is designed to mitigate the worst risks quickly, provide developers an opportunity to update sites, and minimize how many warnings Chrome users have to see.  
We plan to roll out restrictions on mixed content downloads on desktop platforms (Windows, macOS, Chrome OS and Linux) first. Our plan for desktop platforms is as follows:  

[![](https://4.bp.blogspot.com/-uc2I5k26oGg/XjtFJgTu7mI/AAAAAAAABs0/X0mfxT5mWEoga8htBqBXpUDwQZO-7xK9gCNcBGAsYHQ/s1600/mix_dl_table.png)](https://4.bp.blogspot.com/-uc2I5k26oGg/XjtFJgTu7mI/AAAAAAAABs0/X0mfxT5mWEoga8htBqBXpUDwQZO-7xK9gCNcBGAsYHQ/s1600/mix_dl_table.png)

  

*   In Chrome 81 (released March 2020) and later:
    *   Chrome will print a **console message** warning about all mixed content downloads.
*   In Chrome 82 (released April 2020):
    *   Chrome will **warn** on mixed content downloads of **executables** (e.g. .exe).
*   In Chrome 83 (released June 2020):
    *   Chrome will **block** mixed content **executables**
    *   Chrome will **warn** on mixed content **archives** (.zip) and **disk images** (.iso).
*   In Chrome 84 (released August 2020):
    *   Chrome will **block** mixed content **executables, archives and disk images**
    *   Chrome will **warn on all other mixed content downloads** except image, audio, video and text formats.
*   In Chrome 85 (released September 2020):
    *   Chrome will **warn** on mixed content downloads of **images, audio, video, and text**
    *   Chrome will **block all other mixed content downloads**
*   In Chrome 86 (released October 2020) and beyond, Chrome will block all mixed content downloads.

![](https://lh6.googleusercontent.com/7VoXAcrd9RpJ0mMeP26IilFMeepkst8sF8EAohoKCfA0Rqbrh7N8_VSXhMmsb2MNZyD2sNEBWzDJ43aDpyFuAHmAV6TPgSXErAp9huOfUmv4Tz19mfoWGImTe6XfOzobf6JD1LdJ)

_Example of a potential warning_

Chrome will delay the rollout for Android and iOS users by one release, starting warnings in Chrome 83. Mobile platforms have better native protection against malicious files, and this delay will give developers a head-start towards updating their sites before impacting mobile users.  
Developers can prevent users from ever seeing a download warning by ensuring that downloads only use HTTPS. In the current version of Chrome Canary, or in Chrome 81 once released, developers can activate a warning on all mixed content downloads for testing by enabling the "Treat risky downloads over insecure connections as active mixed content" flag at `chrome://flags/#treat-unsafe-downloads-as-active-content`.  
Enterprise and education customers can disable blocking on a per-site basis via the existing `InsecureContentAllowedForUrls` policy by adding a pattern matching the page requesting the download.  
In the future, we expect to further restrict insecure downloads in Chrome. We encourage developers to fully migrate to HTTPS to avoid future restrictions and fully protect their users. Developers with questions are welcome to email us at [security-dev@chromium.org](mailto:security-dev@chromium.org).

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=SRlfhfZ0GC4:GtjrHOselpo:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=SRlfhfZ0GC4:GtjrHOselpo:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=SRlfhfZ0GC4:GtjrHOselpo:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/SRlfhfZ0GC4)  
  
from Google Online Security Blog https://ift.tt/3bhvc7W  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)