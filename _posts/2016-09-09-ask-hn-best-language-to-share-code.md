---
title: 'Ask HN: Best language to share code between an Android and iOS app?'
date: 2019-10-27T07:17:00+01:00
draft: false
---

[Ask HN: Best language to share code between an Android and iOS app?](https://news.ycombinator.com/item?id=21356203)

12 points by [mevorah](https://news.ycombinator.com/user?id=mevorah) [3 hours ago](https://news.ycombinator.com/item?id=21356203) | [hide](https://news.ycombinator.com/hide?id=21356203&goto=item%3Fid%3D21356203) | [past](https://hn.algolia.com/?query=Ask%20HN%3A%20Best%20language%20to%20share%20code%20between%20an%20Android%20and%20iOS%20app%3F&sort=byDate&dateRange=all&type=story&storyText=false&prefix&page=0) | [web](https://www.google.com/search?q=Ask%20HN%3A%20Best%20language%20to%20share%20code%20between%20an%20Android%20and%20iOS%20app%3F) | [favorite](https://news.ycombinator.com/fave?id=21356203&auth=117ca244c7cf96366a2b4d8fc047aa6388737231) | [6 comments](https://news.ycombinator.com/item?id=21356203)

Hello app developers of HN!

My team owns an Android (Kotlin) and iOS (Swift) app. The app is responsible for processing data, submitting to ML models, and then displaying results in a UI. We chose to do a lot of that processing in a shared Rust component. What we have found is a high overhead of bridging Kotlin/Swift to Rust. Some core logic has also seeped into our bridging code resulting in some duplication (exactly what we were trying to avoid).

With that, those of you who have found yourselves in similar situations, which language would you choose to be shared between your Android and iOS app (if any)?

  
  
  
  

![](https://news.ycombinator.com/s.gif)  

[Guidelines](https://news.ycombinator.com/newsguidelines.html) | [FAQ](https://news.ycombinator.com/newsfaq.html) | [Support](mailto:hn@ycombinator.com) | [API](https://github.com/HackerNews/API) | [Security](https://news.ycombinator.com/security.html) | [Lists](https://news.ycombinator.com/lists) | [Bookmarklet](https://news.ycombinator.com/bookmarklet.html) | [Legal](http://www.ycombinator.com/legal/) | [Apply to YC](http://www.ycombinator.com/apply/) | [Contact](mailto:hn@ycombinator.com)  
  

  
  
from Hacker News https://ift.tt/34cnPKH