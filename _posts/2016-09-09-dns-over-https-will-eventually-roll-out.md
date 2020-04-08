---
title: 'DNS-over-HTTPS will eventually roll out in all major browsers, despite ISP opposition'
date: 2019-11-08T01:38:00+01:00
draft: false
---

![DoH DNS-over-HTTPS](https://zdnet3.cbsistatic.com/hub/i/2019/10/06/196fd31d-54d9-4e52-a1e2-7e050fdf8f3e/38de2c6dcef89b1a6aad6d440b230b1a/dns-over-https.png)

All six major browser vendors have plans to support DNS-over-HTTPS (or DoH), a protocol that encrypts DNS traffic and helps improve a user's privacy on the web.

The DoH protocol has been one of the year's hot topics. It's a protocol that, when deployed inside a browser, it allows the browser to hide DNS requests and responses inside regular-looking HTTPS traffic.

Doing this makes a user's DNS traffic invisible to third-party network observers, such as ISPs. But while users love DoH and have deemed it a privacy boon, ISPs, networking operators, and cyber-security vendors [hate it](https://www.zdnet.com/article/dns-over-https-causes-more-problems-than-it-solves-experts-say/).

A UK ISP called Mozilla an "[internet villain](https://www.zdnet.com/article/uk-isp-group-names-mozilla-internet-villain-for-supporting-dns-over-https/)" for its plans to roll out DoH, and a Comcast-backed lobby group has been caught [preparing a misleading document about DoH](https://www.vice.com/en_us/article/9kembz/comcast-lobbying-against-doh-dns-over-https-encryption-browsing-data) that they were planning to present to US lawmakers in the hopes of preventing DoH's broader rollout.

However, this may be a little too late. ZDNet has spent the week reaching out to major web browser providers to gauge their future plans regarding DoH, and all vendors plan to ship it, in one form or another.

Below are what we currently know about each browser vendor's plans regarding DoH, and how users could enable DoH in each respective browser.

### Brave

"We absolutely want to implement it," Tom Lowenthal, Product Manager at Brave for Privacy & Security told ZDNet yesterday.

However, the Brave team doesn't yet have an exact timeline for DoH's rollout. This is because Brave developers have been busy with other privacy-focused improvements.

For example, yesterday, the company released an update with [improved detection of user fingerprinting scripts](https://brave.com/brave-fingerprinting-and-privacy-budgets/). Further, the v1.0 stable release is on the horizon, so the Brave team needs to focus on that release first.

Nevertheless, DoH will come to Brave.

"Implementing DoH is far more than just the technical work, though. We need to decide on sensible and protective defaults for the vast majority of people who don't think about their DNS configuration while making sure that we don't break things for the people and organizations who have carefully tuned their setup," Lowenthal said.

Because Brave is built on top of the Chromium open-source browser codebase, DoH support is available. However, the Brave team has not configured the feature to its own liking. It is there in the codebase, but in the way the Google Chrome team designed it to work (see Chrome section below).

You can enable DoH in Brave by visiting the following URL:

**brave://flags/#dns-over-https**

![doh-brave.png](https://www.zdnet.com/article/dns-over-https-will-eventually-roll-out-in-all-major-browsers-despite-isp-opposition/#ftag=RSSbaffb68)

<span><img src="https://zdnet4.cbsistatic.com/hub/i/2019/11/07/dc0c1250-6925-4d2c-b835-d277e03edf17/ff13f1a800e839cf97148b9bda76ae1e/doh-brave.png" alt="doh-brave.png" /></span>

### Chrome

Google Chrome is the second browser after Firefox to have added DoH support. You can enable DoH in Chrome by going to:

**chrome://flags/#dns-over-https**

![doh-chrome.png](https://www.zdnet.com/article/dns-over-https-will-eventually-roll-out-in-all-major-browsers-despite-isp-opposition/#ftag=RSSbaffb68)

<span><img src="https://zdnet3.cbsistatic.com/hub/i/2019/11/08/f61cfaea-23e3-429b-9dca-f4a68e08e6e1/902cae1e2af2b0ab416cab0772701452/doh-chrome.png" alt="doh-chrome.png" /></span>

DoH isn't turned on by default for everyone. Google is currently running a limited experiment with a small number of users to see how DoH fares in a real-world test. Details [here](https://blog.chromium.org/2019/09/experimenting-with-same-provider-dns.html).

Unlike Firefox, which forces all DoH traffic to Cloudflare by default, Chrome's DoH support is different.

After DoH is enabled in Chrome, the browser will send DNS queries to the same DNS servers as before. If the target DNS server has a DoH-capable interface, then Chrome will encrypt DNS traffic and send it to the same DNS server's DoH interface.

This prevents Chrome from hijacking an operating system's DNS settings, a sensible approach in enterprise environments.

Currently, Chrome's DoH support works like this:

\- a user types a website URL in the browser  
\- Chrome looks at the operating system's DNS server  
\- Chrome checks to see if this DNS server is on a whitelist of approved DoH-capable DNS servers  
\- if yes, Chrome sends a DoH (encrytped) DNS query to that DNS server's DoH interface  
\- if not, Chrome sends a regular DNS query to the same server

Because of the way Google implemented DoH support in Chrome, users risk of never being able to use DoH. This is because a user's operating system gets its DNS settings from a central network authority, which is usually the ISP. If the ISP doesn't want to use a DoH-friendly DNS setting, then you're never going to have DoH in Chrome.

The good news is that there are two ways of bypassing this and forcing Chrome to use DoH all the time, regardless of your ISP's DNS settings.

First, there's this tutorial to [forcibly-enable DoH in Chrome](https://www.zdnet.com/article/how-to-enable-dns-over-https-doh-in-google-chrome/). Second, a user can configure a custom DoH-friendly DNS server for their operating system. They can choose one from [this list](https://www.chromium.org/developers/dns-over-https), guaranteed to work in Chrome.

### Edge

Next year, Microsoft plans to roll out a new version of its Edge browser, rebuilt on the Chromium codebase.

A Microsoft spokesperson told ZDNet the company is supportive of DoH, but they couldn't share their exact plans.

However, the Chromium-based version of Edge already supports DoH. Users can enable it by visiting:

**edge://flags/#dns-over-https**

![doh-edge.png](https://www.zdnet.com/article/dns-over-https-will-eventually-roll-out-in-all-major-browsers-despite-isp-opposition/#ftag=RSSbaffb68)

<span><img src="https://zdnet2.cbsistatic.com/hub/i/2019/11/08/a723d483-3146-4cc2-af3c-877148a3d7f5/b10c4c3eedd8a275715ca8c970935465/doh-edge.png" alt="doh-edge.png" /></span>

This will turn on DoH, but it won't work unless your computer is using a DoH-capable DNS server -- which in 99% of cases, they are not.

To forcibly enable DoH in Edge and work at all times, you can follow the steps laid out in the tweet below.

> msedge.exe --enable-features="DnsOverHttpshttps://t.co/pOcecpw0xO%2Fdns-query"
> 
> — Eric Lawrence 🎻 (@ericlaw) [October 25, 2019](https://twitter.com/ericlaw/status/1187747391421722628?ref_src=twsrc%5Etfw)

You can replace the address of the Cloudflare DoH resolver with any other DoH server you want. You can choose one from [here](https://github.com/curl/curl/wiki/DNS-over-HTTPS#publicly-available-servers).

Once configured properly, Edge is capable of running over DoH -- see screenshot below.

![doh-edge-check.png](https://www.zdnet.com/article/dns-over-https-will-eventually-roll-out-in-all-major-browsers-despite-isp-opposition/#ftag=RSSbaffb68)

<span><img src="https://zdnet4.cbsistatic.com/hub/i/2019/11/08/a6ce2d9e-0ce9-4464-b950-489a5d84fac1/c34bd41c8d106515cd011e091d2dde6a/doh-edge-check.png" alt="doh-edge-check.png" /></span>

### Firefox

Mozilla was the organization that pioneered DoH's creation together with Cloudflare. Support for DoH is available in stable versions of Firefox already. You can enable it via the browser's Settings section, in the Networking section. See instructions here.

![DoH section in Firefox settings](https://www.zdnet.com/article/dns-over-https-will-eventually-roll-out-in-all-major-browsers-despite-isp-opposition/#ftag=RSSbaffb68)

<span><img src="https://zdnet3.cbsistatic.com/hub/i/2019/07/07/8608af28-2a28-4ff1-952b-9b6d2deb1ea6/b1fc322caaa2c955b1a2fb285daf0e42/doh-settings-2.png" alt="DoH section in Firefox settings" /></span>

Image: ZDNet

The reason why everyone has and is criticizing Firefox's DoH implementation is that they're using Cloudflare as the default DoH server for everyone, effectively overwriting local DNS settings for everyone.

However, anyone can change this default setting to [any other DoH server they want](https://github.com/curl/curl/wiki/DNS-over-HTTPS#publicly-available-servers). Of all browsers, Firefox's DoH support is the strongest and easiest to configure, primarily because they've been working on it for longer than anyone else.

The organization is currently enabling DoH by default for all users in the US. DoH won't be enabled by default for UK users, following the UK government's pushback against the feature.

In the past, Mozilla was non-commital on its plans to enable DoH by default in other geographical areas outside the US. However, since DoH support is already present in the browser's stable release, all a user has to do is enable it, and it will work without any glitches.

### Opera

Opera has already rolled out DoH support. The feature is turned off for all users but can be enabled at any time in the stable release, and it will work without users going through any additional steps.

This is because Opera devs are using a default DoH resolver, similar to Firefox, and are not leaving it to ISPs, like Chrome. All Opera DoH traffic is currently funneled to Cloudflare's 1.1.1.1 DoH resolver.

We couldn't find a way for users to change the DoH resolver to a custom server, but at least DoH is working in Opera.

It won't work, however, if you're using Opera's built-in VPN system. The VPN feature must be disabled for DoH to work.

To enable DoH in Opera, visit:

**opera://flags/opera-doh**

![doh-opera.png](https://www.zdnet.com/article/dns-over-https-will-eventually-roll-out-in-all-major-browsers-despite-isp-opposition/#ftag=RSSbaffb68)

<span><img src="https://zdnet3.cbsistatic.com/hub/i/2019/11/08/c9ccfffa-c93a-4772-9426-c3f7c1d0aedd/05aadb67d4237dac932e1705a5552209/doh-opera.png" alt="doh-opera.png" /></span>

### Vivaldi

A Vilvadi spokesperson said that its DoH support is closely tied to Chrome's implementation. Users can enable it by visiting:

**vivaldi://flags/#dns-over-https**

However, because DoH in Vivaldi works just like in Chrome, it will not encrypt DNS queries unless a user is using an OS-wide DNS server that also has a DoH interface, and is listed on this page.

Most likely, you'll need to add one of those DoH friendly DNS servers to your operating system's DNS settings if you want to make DoH work in Vivaldi, and use it all the time. We got it working by using 1.1.1.1 as our operating system's DNS settings.

A Vivaldi spokesperson said Vivaldi's DoH support might change in the future, based on how Google changes Chromium's DoH support.

![doh-vivaldi.png](https://www.zdnet.com/article/dns-over-https-will-eventually-roll-out-in-all-major-browsers-despite-isp-opposition/#ftag=RSSbaffb68)

<span><img src="https://zdnet2.cbsistatic.com/hub/i/2019/11/08/2dd69d38-95cd-4d5d-b000-258de20b2b4d/bcefeb33dade9c4c9a50372ec0cf05f1/doh-vivaldi.png" alt="doh-vivaldi.png" /></span>

  
  
from Latest Topic for ZDNet in... https://ift.tt/36KNnjS