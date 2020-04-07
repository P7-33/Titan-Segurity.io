---
title: 'How To Customize Blogger''s Lightbox'
date: 2020-01-10T06:39:00+01:00
draft: false
---

For those of you lot who convey chosen to role the Blogger's Lightbox View for displaying pictures when clicking on them, you lot convey the selection to modify its agency inwards a whole dissimilar way. You volition live on able to modify the dark color of the screen, the edge or shadow of the images in addition to the color of the thumbnails background. We tin laissez passer on the sack customize the Blogger Lightbox solely on our taste.  
  

[![For those of you lot who convey chosen to role the Blogger How to Customize Blogger's Lightbox](http://3.bp.blogspot.com/-bQEJPVQLkQ8/UTVQzOygfAI/AAAAAAAAC9I/3vRYJyv3lIM/s320/modify-the-blogger-lightbox-background-style-color-3.png "How to Customize Blogger's Lightbox")](http://3.bp.blogspot.com/-bQEJPVQLkQ8/UTVQzOygfAI/AAAAAAAAC9I/3vRYJyv3lIM/s1600/modify-the-blogger-lightbox-background-style-color-3.png)

**Demo**  
  
Take a await at the screenshots below:  
  

**Before**:

  

[![For those of you lot who convey chosen to role the Blogger How to Customize Blogger's Lightbox](http://1.bp.blogspot.com/-PxVYvEGO39k/UTVJ2ktC2sI/AAAAAAAAC8c/I6U60aZUkjc/s320/how-to-change-the-style-background-of-blogger-lightbox.png "How to Customize Blogger's Lightbox")](http://1.bp.blogspot.com/-PxVYvEGO39k/UTVJ2ktC2sI/AAAAAAAAC8c/I6U60aZUkjc/s1600/how-to-change-the-style-background-of-blogger-lightbox.png)

  

**After:**

  

[![For those of you lot who convey chosen to role the Blogger How to Customize Blogger's Lightbox](http://1.bp.blogspot.com/-LtcTm_5yjEo/UTVK5_RXGlI/AAAAAAAAC8w/KINeUY501KA/s320/modify-the-blogger-lightbox-background-style-color-2.png "How to Customize Blogger's Lightbox")](http://1.bp.blogspot.com/-LtcTm_5yjEo/UTVK5_RXGlI/AAAAAAAAC8w/KINeUY501KA/s1600/modify-the-blogger-lightbox-background-style-color-2.png)

  
After adding our CSS code, the entire await of the modal window volition live on changed: the background color, the bar showing the thumbnails, the edge of images, the text within it, transparency in addition to the unopen button.  
  

[![For those of you lot who convey chosen to role the Blogger How to Customize Blogger's Lightbox](http://2.bp.blogspot.com/-bQEJPVQLkQ8/UTVQzOygfAI/AAAAAAAAC9E/ZEjv5cwhat0/s640/modify-the-blogger-lightbox-background-style-color-3.png "How to Customize Blogger's Lightbox")](http://2.bp.blogspot.com/-bQEJPVQLkQ8/UTVQzOygfAI/AAAAAAAAC9E/ZEjv5cwhat0/s1600/modify-the-blogger-lightbox-background-style-color-3.png)

  
All nosotros convey to create is to overwrite the default styles in addition to modify them alongside ours.  
  
**How to Change the Blogger's Lightbox Background in addition to Style**  
  
**Step 1.** Go to Template, click on the Edit HTML push clitoris (also click on the Proceed push clitoris if needed)  
  

[![](http://3.bp.blogspot.com/-rP7Xdxqm5W0/UaJpKUUs7pI/AAAAAAAADfc/NP9sNObx2l4/s1600/blogger_blogspot_template_edit_html_tutorial.png)](http://3.bp.blogspot.com/-rP7Xdxqm5W0/UaJpKUUs7pI/AAAAAAAADfc/NP9sNObx2l4/s1600/blogger_blogspot_template_edit_html_tutorial.png)

  
**Step 2.** Click anywhere within the code expanse in addition to search using CTRL + F the next tag:  

**Step 3.** Just higher upward the tag, add together the next code:  

> <br /> <span style="color: #38761d;">/\* Background Color \*/</span><br /> .CSS\_LIGHTBOX\_BG\_MASK {<br /> background-color: #ffffff !important;<br /> background-image: url(<span style="color: #cc0000;">image-url-address</span>) !important;<br /> opacity: <span style="color: orange;">0.8</span> !important;<br /> filter: alpha(opacity=90) !important;<br /> }<br /> <span style="color: #38761d;">/\* Images Border \*/</span><br /> .CSS\_LIGHTBOX\_SCALED\_IMAGE\_IMG {<br /> outline: 0px corporation #fff !important;<br /> -webkit-border-radius: 10px;<br /> -moz-border-radius: 10px;<br /> border-radius: 10px;<br /> -webkit-box-shadow: 0px 0px 5px #000000;<br /> -moz-box-shadow: 0px 0px 5px #000000;<br /> box-shadow: 0px 0px 5px #000000;<br /> }<br /> <span style="color: #38761d;">/\* Close Button \*/</span><br /> .CSS\_LIGHTBOX\_BTN\_CLOSE {<br /> background: url(<span style="color: blue;">image-url</span>) no-repeat !important;<br /> width: 24px !important;<br /> height: 24px !important;<br /> }<br /> <span style="color: #38761d;">/\* Thumbnails Bar Color \*/</span><br /> .CSS\_LIGHTBOX\_FILMSTRIP {<br /> background-color: #eaeaea !important;<br /> }<br /> <span style="color: #38761d;">/\* Text Color \*/</span><br /> .CSS\_LIGHTBOX\_ATTRIBUTION\_INFO, .CSS\_LIGHTBOX\_ATTRIBUTION\_LINK {<br /> color: #000 !important;<br /> }<br /> <span style="color: #38761d;">/\* Index Info (number of images) \*/</span><br /> .CSS\_LIGHTBOX\_INDEX\_INFO {<br /> color: <i>#555555</i> !important;<br /> }<br />

  
**Note:**  
\- The text inwards light-green explains to which business office the code belongs to in addition to it doesn't require to live on modified  
  
For example, the component below / \* Background Color \* / can modify the background color or fifty-fifty the LightBox background color alongside an epitome - for this, modify this job yesteryear replacing the ruby-red text alongside the url address of your image:  

> background-image: url(image-url) !important;

\- Below is the opacity: if you lot add together a lower value ( 0.8 ) the background volition drib dead to a greater extent than transparent.  
  
\- To modify the icon for the unopen button, you lot convey to supersede the text inwards ruby-red from /\* Close Button \*/ with the URL of your image. (you tin laissez passer on the sack host epitome at tinypic or upload it into a blogger draft in addition to and then Copy the Link Location - read [this tutorial](https://rdbrry.blogspot.com//search?q=upload-images-and-get-url-of-image) for to a greater extent than info)  
\- To modify the text color of images, supersede the _#555555_ value from /\* Index Info (number of images) \*/  
  
\- We tin laissez passer on the sack too modify the await of the edge some our pictures similar nosotros tin laissez passer on the sack brand them to a greater extent than round, add together a shadow, etc... precisely recall this is CSS3 in addition to older versions of Internet Explorer volition non exhibit whatever changes.  
  
**Step 4.** Click on **Save Template** in addition to you're done!