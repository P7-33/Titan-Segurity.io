---
title: 'How Chrome’s “Tab Freezing” Will Save CPU and Battery'
date: 2019-10-16T11:49:00+01:00
draft: false
---

![Close up of the Google Chrome's logo.](https://www.howtogeek.com/wp-content/uploads/2019/07/stock-lede-google-chrome-variant.png)

Google is working on a new “Tab Freeze” feature for Chrome, which will pause (freeze) tabs you’re not using. That means lower CPU usage, a faster browser, and longer battery life on a laptop or convertible.

The Problem: Too Many Tabs
--------------------------

If you only had a single tab open at all times, Chrome would only need to render one web page at once. But you probably have more. Even while you’re not using them, each tab you have open in Chrome contains an open web page. That web page uses system memory. Any scripts and other active content on it continue running, too, which means the web page can use CPU resources in the background.

In some ways, this is good: Even if you switch tabs, a tab can continue playing audio or updating itself in the background. When you switch back to it, you don’t need to wait for the web page to reload—it’s instant.

But it can be bad. If you have a large number of tabs open—or even just a small number of tabs containing heavy web pages—they can use a lot of system resources, filling up your memory, taking up CPU cycles, making Chrome less responsive, and draining your battery. That’s why Chrome’s engineers created Tab Discarding and, now, Tab Freezing. They’re related features, but do different things in different situations.

How Tab Discarding Saves Your RAM
---------------------------------

![A large number of tabs open on Chrome's tab bar.](https://www.howtogeek.com/wp-content/uploads/2019/10/img_5da650d75fa7d.png)

Tab Discarding was added back in 2015. This is a “memory-saving” feature, as [Google](https://developers.google.com/web/updates/2015/09/tab-discarding) puts it. In short, if your computer is low on memory, Chrome will automatically “discard” the contents of “uninteresting” tabs. Chrome won’t automatically discard a tab if you’re interacting with it, but that background tab you haven’t interacted with in hours is a prime target.

When a tab’s contents are discarded, it’s removed from your system’s memory, and the state is saved to disk. Nothing changes in Chrome’s interface—the tab appears on your tab bar and looks normal. But, when you click it and switch to it, you’ll see Chrome take a moment to quickly reload the page and get you back to where you were.

This slight delay is why Chrome only discards tab when your system’s memory is “running pretty low.” [It’s good to use your RAM for caching](https://www.howtogeek.com/128130/htg-explains-why-its-good-that-your-computers-ram-is-full/). But automatically discarding a tab and quickly reopening it is better than forcing Chrome’s user’s to bookmark and close tabs manually.

### [Read the remaining 16 paragraphs](https://www.howtogeek.com/444481/how-chromes-tab-freezing-will-save-cpu-and-battery/)