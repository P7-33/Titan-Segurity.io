---
title: 'Get Ready for New SameSite=None; Secure Cookie Settings'
date: 2020-01-16T15:58:00+01:00
draft: false
---

_This is a cross-post from the [Chromium developer blog](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html) and is specific to how changes to Chrome may affect how your website works for your users in the future._  
  
In May, Chrome [announced](https://blog.chromium.org/2019/05/improving-privacy-and-security-on-web.html) a secure-by-default model for cookies, enabled by a new cookie classification system ([spec](https://tools.ietf.org/html/draft-west-cookie-incrementalism-00)). This initiative is part of our [ongoing effort](https://www.blog.google/products/chrome/building-a-more-private-web/) to improve privacy and security across the web.  
Chrome plans to implement the new model with Chrome 80 in February 2020. Mozilla and Microsoft have also indicated intent to implement the new model in Firefox and Edge, on their own timelines. While the Chrome changes are still a few months away, It’s important that developers who manage cookies assess their readiness today. This blog post outlines high level concepts; please see [SameSite Cookies Explained](https://web.dev/samesite-cookies-explained) on web.dev for developer guidance.  
  

### Understanding Cross-Site and Same-Site Cookie Context

  
Websites typically integrate external services for advertising, content recommendations, third party widgets, social embeds and other features. As you browse the web, these external services may store cookies in your browser and subsequently access those cookies to deliver personalized experiences or measure audience engagement. Every cookie has a domain associated with it. If the domain associated with a cookie matches an external service and not the website in the user’s address bar, this is considered a **cross-site** (or **“third party”**) context.  
  
Less obvious cross-site use cases include situations where an entity that owns multiple websites uses a cookie across those properties. Although the same entity owns the cookie and the websites, this still counts as cross-site or “third party” context when the cookie’s domain does not match the site(s) from which the cookie is accessed. ![](https://lh4.googleusercontent.com/K0TdWPVcr8pium5MnY2PMeFZj9rkqpY4Z_U9Z_C9yllN_GO2STNRWrwBmZNuXQ4ILocG5si0tmFZAk4QeIE2DyqRQ_8hRt2GZSZGflsw_YfMuyeu0Y6D4qtiUy3HVCYQKX6zlZ6G)  
_When an external resource on a web page accesses a cookie that does not match the site domain, this is cross-site or “third-party” context._  
  
In contrast, cookie access in a **same-site** (or **“first party”**) context occurs when a cookie’s domain matches the website domain in the user’s address bar. Same-site cookies are commonly used to keep people logged into individual websites, remember their preferences and support site analytics.  
  
![](https://lh3.googleusercontent.com/AgtxHofbBpva_NgsyGLvLko9J6ZFgWBDk3zqFXz37zWCuokA0xfCciKug5A3-ze7FGlorSWfVoPnwiWC7ydHjkqePG4g09SNQE37eXZfj3oz7buWcTrUMgF6QvdDX__9ks3HJap_)  
_When a resource on a web page accesses a cookie that matches the site the user is visiting, this is same-site or “first party” context._  
  

### A New Model for Cookie Security and Transparency

  
Today, if a cookie is only intended to be accessed in a first party context, the developer has the option to apply one of two settings (SameSite=Lax or SameSite=Strict) to prevent external access. However, very few developers follow this recommended practice, leaving a large number of same-site cookies needlessly exposed to threats such as [Cross-Site Request Forgery](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html) attacks.  
  
To safeguard more websites and their users, the new secure-by-default model assumes all cookies should be protected from external access unless otherwise specified. Developers must use a new cookie setting, SameSite=None, to designate cookies for cross-site access. When the SameSite=None attribute is present, an additional Secure attribute must be used so cross-site cookies can only be accessed over HTTPS connections. This won’t mitigate all risks associated with cross-site access but it will provide protection against network attacks.  
  
Beyond the immediate security benefits, the explicit declaration of cross-site cookies enables greater transparency and user choice. For example, browsers could offer users fine-grained controls to manage cookies that are only accessed by a single site separately from cookies accessed across multiple sites.  
  

### Chrome Enforcement Starting in February 2020

  
With Chrome 80 in February, Chrome will treat cookies that have no declared SameSite value as SameSite=Lax cookies. Only cookies with the SameSite=None; Secure setting will be available for external access, provided they are being accessed from secure connections. The Chrome Platform Status trackers for [SameSite=None](https://chromestatus.com/feature/5088147346030592) and [Secure](https://chromestatus.com/feature/5633521622188032) will continue to be updated with the latest launch information.  
  
Mozilla has affirmed their support of the new cookie classification model with their [intent to implement](https://groups.google.com/forum/#!msg/mozilla.dev.platform/nx2uP0CzA9k/BNVPWDHsAQAJ) the SameSite=None; Secure requirements for cross-site cookies in Firefox. Microsoft recently [announced](https://groups.google.com/a/chromium.org/forum/#!msg/blink-dev/AknSSyQTGYs/8lMmI5DwEAAJ) plans to begin implementing the model starting as an experiment in Microsoft Edge 80.  
  

### How to Prepare; Known Complexities

  
If you manage cross-site cookies, you will need to apply the SameSite=None; Secure setting to those cookies. Implementation should be straightforward for most developers, but we strongly encourage you to begin testing now to identify complexities and special cases, such as the following:  
  

*   Not all languages and libraries support the None value yet, requiring developers to set the cookie header directly. This [Github repository](https://github.com/GoogleChromeLabs/samesite-examples) provides instructions for implementing SameSite=None; Secure in a variety of languages, libraries and frameworks.
*   Some browsers, including some versions of Chrome, Safari and UC Browser, might handle the  None value in unintended ways, requiring developers to code exceptions for those clients. This includes Android WebViews powered by older versions of Chrome. Here’s a list of known [incompatible clients](https://www.chromium.org/updates/same-site/incompatible-clients).
*   App developers are advised to declare the appropriate SameSite cookie settings for Android WebViews based on versions of Chrome that are compatible with the  None value, both for cookies accessed via HTTP(S) headers and via Android WebView's [CookieManager API](https://developer.android.com/reference/android/webkit/CookieManager), although the new model will not be enforced on Android WebView until later.
*   Enterprise IT administrators may need to implement [special policies](https://www.chromium.org/administrators/policy-list-3/cookie-legacy-samesite-policies) to temporarily revert Chrome Browser to legacy behavior if some services such as single sign-on or internal applications are not ready for the February launch.
*   If you have cookies that you access in both a first and third-party context, you might consider using separate cookies to get the security benefits of SameSite=Lax in the first-party context.

[SameSite Cookies Explained](https://web.dev/samesite-cookies-explained) offers specific guidance for the situations above, and channels for raising issues and questions.  
  
To test the effect of the new Chrome behavior on your site or cookies you manage, you can go to chrome://flags in Chrome 76+ and enable the “SameSite by default cookies” and “Cookies without SameSite must be secure” experiments. In addition, these experiments will be automatically enabled for a subset of Chrome 79 Beta users. Some Beta users with the experiments enabled could experience incompatibility issues with services that do not yet support the new model; users can opt out of the Beta experiments by going to chrome://flags and disabling them.  
  
If you manage cookies that are only accessed in a same-site context (same-site cookies) there is no required action on your part; Chrome will automatically prevent those cookies from being accessed by external entities, even if the SameSite attribute is missing or no value is set. However we strongly recommend you apply an appropriate SameSite value (Lax or Strict) and not rely on default browser behavior since not all browsers protect same-site cookies by default.  
  
Finally, if you’re concerned about the readiness of vendors and others who provide services to your website, you can check for Developer Tools console warnings in Chrome 77+ when a page contains cross-site cookies that are missing the required settings:  
  
![A cookie associated with a cross-site resource at (cookie domain) was set without the `SameSite` attribute. A future release of Chrome will only deliver cookies with cross-site requests if they are set with `SameSite=None` and `Secure`. You can review cookies in developer tools under Application Storage Cookies and see more details at https://www.chromestatus.com/feature/5088147346030592 and https://www.chromestatus.com/feature/5633521622188032.](https://lh6.googleusercontent.com/AMjvE6tOlDJ8omG83qcir_OWvHdXTPM2PTFa_AVZa_2fbqBA85of3rU4-_d83Nm6m7W6ojc1gCGJkwsY3KljB2hHeCrcJH4H3G1ThES7wsceY34BrGF8a-srV0lKbsIjZBoi_Sl8)  
Some providers (including some Google services) will implement the necessary changes in the months leading up to Chrome 80 in February; you may wish to reach out to your partners to confirm their readiness.  
Posted by Barb Palser, Chrome and Web Platform Partnerships