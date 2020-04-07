---
title: 'Ring doorbell app packed with third-party trackers'
date: 2020-01-28T05:12:00+01:00
draft: false
---

\[My EFF colleague Bill Buddington has a fantastic report on all the ways that Ring surveils its own customers. Caveat emptor, indeed. -Cory\]

Ring isn't just a product that allows users to surveil their neighbors. The company also uses it to surveil its customers.  

An investigation by EFF of the Ring doorbell app for Android found it to be packed with third-party trackers sending out a plethora of customers’ personally identifiable information (PII). Four main analytics and marketing companies were discovered to be receiving information such as the names, private IP addresses, mobile network carriers, persistent identifiers, and sensor data on the devices of paying customers.

The danger in sending even small bits of information is that analytics and tracking companies are able to [combine](https://www.eff.org/deeplinks/2010/01/primer-information-theory-and-privacy) these bits together to form a unique picture of the user’s device. This cohesive whole represents a fingerprint that follows the user as they interact with other apps and use their device, in essence providing trackers the ability to spy on what a user is doing in their digital lives and when they are doing it. All this takes place without meaningful user notification or consent and, in most cases, no way to mitigate the damage done. Even when this information is not misused and employed for precisely its stated purpose (in most cases marketing), this can lead to a whole host of [social ills](https://books.google.com/books?id=CxD-DAAAQBAJ&pg=PA69&lpg=PA69&dq=diploma+mills+cathy+oneil&source=bl&ots=WS_NCqpO_5&sig=ACfU3U268CNM3c_vxkK8_RZAHGaTJmkB6A&hl=en&ppis=_e&sa=X&ved=2ahUKEwj4rrjRtZnnAhUoHDQIHQfYDIMQ6AEwAXoECAoQAQ#v=onepage&q=diploma%20mills%20cathy%20oneil&f=false).

Ring has exhibited a pattern of behavior that attempts to [mitigate exposure](https://www.eff.org/deeplinks/2019/12/ring-throws-customers-under-bus-after-data-breach) to criticism and scrutiny while benefiting from the wide array of customer data available to them. It has been able to do so by leveraging an image of the secure home, while profiting from a surveillance network which facilitates police departments’ unprecedented access into the private lives of citizens, [as we have previously covered](https://www.eff.org/deeplinks/2019/08/amazons-ring-perfect-storm-privacy-threats). For consumers, this image has cultivated a sense of trust in Ring that should be shaken by the reality of how the app functions: not only does Ring mismanage consumer data, but it also intentionally hands over that data to trackers and data miners.

**Findings**

Our testing, using [Ring for Android](https://play.google.com/store/apps/details?id=com.ringapp) version 3.21.1, revealed PII delivery to `branch.io`, `mixpanel.com`, `appsflyer.com` and `facebook.com`. Facebook, via its [Graph API](https://developers.facebook.com/docs/graph-api/), is alerted when the app is opened and upon device actions such as app deactivation after screen lock due to inactivity. Information delivered to Facebook (even if you don’t have a Facebook account) includes time zone, device model, language preferences, screen resolution, and a unique identifier (`anon_id`), which persists even when you reset the OS-level advertiser ID.

Branch, which describes itself as a “deep linking” platform, receives a number of unique identifiers (`device_fingerprint_id`, `hardware_id`, `identity_id`) as well as your device’s local IP address, model, screen resolution, and DPI.

[AppsFlyer](https://en.wikipedia.org/wiki/AppsFlyer), a big data company focused on the mobile platform, is given a wide array of information upon app launch as well as certain user actions, such as interacting with the “Neighbors” section of the app. This information includes your mobile carrier, when Ring was installed and first launched, a number of unique identifiers, the app you installed from, and whether AppsFlyer tracking came preinstalled on the device. This last bit of information is presumably to determine whether AppsFlyer tracking was included as bloatware on a low-end Android device. Manufacturers often offset the costs of device production by selling consumer data, a practice that disproportionately affects low-income earners and was the subject of a recent [petition to Google](https://action.privacyinternational.org/node/9) initiated by Privacy International and co-signed by EFF.

Most alarmingly, AppsFlyer also receives the sensors installed on your device (on our test device, this included the magnetometer, gyroscope, and accelerometer) and current calibration settings.

Ring gives [MixPanel](https://en.wikipedia.org/wiki/Mixpanel) the most information by far. Users’ full names, email addresses, device information such as OS version and model, whether bluetooth is enabled, and app settings such as the number of locations a user has Ring devices installed in, are all collected and reported to MixPanel. MixPanel is briefly mentioned in Ring’s [list of third party services](https://ring.com/third-party-services), but the extent of their data collection is not. None of the other trackers listed in this post are mentioned at all on this page.

Ring also sends information to the Google-owned crash logging service [Crashalytics](https://en.wikipedia.org/wiki/Crashlytics). The exact extent of data sharing with this service is yet to be determined.

![](/files/2020/01/27/api.branch.io_.png)

Data delivered to `api.branch.io`

![](/files/2020/01/27/api.mixpanel.com_.png)

Data delivered to `api.mixpanel.com`

![](/files/2020/01/27/graph.facebook.com_.png)

Data delivered to `graph.facebook.com`

![](/files/2020/01/27/t.appsflyer.com_.png)

Data delivered to `t.appsflyer.com`

**Methodology**

All traffic we observed on the app was being sent using encrypted HTTPS. What’s more, the encrypted information was delivered in a way that eludes analysis, making it more difficult (but not impossible) for security researchers to learn of and report these serious privacy breaches.

Our dynamic analysis was performed using `[mitmproxy](https://mitmproxy.org/)` running on an access point to intercept and analyze HTTPS flows from an Android test device. To remove noise generated from other apps, we installed the AFWall+ firewall app and only allowed network traffic from Ring. `mitmproxy` generates a root x509 certificate which is to be installed in the OS-level certificate store in Android, allowing active interception to take place on otherwise secured traffic. This led us to the initial discovery that the root certificate was not being accepted as valid, and that some form of certificate pinning was being employed by the app.

App-level certificate pinning is when an app validates the certificates of a remote server against a record of that certificate stored within the app, rather than validating against the list of root certificates within the OS. This is often used as a security measure, to ensure that [misissuance](https://jhalderm.com/pub/papers/misissuance-sp18.pdf) of certificates or mismanagement along the chain of trust in PKI does not compromise the integrity, confidentiality, or authenticity of HTTPS traffic. Unfortunately, it can  also prevent security researchers and users from seeing exactly what information these devices are sending, and to whom. In the case of Ring, we initially observed all intercepted traffic upon launch being rejected, and were not able to observe any communications.

![](/files/2020/01/27/pinning.png)

`mitmproxy` screen displaying results of certificate pinning

It was only through the powerful dynamic analysis framework [Frida](https://frida.re/) that we were able to inject code into Ring at runtime, which ensured that the certificate provided by our `mitmproxy` instance would be accepted as valid. This allowed us to inspect all HTTPS traffic sent through the app.

**Conclusion**

Ring claims to prioritize the security and privacy of its customers, yet time and again we’ve seen these claims not only fall short, but harm the customers and community members who engage with Ring’s surveillance system. In the past, we’ve [illuminated the mismanagement](https://www.eff.org/deeplinks/2019/12/ring-throws-customers-under-bus-after-data-breach) of user information which has led to data breaches, and the attempt to place the blame for such blunders at the customers’ feet.

This goes a step beyond that, by simply delivering sensitive data to third parties not accountable to Ring or bound by the trust placed in the customer-vendor relationship. As we’ve mentioned, this includes information about your device and carrier, unique identifiers that allow these companies to track you across apps, real-time interaction data with the app, and information about your home network. In the case of MixPanel, it even includes your name and email address. This data is given to parties either only mentioned briefly, buried on an internal page users are unlikely to ever see, or not listed at all.

`mitmproxy` flow files:

  
  
from Hacker News https://ift.tt/2RXOeHg