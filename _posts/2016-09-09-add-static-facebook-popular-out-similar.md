---
title: 'Add Static Facebook Popular Out Similar Box Amongst Smoothen Jquery Hover Effect'
date: 2020-02-13T06:39:00+01:00
draft: false
---

In this tutorial, I volition present y'all how to add together a cool floating Facebook similar widget for Blogger that slides to the left on mouseover. Demo: You tin run across a static Facebook badge on the correct side of this blog:  
  

[Demo blog](http://demo-helplogger.blogspot.com/)

  

[![](http://4.bp.blogspot.com/-TvFOFKkPOeg/T387y_p5zQI/AAAAAAAABqg/-4kYennfj5M/s1600/floating+static+facebook+like+box+widget+for+blogger+blogspot.png)](http://4.bp.blogspot.com/-TvFOFKkPOeg/T387y_p5zQI/AAAAAAAABqg/-4kYennfj5M/s1600/floating+static+facebook+like+box+widget+for+blogger+blogspot.png)

  

### Adding Static Facebook Like widget on Blogger

Step 1. Log inward to your Blogger account, become to "Template" as well as hitting the "Edit HTML" button  

[![](http://3.bp.blogspot.com/-rP7Xdxqm5W0/UaJpKUUs7pI/AAAAAAAADfc/NP9sNObx2l4/s1600/blogger_blogspot_template_edit_html_tutorial.png)](http://3.bp.blogspot.com/-rP7Xdxqm5W0/UaJpKUUs7pI/AAAAAAAADfc/NP9sNObx2l4/s1600/blogger_blogspot_template_edit_html_tutorial.png)

  
Step 2. Click anywhere within the code surface area as well as press the CTRL + F keys to opened upwards the search box:  
  

[![](http://4.bp.blogspot.com/-pNjafQlLYFU/U69TmT3-feI/AAAAAAAAJZQ/BRdO0NS6vvc/s1600/open-blogger-search-box-ctrl%252Bf.png)](http://4.bp.blogspot.com/-pNjafQlLYFU/U69TmT3-feI/AAAAAAAAJZQ/BRdO0NS6vvc/s1600/open-blogger-search-box-ctrl%252Bf.png)

  
Step 3. Search (CTRL + F) for this tag:  

Step 4. Add the next code only before/above tag:  

Step 5. Save the Template.  
  
Step 6. Go to Layout > Add a novel Gadget > conduct the 'HTML/JavaScript' gadget as well as glue the code below inward the HTML box:  

> <br /> #fbplikebox {<br />     display: block;<br />     padding: 0;<br />     z-index: 99999;<br />     position: fixed;<br />     background: <span style="color: red;">#ffffff</span>;<br /> }<br /> <br /> .fbplbadge {<br />     background-color: <span style="color: red;">#3B5998</span>;<br />     display: block;<br />     height: 150px;<br />     top: 50%;<br />     margin-top: -75px;<br />     position: absolute;<br />     left: -47px;<br />     width: 47px;<br />     background-image: url("http://3.bp.blogspot.com/-1GCgbuSZXK0/T38iRiVF41I/AAAAAAAABpg/WlGuQ3fi-Rs/s1600/vertical-right.png");<br />     background-repeat: no-repeat;<br />     overflow: hidden;<br />     -webkit-border-top-left-radius: 8px;<br />     -webkit-border-bottom-left-radius: 8px;<br />     -moz-border-radius-topleft: 8px;<br />     -moz-border-radius-bottomleft: 8px;<br />     border-top-left-radius: 8px;<br />     border-bottom-left-radius: 8px;<br /> }<br />  
> <br /> /\*<!\[CDATA\[\*/<br />     (function(w2b){<br />         w2b(document).ready(function(){<br />             var $dur = "medium"; // Duration of Animation<br />             w2b("#fbplikebox").css({right: -250, "top" : 100 })<br />             w2b("#fbplikebox").hover(function () {<br />                 w2b(this).stop().animate({<br />                     right: 0<br />                 }, $dur);<br />             }, part () {<br />                 w2b(this).stop().animate({<br />                     right: -250<br />                 }, $dur);<br />             });<br />             w2b("#fbplikebox").show();<br />         });<br />     })(jQuery);<br /> /\*\]\]>\*/<br />  
> 
>   
>    
> 
>   
>     YOUR-FACEBOOK-PAGE</span>&width=<b><span style="color: red;">250</span></b>&height=<b><span style="color: red;">250</span></b>&colorscheme=light&show\_faces=true&border\_color=%23C4C4C4&stream=false&header=false" scrolling="no" frameborder="0" style="border:none; overflow:hidden; width:<span style="color: red;"><b>250</b></span>px; height:<span style="color: red;"><b>250</b></span>px;" allowtransparency="true">  

Step 7. Replace YOUR-FACEBOOK-PAGE text amongst your Facebook fan page URL. Then, y'all volition bespeak to supersede the next characters inward the URL, every bit follows:  
  
The  : symbol with:  

> %3A

The  / symbol with:  

> %2F

For example, the Facebook fan page of this spider web log is:  

> http://www.facebook.com/pages//120574614736021

After replacing the inward a higher house symbols, the Facebook fan page would await similar this:  

> http%3A%2F%2Fwww.facebook.com%2Fpages%2F%2F120574614736021

Other settings (optional):  
\- to alter background color of the fan box, supersede the #ffffff value inward red. You tin pick the favorite color using this [Color Code Generator](https://rdbrry.blogspot.com//search?q=color-code-generator).  
\- to alter the Facebook badge color, supersede the #3B5998 color value amongst your own.  
\- to alter the width as well as pinnacle of the Facebook box, alter the values inward carmine (**250**)  
  
Step 8. Now y'all tin relieve this static Facebook fan box widget - press the 'Save' button. Enjoy!  
  
Credit goes to Harish (way2blogging)