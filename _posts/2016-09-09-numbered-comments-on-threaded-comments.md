---
title: 'Numbered Comments On Threaded Comments For Blogger/Blogspot'
date: 2020-01-13T06:39:00+01:00
draft: false
---

[In a previous tutorial](https://rdbrry.blogspot.com//search?q=how-to-number-comments-in) you've seen how you lot tin add together numbered comments to your blogger blog, unfortunately, this play a joke on worked entirely for those who don't choose the respond selection as well as are even hence using the one-time blogger commenting system. But nosotros won't choose whatever occupation this fourth dimension because this tutorial volition demo you lot how to add together numbered comments amongst comment bubbles on the threaded comments, also ;)  
  
What the next CSS play a joke on volition produce for you:  

1.  When the full general block of comments is initiating (.comments-content) a counter called countcomments activates as well as starts amongst an initial value of 1. 
2.  Then, each fourth dimension the code period of time goes through a review of whatever level, either the master comment or a respond (.comment-thread li), it volition convey us inward front end (:before) of the comment's trunk the set out that is the counter.  
    
3.  Finally, this is incremented inward the counter (counter-increment).

See the screenshot:

[![ve seen how you lot tin add together numbered comments to your blogger weblog Numbered comments on threaded comments for Blogger/Blogspot](http://4.bp.blogspot.com/-BYX5SB3FUYg/T8qQ5csgvsI/AAAAAAAACRQ/eitO9wJ_mJ0/s320/numbered+comments+for+threaded+comments+on+blogger+blogspot.png "Numbered comments on threaded comments for Blogger/Blogspot")](http://4.bp.blogspot.com/-BYX5SB3FUYg/T8qQ5csgvsI/AAAAAAAACRQ/eitO9wJ_mJ0/s1600/numbered+comments+for+threaded+comments+on+blogger+blogspot.png)

  
Isn't that great? I'm pretty certain many of you lot choose been waiting for this cool trick. So, let's laid about applying it for our threaded commenting system.  
  
**Steps to add together bubble comments count**  
  
**Step 1**: From your [Blogger Dashboard](http://blogger.com/), instruct to **Template** as well as click on the **Edit HTML** button:  

[![](http://1.bp.blogspot.com/-3GkUIt4Yizc/UTAL2ZcfjRI/AAAAAAAAC1o/F1TktDfC8pI/s1600/remove-blogger-labels.png)](http://1.bp.blogspot.com/-3GkUIt4Yizc/UTAL2ZcfjRI/AAAAAAAAC1o/F1TktDfC8pI/s1600/remove-blogger-labels.png)

  
... click anywhere within the code expanse as well as press CTRL + F to opened upward the Blogger' search box.  
  
**Step 2:** Type the next tag within the search box as well as hitting Enter to notice it:  

> \]\]>

_Note. you lot choose to click on the arrow adjacent to it, as well as hence search the \]\]> i to a greater extent than time _  
  
**Step 3:** Add the next code only above \]\]>:  

> .comment-thread ol {  
> counter-reset: countcomments;  
> }  
> .comment-thread li:before {  
> content: counter(countcomments,decimal);  
> counter-increment: countcomments;  
> float: right;  
> z-index: 2;  
> position:relative;  
> font-size: 22px;  
> color: #555555;  
> **padding-left:10px; **  
> **padding-top:3px; **  
> background: url(http://4.bp.blogspot.com/-f6ByQfbwApQ/T4x\_8p1FGpI/AAAAAAAAB2A/WJKf-ybmvQk/s1600/comment+bubble2.png) no-repeat;  
> **margin-top:7px; **  
> **margin-left:10px; **  
> width: 50px; /\*image-width size\*/  
> height: 48px; /\*image-height size\*/   
> }  
> .comment-thread ol ol {  
> counter-reset: contrebasse;  
> }  
> .comment-thread li li:before {  
> content: counter(countcomments,decimal) "." counter(contrebasse,lower-latin);  
> counter-increment: contrebasse;  
> float: right;  
> font-size: 18px;  
> color: #666666;  
> }

Note:  

*   if you lot desire to choose no bubble icon, take away the code inward red (including the address inward blue)
*   to alter the comment bubble, supersede the code inward blue amongst the URL address of your ain icon. If you're non certain what icon you lot should use, you lot tin notice roughly cool icons inward my previous posts (see these tutorials [here](https://rdbrry.blogspot.com//search?q=how-to-number-comments-in) as well as [here](https://rdbrry.blogspot.com//search?q=how-to-number-comments-in))
*   to alter the seat of comments count, increase/decrease the values (3 & 10) from **padding-top** as well as **padding-left**
*   to alter the seat of comments bubble/icon, alter the values (10 & 7) from **margin-left** as well as **margin-top**

**Step 4:** Now Save the Template as well as you're done!  
  
If you lot relish reading this blog, delight percentage as well as subscribe. For whatever questions you lot may have, instruct out a comment below.