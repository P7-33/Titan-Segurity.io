---
title: 'Firefox Will Soon Let You Set a Separate Search Engine for Private Mode'
date: 2019-10-06T10:38:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/10/mozilla-firefox-logo.jpg)

Mozilla has added a new feature in the latest nightly build of Firefox that will let you choose the search engine you want while browsing in private mode. This way, you will be able to set different search engines for normal mode and private mode.  

The feature seems to be inspired from Vivaldi browser, which uses DuckDuckGo as the default search engine in private mode. It is disabled by default and you will have to make a couple of changes in the **about:config** to enable it.  

I tried enabling the feature on Firefox Nightly version 71.0a1 (2019-10-03) (64-bit) and it worked just fine. If you’re interested to try out the feature on Firefox Nightly, follow the below steps.  

Enable Private Search Engine on Firefox Nightly
-----------------------------------------------

  

1\. [Download](https://www.mozilla.org/en-US/firefox/nightly/all/) and open the latest version of Firefox Nightly and go to about:config.  

![](https://beebom.com/wp-content/uploads/2019/10/firefox-about-config.jpg)

2\. In the search box that appears now, paste the commands mentioned below one by one and set the value to true.  

```
browser.search.separatePrivateDefault.enabled  
browser.search.separatePrivateDefault.ui.enabled
```  

3\. Now, navigate to Options -> Search -> Default Search Engine. From the drop-down list that appears below “Choose the default search engine to use in Private Windows”, pick the search engine you would like to use in private mode.  

![](https://beebom.com/wp-content/uploads/2019/10/firefox-nightly-private-tab-search-engine.jpg)

As of now, the browser lets you choose from Google, Bing, Amazon, DuckDuckGo, eBay, Twitter, and Wikipedia. You will still have the option to use the same search engine on both modes if you check the “Use this search engine in Private Windows” option.  

Now that Firefox nightly has gained support for this feature, there is a solid chance for it to be enabled by default on the next stable build of Firefox unless any major issue crops up with this implementation. So, are you excited to use this feature on your Firefox? Let us know in the comments.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/firefox-set-separate-search-engine-private-windows/)  
\[the\_ad id='1307'\]