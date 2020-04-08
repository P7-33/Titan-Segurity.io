---
title: 'The Catch-22 of Building a Business on Apple’s APIs – Astroblog'
date: 2019-10-24T04:01:00+01:00
draft: false
---

![](https://lxv1rhv288-flywheel.netdna-ssl.com/wp-content/uploads/2019/09/retro2-1024x686.jpg)

As an iOS development community, we need to talk about APIs. Apple has created an incredible platform with powerful APIs for us to build on, but we should be mindful of getting locked in. While adopting the latest APIs and language features is in the best interest of Apple, it can create dangerous catch-22 situations for third-party developers. 

Here at Astropad, we’ve developed a unique low-latency, high-fidelity video streaming technology we call Liquid. Liquid is what makes both **[Astropad Studio](https://astropad.com/)** and [**Luna Display**](https://lunadisplay.com/) possible — and it was designed for the unique demands of creative professionals, such as illustrators, animators, and photographers. In the five years since we launched Astropad, we’ve come to realize how difficult it is to strike harmony between living in the Apple ecosystem and growing a sustainable business. 

### What’s good for Apple isn’t necessarily good for you

Apple always encourages adopting their latest APIs, tools, and languages like Swift; they’re incredibly powerful resources, but they also make us dependent on Apple’s ecosystem. From Apple’s perspective, they are happy to lock developers in. If they can have tons of incredible and unique apps that are exclusive to their platforms, that makes Apple’s products _that much more_ compelling to their customers. 

But for a third-party developer, dependency on Apple’s APIs puts you in a tricky spot: it limits your customer base, and it puts your business at risk if Apple decides to compete with your product offering. If Apple ever offers a similar product for free, bundled into the operating system, it will be tough for your app to compete.   

This is something that we experienced first hand when Apple recently launched Sidecar, a native macOS feature that competes directly with our products. And we’re just one example of this. Apple has an extensive history of [sherlocking](https://beta.washingtonpost.com/technology/2019/09/05/how-apple-uses-its-app-store-copy-best-ideas/?noredirect=on), and has continued this behavior with the most recent release of its mobile OS — launching native features that move into the parental control and menstrual tracking app territory. Unraveling your dependency on Apple starts with building a foundation for cross-platform code.   

### Launch your prototype on one platform, but don’t linger

For the MVP stage of a product, it makes a lot of sense to use tools you know and to launch exclusively on one platform. Why build out a complex cross-platform architecture, when you don’t even know if you’re building a product that people want? When we started developing Liquid, we used the tools we were most comfortable with, like Objective-C and the Cocoa APIs. This allowed us to move quickly, launch Astropad 1.0, and establish product-market fit in a relatively short period of time. 

However, once you’ve established product market fit you need to start thinking about spreading your wings. We made the mistake of doubling down on Objective-C, when we should have been untangling ourselves from Objective-C and the Cocoa APIs. 

### Build a cross-platform core 

I’m not suggesting that you write everything in cross-platform toolkits like Qt or WxWidgets, and never use platform specific APIs. Doing so is a sure path to making subpar apps that feel clunky and unpolished. The difference is that your core engine, your _secret sauce_, should be written in a cross-platform fashion. From there, you can layer your engine with native UI, APIs, and languages. 

When your engine is tied to specific Apple APIs, that’s when you enter dangerous territory and box yourself in. What do I consider dangerous?

*   An audio app that relies on the [Accelerate framework](https://developer.apple.com/documentation/accelerate?language=objc) for it’s signature algorithms
*   A photo processing app that uses [Metal Performance Shaders](https://developer.apple.com/documentation/metalperformanceshaders?language=objc) to perform its tricks
*   A vector graphics app that relies on [CoreGraphics](https://developer.apple.com/documentation/coregraphics?language=objc) to render
*   A subscription iOS app that doesn’t have it’s own subscription backend server
*   A travel app with a sophisticated rules engine written in Swift

It’s never been easy to run Objective-C on anything but Mac and iOS, and while there are early attempts at running Swift on other platforms, how committed to that effort do you think will Apple be? In all of these cases, it would be better to have a core written in a portable language like C, C++, or Rust with a UI layer wrapping it in Swift or Objective-C.

### Our future is in Rust

For years our customers have been asking us for Windows-based versions of our products, but our reliance on Objective-C has made that incredibly hard. We’ve tried to port our core Liquid platform to Windows via WinObjC and GNUStep, but both attempts produced only partial success and a brittle platform that we’d be hesitant to build on for the future. 

We’ve taken the plunge and are in the process of [rewriting our entire Liquid platform in Rust](https://blog.astropad.com/why-rust/) with a sprinkling of a C/C++. Building our Liquid platform in Rust is setting us up for the future. Soon, we’ll have a high-performance and portable platform that we can easily run on Mac, iOS, Linux, Android and Windows. In addition, we see many interesting new uses for our Liquid technology that we’ll be able to pursue with our Rust based platform.

### Think about an exit

If you’re building a technology company that you’d like to eventually sell, you’re also dramatically limiting your options by locking yourselves into Apple’s ecosystem. Let’s say you build incredible new photography technology in Swift and Metal — you’ve built tech that really has only one potential acquirer: Apple. But what if Apple isn’t interested or they decide to build it themselves? Uh oh. 

Now imagine instead your technology is cross platform. Suddenly your potential acquirers expand to companies like Microsoft, Google, Samsung, Adobe, and virtually anyone else in the photography space. You might even have a bidding war on your hands! Once one company launches a new feature, the others generally acquire or build to have parity (for example Apple has Siri, Microsoft has Cortana, Samsung has Bixby, and Google has Assistant — they all copy each other!). 

* * *

As developers in the iOS community, we need to be more business savvy and realize that adopting platform-specific APIs have implications that may affect our companies for years to come. We learned this the hard way, but we are now fixing it by moving our Liquid platform to Rust, and unlocking possibilities we’ve dreamed about for years. Before long our Liquid technology will run on Mac, iOS, Windows, Android, Linux servers, and even embedded devices! Stay tuned, we may surprise you with what we do next. 

  
  
from Hacker News https://ift.tt/2pjXRp3