---
title: 'How To Supercede Older Posts As Well As Newer Posts Links Alongside Blogger Postal Service Titles'
date: 2020-02-05T06:39:00+01:00
draft: false
---

If y'all accept e'er visited a WordPress blog, y'all mightiness accept noticed that the spider web log pager on these blogs displays the actual post service titles, non simply links to the older together with newer posts that y'all honor at the bottom of your Blogger blog. This links are parts of the so-called spider web log pager which helps readers navigate betwixt pages together with posts.  
  
If y'all desire to increment your page impressions, 1 of the ways is to supercede the older/newer posts links amongst the Blogger post service titles.  
  

![](https://4.bp.blogspot.com/-NRAGe0vDgg0/T4WXZfqmLsI/AAAAAAAABuw/2CQu-Hrv7bI/s200/add+blogger+blogspot+post+titles+instead+of+newer+older+posts+links+increase+page+impressions+blogger+tricks+tips.png)

### Adding Post Titles Instead of Older Post/Newer Post Links

Step 1. Log inwards to Blogger, become to Layout together with click on "Add H5N1 Gadget" link  
  

![](https://4.bp.blogspot.com/-LcW_xNLozrI/UTJQzFPdhEI/AAAAAAAAC4c/LQFO0DKxxm4/s1600/blogger-layout-add+a+gadget-how-to.png)

  
Step 2. From the pop-up window, select "HTML/JavaScript"  
  

![](https://2.bp.blogspot.com/-c2r6HAMX2EE/UTJRX0C3_eI/AAAAAAAAC4k/tqQrar_00tM/s1600/blogger-widgets-gadgets-tutorials-tricks-helplogger-html-javascrip.png)

  
Step 3. Paste the next code into the empty champaign of the HTML/JavaScript gadget:  
  

>   
> <br /> var olderLink = $("a.blog-pager-older-link").attr("href");<br /> $("a.blog-pager-older-link").load(olderLink+" h3:first", function() {<br /> var olderLinkTitle = $("a.blog-pager-older-link:first").text();<br /> $("a.blog-pager-older-link").text(olderLinkTitle);<br /> });<br /> var newerLink = $("a.blog-pager-newer-link").attr("href");<br /> $("a.blog-pager-newer-link").load(newerLink+" h3:first", function() {<br /> var newerLinkTitle = $("a.blog-pager-newer-link:first").text();<br /> $("a.blog-pager-newer-link").text(newerLinkTitle);<br /> });<br />

  
Note: The business inwards ruby-red is for acquiring jQuery framework. If y'all accept acquired jQuery inwards your template, together with hence y'all tin simply delete this part.  
  
Step 4. Now Save the Widget together with drag it nether the Blog Posts section.  
  

![](https://1.bp.blogspot.com/-ZDCNRI3L7x4/UTPFLV8opQI/AAAAAAAAC6k/TxKIvgA21hU/s1600/replace-older-newer-posts-with-post-titles-blogger-tutorials.png)

  
Step 5. Click on the "Save arrangement" button.  
  

![](https://1.bp.blogspot.com/-c7Gs7TL2sdw/UTH_LEFG6PI/AAAAAAAAC4I/pQtqluf-6SM/s1600/save-arrangement-blogger-widgets-page-elements.png)

  
Now stance your spider web log together with run across the older/newer posts link replaced amongst your post service titles.