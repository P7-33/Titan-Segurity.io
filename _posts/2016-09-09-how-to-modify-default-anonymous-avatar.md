---
title: 'How To Modify Default Anonymous Avatar Inwards Blogger Comments'
date: 2020-01-18T06:39:00+01:00
draft: false
---

Earlier, you've seen [how you lot tin alter the size of the avatars inward blogger comments](https://rdbrry.blogspot.com//search?q=how-to-change-avatar-size-in-blogger) and now I volition demonstrate you lot how to alter or customize the default avatar of anonymous commenters or Blogger users amongst no flick on their profiles. While Blogger announced the novel threaded commenting system, nosotros tin notwithstanding customize it yesteryear adding a jQuery plugin to our template as well as and thence supervene upon the default anonymous avatar that tin live on works life on this address: _**http://img1.blogblog.com/img/anon36.png **_and the ane for blogger users: _**http://img2.blogblog.com/img/b36-rounded.png **_...with our own.  
  

[![how you lot tin alter the size of the avatars inward blogger comments How to Change Default Anonymous Avatar inward Blogger Comments](http://3.bp.blogspot.com/-zwRnvZri1WQ/T6ZuTfSj1PI/AAAAAAAACGo/G0RqCE7SLlA/s1600/change+anonymous+avatar+in+blogger+blogspot+comments.png "How to Change Default Anonymous Avatar inward Blogger Comments")](http://3.bp.blogspot.com/-zwRnvZri1WQ/T6ZuTfSj1PI/AAAAAAAACGo/G0RqCE7SLlA/s1600/change+anonymous+avatar+in+blogger+blogspot+comments.png)

  

### **Replace the Default Anonymous Avatar on Blogger Comments**

  
**Step 1. **Go to Dashboard - **Template** - click on the **Edit HTML** button  
  

[![](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)

  
...click anywhere within the code surface area as well as opened upwards the template search box yesteryear pressing the CTRL + F keys  
  
**Step 2.** Type or glue this code inward the search box, as well as thence hitting Enter to uncovering it:  

**Step 3.** Just inward a higher house the  tag, add together the next code:  

> <br /> <script><br /> $("img\[src='http://img1.blogblog.com/img/anon36.png'\]")<br /> .attr('src', '<b><span style="color: red;">http://1.bp.blogspot.com/-Zphr2YJH\_6w/T6ZZE4YeNBI/AAAAAAAACF0/Tyuj8hkOpdc/s1600/default\_avatar.gif</span></b>')<br /> .ssyby('blank')<br />  
> <br /> <script><br /> $("img\[src='http://img2.blogblog.com/img/b36-rounded.png'\]")<br /> .attr('src', '<b><span style="color: #0b5394;">http://1.bp.blogspot.com/-eKbzORzVaBQ/T6ZXHmdgHqI/AAAAAAAACFs/rVy3T4gxojM/s1600/blogger-user.png</span></b>')<br /> .ssyby('blank')<br />

**Step 4.** Save the changes yesteryear clicking on the **Save Template** button  
  

#### **Changing the default avatar**

**For Anonymous users: **Replace the code inward reddish amongst your picture address  
**For Blogger users: **Replace the URL inward blueish amongst your own.  
  
You tin pick out an avatar from hither as well as and thence re-create the url of it:  
  

![](http://1.bp.blogspot.com/-Zphr2YJH_6w/T6ZZE4YeNBI/AAAAAAAACF0/Tyuj8hkOpdc/s200/default_avatar.gif)

  

> http://1.bp.blogspot.com/-Zphr2YJH\_6w/T6ZZE4YeNBI/AAAAAAAACF0/Tyuj8hkOpdc/s200/default\_avatar.gif

  

![](http://3.bp.blogspot.com/-p4JvM7rWNG4/T6ZcU5eKqTI/AAAAAAAACGM/K0DB35A5brE/s1600/facebook.gif)

  

> http://3.bp.blogspot.com/-p4JvM7rWNG4/T6ZcU5eKqTI/AAAAAAAACGM/K0DB35A5brE/s1600/facebook.gif

  

![](http://2.bp.blogspot.com/-5nGzg5T-9qA/T6ZbL9JF0iI/AAAAAAAACF8/TvTnURwsNb0/s1600/anonymous3.png)

  

> http://2.bp.blogspot.com/-5nGzg5T-9qA/T6ZbL9JF0iI/AAAAAAAACF8/TvTnURwsNb0/s1600/anonymous3.png

  

  

![](http://3.bp.blogspot.com/-oivPlkvBNBY/T6ZoNQhfAII/AAAAAAAACGY/3gem5DBmmQ8/s1600/blogger-user.png)

  

> http://3.bp.blogspot.com/-oivPlkvBNBY/T6ZoNQhfAII/AAAAAAAACGY/3gem5DBmmQ8/s1600/blogger-user.png

  
That's it! If you lot works life this play a joke on useful, delight consider sharing it.