---
title: 'Say hello to OpenSK: a fully open-source security key implementation'
date: 2020-01-30T18:11:00+01:00
draft: false
---

Posted by Elie Bursztein, Security & Anti-abuse Research Lead, and Jean-Michel Picod, Software Engineer, Google   
  

  
Today, [FIDO](https://fidoalliance.org/how-fido-works/) security keys are reshaping the way online accounts are protected by providing an easy, phishing-resistant form of two-factor authentication (2FA) that is trusted by a growing number of websites, including Google, social networks, cloud providers, and many others. To help advance and improve access to FIDO authenticator implementations, we are excited, following other open-source projects like Solo and Somu, to announce the release of [OpenSK](https://github.com/google/OpenSK), an open-source implementation for security keys written in [Rust](https://www.rust-lang.org/) that supports both FIDO U2F and FIDO2 standards.  

  

[![](https://1.bp.blogspot.com/-jQvZmprkkOU/XjL4iBkvbgI/AAAAAAAABgo/khrdiLFzrCw7hCv23OcIuxHxD6RQZZwDwCNcBGAsYHQ/s400/unnamed.jpg)](https://1.bp.blogspot.com/-jQvZmprkkOU/XjL4iBkvbgI/AAAAAAAABgo/khrdiLFzrCw7hCv23OcIuxHxD6RQZZwDwCNcBGAsYHQ/s1600/unnamed.jpg)

**Photo of OpenSK developer edition: a Nordic Dongle running the OpenSK firmware on DIY case**

  

By opening up OpenSK as a research platform, our hope is that it will be used by researchers, security key manufacturers, and enthusiasts to help develop innovative features and accelerate security key adoption.  
  
With this early release of OpenSK, you can make your own developer key by flashing the OpenSK firmware on a [Nordic chip dongle](https://www.nordicsemi.com/About-us/BuyOnline?search_token=nRF52840%20Dongle&series_token=nRF52840). In addition to being affordable, we chose Nordic as initial reference hardware because it supports all major transport protocols mentioned by [FIDO2](https://fidoalliance.org/specs/fido-v2.0-ps-20190130/fido-client-to-authenticator-protocol-v2.0-ps-20190130.html#transport-specific-bindings): NFC, Bluetooth Low Energy, USB, and a dedicated hardware crypto core. To protect and carry your key, we are also providing a [custom, 3D-printable case](https://www.thingiverse.com/thing:4132768) that works on a variety of printers.  
  
“We’re excited to collaborate with Google and the open source community on the new OpenSK research platform,” said Kjetil Holstad, Director of Product Management at Nordic Semiconductor. “We hope that our industry leading nRF52840’s native support for secure cryptographic acceleration combined with new features and testing in OpenSK will help the industry gain mainstream adoption of security keys.”  

  

While you can make your own fully functional FIDO authenticator today, as showcased in the video above, this release should be considered as an experimental research project to be used for testing and research purposes.

  
  
Under the hood, OpenSK is written in [Rust](https://www.rust-lang.org/) and runs on [TockOS](https://www.tockos.org/) to provide better isolation and cleaner OS abstractions in support of security. Rust’s strong memory safety and zero-cost abstractions makes the code less vulnerable to logical attacks. [TockOS, with its sandboxed architecture](https://www.tockos.org/documentation/design), offers the isolation between the security key applet, the drivers, and kernel that is needed to build defense-in-depth. Our TockOS contributions, including our [flash-friendly storage system](https://github.com/tock/tock/pull/1467) and [patches](https://github.com/tock/tock/pulls?q=is%3Apr+author%3Agendx), have all been upstreamed to the TockOS repository. We’ve done this to encourage everyone to build upon the work.  

  

  
**How to get involved and contribute to OpenSK **  

  

To learn more about OpenSK and how to experiment with making your own security key, you can check out our [GitHub repository](https://github.com/google/OpenSK) today. With the help of the research and developer communities, we hope OpenSK over time will bring innovative features, stronger embedded crypto, and encourage widespread adoption of trusted phishing-resistant tokens and a passwordless web.  
**Acknowledgements**  
  
We also want to thank our OpenSK collaborators: Adam Langley, Alexei Czeskis, Arnar Birgisson, Borbala Benko, Christiaan Brand, Dirk Balfanz, Dominic Rizzo, Fabian Kaczmarczyck, Guillaume Endignoux, Jeff Hodges, Julien Cretin, Mark Risher, Oxana Comanescu, Tadek Pietraszek

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=rHM7PgY6L5c:36AsKnWzClI:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=rHM7PgY6L5c:36AsKnWzClI:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=rHM7PgY6L5c:36AsKnWzClI:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/rHM7PgY6L5c)  
  
from Google Online Security Blog https://ift.tt/37GzdR1  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)