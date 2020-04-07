---
title: 'How To Take Away Blogger Picture/Image Shadow In Addition To Border'
date: 2020-02-11T06:39:00+01:00
draft: false
---

If y'all desire to boot the bucket rid of those annoying shadows as well as borders roughly blogger images, as well as thus follow the adjacent steps (see the divergence inward the screenshot below):  

[![](http://3.bp.blogspot.com/-E1Egx--Lp4w/Urhcy2vI71I/AAAAAAAAFos/vdkIPgCuSHM/s320/remove-blogger-picture-image-shadow-border.png)](http://3.bp.blogspot.com/-E1Egx--Lp4w/Urhcy2vI71I/AAAAAAAAFos/vdkIPgCuSHM/s1600/remove-blogger-picture-image-shadow-border.png)

  

[![](http://4.bp.blogspot.com/-syGpT44xiSY/T39_meD5CTI/AAAAAAAABrg/zxsnViV8dQ4/s640/how+to+remove+borders+or+shadows+around+images+in+blogger+blogspot.png)](http://4.bp.blogspot.com/-syGpT44xiSY/T39_meD5CTI/AAAAAAAABrg/zxsnViV8dQ4/s1600/how+to+remove+borders+or+shadows+around+images+in+blogger+blogspot.png)

  
**If y'all are using the former Blogger interface:**  

*   Go to Dashboard - Design - Template Designer - Advanced - Add CSS - glue the next code - Press come inward later the final grapheme of the final business } - Apply to Blog.

  
**If y'all are using the novel Blogger interface:**  

*   Go to Dashboard - Template - Customize - Advanced - Add CSS - glue the next code - Press come inward later the final grapheme of the final business } - Apply to Blog.

> .post-body img, .post-body .tr-caption-container, .Profile img, .Image img,  
> .BlogList .item-thumbnail img {  
>   padding: 0 !important;  
>   border: none !important;  
>   background: none !important;  
>   -moz-box-shadow: 0px 0px 0px transparent !important;  
>   -webkit-box-shadow: 0px 0px 0px transparent !important;  
>   box-shadow: 0px 0px 0px transparent !important;  
> }

Screenshot

[![If y'all desire to boot the bucket rid of those annoying shadows as well as borders roughly blogger images How to take Blogger Picture/Image Shadow as well as Border](http://1.bp.blogspot.com/-umWUh9PVOC0/UrhZNROcO7I/AAAAAAAAFog/wkUye3BvVTg/s640/remove-hide-shadow-border-on-blogger-pictures-images.png "How to take Blogger Picture/Image Shadow as well as Border")](http://1.bp.blogspot.com/-umWUh9PVOC0/UrhZNROcO7I/AAAAAAAAFog/wkUye3BvVTg/s1600/remove-hide-shadow-border-on-blogger-pictures-images.png)

  
Now your blogger images should seem without whatever edge or shadow. Cheers!  
Update:  
  
If the to a higher house method doesn't operate for you, produce the following:  
  
\- Go to Blogger's Dashboard > Template > Edit HTML  
\- Click anywhere on the code expanse as well as search past times pressing the CTRL + F keys for the next code:  

>   border: 1px corporation $(image.border.color);  
>   
>   -moz-box-shadow: 1px 1px 5px rgba(0, 0, 0, .1);  
>   -webkit-box-shadow: 1px 1px 5px rgba(0, 0, 0, .1);  
>   box-shadow: 1px 1px 5px rgba(0, 0, 0, .1);

_Note: if y'all can't abide by the entire code, as well as thus essay to abide by this business as well as the remainder of it should appear:_  

> \-moz-box-shadow: 1px 1px 5px rgba(0, 0, 0, .1);

\- Delete it as well as Save your template.