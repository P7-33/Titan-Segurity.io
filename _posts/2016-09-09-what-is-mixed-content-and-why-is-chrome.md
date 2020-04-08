---
title: 'What Is “Mixed Content,” and Why Is Chrome Blocking It?'
date: 2019-10-04T11:43:00+01:00
draft: false
---

![A Google Chrome logo with a lock icon inside it.](https://www.howtogeek.com/wp-content/uploads/2019/10/img_5d968044e8a3a.png)

Google Chrome already blocks some types of “mixed content” on the web. Now, Google [announced](https://blog.chromium.org/2019/10/no-more-mixed-messages-about-https.html) it’s getting even more serious: Starting in early 2020, Chrome will block all mixed content by default, breaking some existing web pages. Here’s what that means.

What Is Mixed Content?
----------------------

There are two types of content here: Content delivered over a [secure, encrypted HTTPS connection](https://www.howtogeek.com/181767/htg-explains-what-is-https-and-why-should-i-care/), and content delivered over an unencrypted HTTP connection. When you use HTTPS, content can’t be snooped on or tampered with in transit, which is why it’s critical websites offer encryption when dealing with financial information or private data.

The web is moving to secure HTTPS websites. If you connect to an older HTTP website without encryption, [Google Chrome now warns you these websites are “not secure.”](https://www.howtogeek.com/359298/why-does-google-chrome-say-websites-are-%E2%80%9Cnot-secure%E2%80%9D/) Google now even [hides the “https://” indicator by default](https://www.howtogeek.com/435728/chrome-now-hides-www-and-https-in-addresses.-do-you-care/), as sites should just be secure by default. And [the new HTTP/3 standard](https://www.howtogeek.com/442047/how-http3-and-quic-will-speed-up-your-web-browsing/) will have built-in encryption.

But some web pages can be neither entirely HTTPS nor completely HTTP. Some web pages are delivered over a secure HTTPS connection, but they pull in images, scripts, or other resources via an unencrypted HTTP connection. Such web pages have “mixed content” because they’re not fully secure. The web page itself couldn’t be tampered with, but it may pull in a script, image, or iframe (a web page inside a “frame” on another web page) that could have been tampered with.

Why Mixed Content Is Bad
------------------------

![Chrome warning of mixed content images.](https://www.howtogeek.com/wp-content/uploads/2019/10/img_5d967e79c9af6.png)

Mixed content is confusing. You’re somehow viewing a web page that’s both secure and not secure. For example, a usually safe and secure web page could pull in a JavaScript file via HTTP. That script could be modified—for instance, if you’re on a public Wi-Fi network that isn’t trustworthy—to do many nasty things on the web page, from monitoring your keystrokes to inserting a tracking cookie.

While scripts and iframes—“active content”— are the most dangerous, even images, videos, and audio-mixed content could be risky. For example, imagine you’re viewing a secure stock trading website that pulls in an image of a stock’s history via HTTP. That image isn’t secure—it could have been tampered with in transit to show incorrect details. Also, because it was delivered over an unencrypted connection, anyone [snooping on the data in transit](https://www.howtogeek.com/219384/how-to-avoid-snooping-on-hotel-wi-fi-and-other-public-networks/) likely knows what stock you’re looking at.

It’s a bad idea to mix content like this. If a web page is using HTTPS, all its resources should be pulled in via HTTPS as well. It’s just a historical accident—the web started with HTTP, and websites gradually upgraded to HTTPS. As they did, they didn’t always update to use HTTPS resources everywhere. Or, they may have depended on a third-party resource that didn’t support HTTPS at the time.

### [Read the remaining 16 paragraphs](https://www.howtogeek.com/443032/what-is-mixed-content-and-why-is-chrome-blocking-it/)