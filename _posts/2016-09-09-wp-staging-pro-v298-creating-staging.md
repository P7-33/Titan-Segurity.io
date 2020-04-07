---
title: 'WP Staging Pro v2.9.8 – Creating Staging Sites nulled'
date: 2020-01-15T06:34:00+01:00
draft: false
---

The Floating Social Media Sharing is a really pop widget on all the move on blogs in addition to this is ane of the ways to growth the publish of times your posts teach shared on Twitter, Facebook in addition to other social networks.  
  
This floating social bar has the next options: Facebook Like, StumbleUpon, Twitter Share, Digg This, Google+ in addition to each of them comes amongst a alive counter. You tin laissez passer the sack add together to a greater extent than sharing buttons or social bookmarking icons afterward if yous want.  
  

[![The Floating Social Media Sharing is a really pop widget on all the move on blogs in addition to this i Add Floating Social Media Sharing Buttons To Blogger](http://3.bp.blogspot.com/-rIlx0X-LCbA/T8fyN49zeoI/AAAAAAAACPY/zlYt6K-lm5c/s320/01-06-2012+01-27-30.png "Add Floating Social Media Sharing Buttons To Blogger")](http://3.bp.blogspot.com/-rIlx0X-LCbA/T8fyN49zeoI/AAAAAAAACPY/zlYt6K-lm5c/s1600/01-06-2012+01-27-30.png)

  

### **How to add together the scrolling social bookmarking bar**

  
**Step 1.** Log inward to your [Blogger Dashboard](http://blogger.com/), lead your weblog in addition to teach to **Layout **  
  
**Step 2.** Click on **Add Influenza A virus subtype H5N1 Gadget** link  

  

[![](http://4.bp.blogspot.com/-mLvgiM6vofE/UTAOF5A25HI/AAAAAAAAC2E/weSw-aAkSeE/s1600/add-a-gadget-blogger-layout.png)](http://4.bp.blogspot.com/-mLvgiM6vofE/UTAOF5A25HI/AAAAAAAAC2E/weSw-aAkSeE/s1600/add-a-gadget-blogger-layout.png)

  
**Step 3.** From the pop-up window, scroll downwardly in addition to lead **HTML/Javascript**   

[![](http://4.bp.blogspot.com/-P2TH6ji2oHw/UTAOqQFPGAI/AAAAAAAAC2Q/M6VnFBd74cc/s1600/html-javascript-blogger-gadgets-widgets.png)](http://4.bp.blogspot.com/-P2TH6ji2oHw/UTAOqQFPGAI/AAAAAAAAC2Q/M6VnFBd74cc/s1600/html-javascript-blogger-gadgets-widgets.png)

  
**Step 4.** Copy the code below in addition to glue it within the empty box.  

  
**Step 5.** [Save](http://4.bp.blogspot.com/-vHuQ4iXW0YQ/UTD79mQXBeI/AAAAAAAAC2k/UDpF4RtWJms/s1600/save-html-javascript-blogger-widget.png) the gadget.

  
The code to copy-paste (updated!):  

> <br /> #social-buttons {<br /> position:fixed;<br /> <b>bottom:<span style="color: #cc0000;">15%</span>; </b><br /> margin-left:<b><span style="color: red;">-721px</span></b>;<br /> float:left;<br /> border-radius:5px;<br /> -moz-border-radius:5px;<br /> -webkit-border-radius:5px;<br /> background-color:#fff;<br /> padding:0 0 2px 0;<br /> z-index:10;<br /> }<br /> #social-buttons .button-share {<br /> float:left;<br /> clear:both;<br /> margin:5px 5px 0 2px;<br /> }<br />  
> 
>   
> 
>   
> 
>   
> (function(d, s, id) {<br />   var js, fjs = d.getElementsByTagName(s)\[0\];<br />   if (d.getElementById(id)) return;<br />   js = d.createElement(s); js.id = id;<br />   js.src = "//connect.facebook.net/en\_US/all.js#xfbml=1";<br />   fjs.parentNode.insertBefore(js, fjs);<br /> }(document, 'script', 'facebook-jssdk'));  
> 
>   
> 
>   
>   
> 
> [Tweet](http://twitter.com/share)  
>   
>   
> 
>   
>   
> 
>   
> 
>   
>   
>   
> 
>   
> 
>   
>   
>   
> 
>   
> 
> Get [widget](https://rdbrry.blogspot.com//)

**Customization:**

*   Vertical alignment - Change the **15%** value of **bottom**. The code positions the social bar relative to the bottom of your browser window. To cook the distance fifty-fifty when window is resized, specify the value inward px (pixels) instead of %.

*   Horizontal alignment - Change the **\-721px** value from **margin-left.** Negative value pushes the clit to the left of the master copy blog column, positive value pushes it to the right. Increase or decrease the value based on your needs.

*   Twitter setting - Replace amongst your Twitter username

*   Replacing in addition to removing buttons - You tin laissez passer the sack supplant existing buttons amongst your own. Each clit is represented past times this code:

> **_
> 
> BUTTON CODE HERE
> 
> _**

Enjoy!!! :)