---
title: 'How To Modify Avatar Size Inward Blogger Comments'
date: 2020-01-19T06:39:00+01:00
draft: false
---

This uncomplicated play tricks volition help y'all modify the avatars size inwards Blogger comments whose default size is of 36px... pretty pocket-sized considering that a lot of sites these days are using much larger avatars. To modify the agency in addition to size of avatars is real slow - y'all but ask to add together the CSS code inwards your Blogger template that volition brand size of avatars to bring width in addition to elevation of 64px.  
  

[![](http://3.bp.blogspot.com/-hEkLHsGX80g/T6W3RFtIRNI/AAAAAAAACEw/2E9gmbDvYiA/s320/how+to+change+avatar+size+in+blogger+blogspot+comments.png)](http://3.bp.blogspot.com/-hEkLHsGX80g/T6W3RFtIRNI/AAAAAAAACEw/2E9gmbDvYiA/s1600/how+to+change+avatar+size+in+blogger+blogspot+comments.png)

  
**Step 1. **Go to Dashboard - **Template** -  click on the **Edit HTML** button  
  

[![](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)

  
...click anywhere within the code surface area in addition to press CTRL + F to opened upwardly the blogger' search box  

[![](http://1.bp.blogspot.com/-5nCDW329k6I/Us9kWq0wcqI/AAAAAAAAF1I/PIe9SpIdtjc/s1600/blogger-template-search-box.png)](http://1.bp.blogspot.com/-5nCDW329k6I/Us9kWq0wcqI/AAAAAAAAF1I/PIe9SpIdtjc/s1600/blogger-template-search-box.png)

  
**Step 2.** Type or glue this tag within the search box in addition to hitting Enter to discovery it:  

> \]\]>

_Note: y'all may ask to click on the arrow adjacent to it in addition to thus search this tag again_  
  

**Step 3.** Depending on which comment arrangement y'all purpose (with reply/no reply), re-create in addition to glue 1 of the next codes but inwards a higher house it:  
  
_\[Works inwards Blogger threaded comment system\]_  

> .comments .avatar-image-container{  
> background-color: rgb(34, 34, 34);  
> border:1px corporation #ccc;  
> margin: 0px 10px 0px 0px;  
> padding: 0px 0px 0px 0px;  
> width: **64**px;  
> max-height: **64**px;  
> }  
> .comments .avatar-image-container img{  
> margin: 0px 0px 0px 0px;  
> padding: 0px 0px 0px 0px;  
> max-width: **64**px;  
> height: **64**px;  
> }

_\[for erstwhile blogger commenting system\]_  

> .avatar-image-container{  
> border:1px corporation #d6d6d6;  
> margin-left: -30px;  
> \-moz-border-radius: 4px;  
> background:#fff;  
> height:**70**px;  
> min-height: **70**px;  
> width:**70**px;  
> min-width:**70**px;  
> }  
> .avatar-image-container img {  
> background: url(**http://2.bp.blogspot.com/-gcjQ0sgWw7M/T6WpkK4S5AI/AAAAAAAACEQ/hYAWpCPl6P0/s200/anonymous.jpg**);  
> background-repeat: no-repeat;  
> background-position: center;  
> background-size: 100%;  
> width:**70**px;  
> min-width:**70**px;  
> height:**70**px;  
> min-height:**70**px;  
> }

Note: For bigger/smaller avatars, modify the values inwards red. To modify the anonymous avatar, supplant the URLs inwards bluish amongst your own. (works exclusively for the erstwhile commenting arrangement i.e. that has no respond option)  
  
**Step 4.** Cick on the **Save template** push clit to utilize the changes.  
  
That's it. Now the Blogger comments avatars should await bigger.