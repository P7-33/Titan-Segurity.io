---
title: 'A Beautiful Jquery Drop-Down Carte For Blogger Blogspot'
date: 2020-01-26T06:39:00+01:00
draft: false
---

Alright, this time, nosotros are going to brand a fashionable together with uncomplicated jQuery driblet downwards menu. The principal objective is to instruct inwards every bit uncomplicated every bit possible, alongside to a greater extent than or less piddling jQuery resultant together with slow to customize/ apply dissimilar manner on it. To manner it into your ain design, y'all but accept to modify the a tag CSS style. You tin alter colors or pose background images, or the size together with color of text.  

[![ nosotros are going to brand a fashionable together with uncomplicated jQuery driblet downwards card Influenza A virus subtype H5N1 Beautiful jQuery Drop-Down Menu For Blogger Blogspot](http://2.bp.blogspot.com/-0mIXTPD72YA/T5l9NZW1nNI/AAAAAAAACAA/Uaez2XJIQSI/s200/add+a+drop+down+menu+for+blogger+blogspot.png "A Beautiful jQuery Drop-Down Menu For Blogger Blogspot")](http://2.bp.blogspot.com/-0mIXTPD72YA/T5l9NZW1nNI/AAAAAAAACAA/Uaez2XJIQSI/s1600/add+a+drop+down+menu+for+blogger+blogspot.png)

  

How to Add jQuery Drop-Down card inwards Blogger
------------------------------------------------

Step 1. Log inwards to your Blogger concern human relationship together with become to Template - Edit HTML  
  

[![](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)

  
Step 2. Click anywhere within the code surface area together with press the CTRL + F keys to opened upward the search box  
  

[![](http://4.bp.blogspot.com/-pNjafQlLYFU/U69TmT3-feI/AAAAAAAAJZQ/BRdO0NS6vvc/s1600/open-blogger-search-box-ctrl%252Bf.png)](http://4.bp.blogspot.com/-pNjafQlLYFU/U69TmT3-feI/AAAAAAAAJZQ/BRdO0NS6vvc/s1600/open-blogger-search-box-ctrl%252Bf.png)

  
Step 3. Type or glue this tag within the search box together with striking Enter to notice it:  

> \]\]>

Step 4. Add the next CSS but inwards a higher house \]\]>  

> #jsddm {  
> height: 40px;  
> margin: 0;  
> overflow: visible;  
> z-index: 2;  
> padding: 15px;  
> position:relative;  
> }  
> #jsddm li {  
> float: left;  
> list-style: none;  
> font: 12px Tahoma, Arial;  
> }  
> #jsddm li a {  
> display: block;  
> white-space: nowrap;  
> margin:1px 3px;  
> border: 1px company #AAAAAA;  
> background: #cccccc;  
> background: -webkit-gradient(linear, left top, left bottom, from(#ebebeb), to(#cccccc));  
> background: -moz-linear-gradient(top, #ebebeb, #cccccc);  
> padding: 5px 10px;  
> \-webkit-border-radius: 5px;  
> \-moz-border-radius: 5px;  
> border-radius: 5px;  
> text-shadow: #ffffff 0 1px 0;  
> color: #363636;  
> font-size: 15px;  
> font-family: Helvetica, Arial, Sans-Serif;  
> text-decoration: none;  
> vertical-align: middle;  
> }  
> #jsddm li a:hover {  
> background: #C8C8C8;  
> }  
> #jsddm li ul {  
> margin: 0;  
> padding: 0;  
> position: absolute;  
> visibility: hidden;  
> border-top: 1px company white;  
> }  
> #jsddm li ul li {  
> float: none;  
> display: inline;  
> }  
> #jsddm li ul li a {  
> width: auto;  
> background: #CAE8FA;  
> }  
> #jsddm li ul li a:hover {  
> background: #A3CEE5;  
> }

  
Step 5. Find this tag:  

Step 6. Add this script correct above/before it:  

> <br />   <script type='text/javascript'><br />   //<!\[CDATA\[<br /> var timeout    = 500;<br />   var closetimer = 0;<br />   var ddmenuitem = 0;<br /> business office jsddm\_open()<br />   {  jsddm\_canceltimer();<br />   jsddm\_close();<br />   ddmenuitem = $(this).find('ul').css('visibility', 'visible');}<br /> business office jsddm\_close()<br />   {  if(ddmenuitem) ddmenuitem.css('visibility', 'hidden');}<br /> business office jsddm\_timer()<br />   {  closetimer = window.setTimeout(jsddm\_close, timeout);}<br /> business office jsddm\_canceltimer()<br />   {  if(closetimer)<br />   {  window.clearTimeout(closetimer);<br />   closetimer = null;}}<br /> $(document).ready(function()<br />   {  $('#jsddm > li').bind('mouseover', jsddm\_open)<br />   $('#jsddm > li').bind('mouseout',  jsddm\_timer)});<br /> document.onclick = jsddm\_close;<br />   //\]\]><br />  

Step 7. Hit the "Save Template" push clitoris to salve the changes.  
  
Step 8. Now let's add together the HTML construction of the menu: Go to Layout > click on "Add a gadget" link  
  

[![](http://4.bp.blogspot.com/-mLvgiM6vofE/UTAOF5A25HI/AAAAAAAAC2E/weSw-aAkSeE/s1600/add-a-gadget-blogger-layout.png)](http://4.bp.blogspot.com/-mLvgiM6vofE/UTAOF5A25HI/AAAAAAAAC2E/weSw-aAkSeE/s1600/add-a-gadget-blogger-layout.png)

  
Step 9. Choose HTML/JavaScript from the pop-up window  
  

[![](http://4.bp.blogspot.com/-P2TH6ji2oHw/UTAOqQFPGAI/AAAAAAAAC2Q/M6VnFBd74cc/s1600/html-javascript-blogger-gadgets-widgets.png)](http://4.bp.blogspot.com/-P2TH6ji2oHw/UTAOqQFPGAI/AAAAAAAAC2Q/M6VnFBd74cc/s1600/html-javascript-blogger-gadgets-widgets.png)

  
Step 10. Paste the next code inwards the empty box:  

>   
>  *   [#">Home](<span style=)  
>      
> *   [#">Link 1](<span style=)  
>      
>     
>       
>      *   [#">Drop 1-1](<span style=)
>       
>      *   [#">Drop 1-2](<span style=)
>       
>      *   [#">Drop 1-3](<span style=)
>       
>      
>     
>       
>      
>   
>  *   [#">Link 2](<span style=)  
>      
>     
>       
>      *   [#">Drop 2-1](<span style=)
>       
>      *   [#">Drop 2-2](<span style=)
>       
>      
>     
>       
>      
>   
>  *   [#">Link 3](<span style=)  
>      
>     
>       
>      *   [#">Drop 3-1](<span style=)
>       
>      *   [#">Drop 3-2](<span style=)
>       
>      *   [#">Drop 3-3](<span style=)
>       
>      *   [#">Drop 3-4](<span style=)
>       
>      
>     
>       
>      
>   
>  *   [#">Link 4](<span style=)
>   
>  *   [#">Link 5](<span style=)
>   
>  *   [#">Link 6](<span style=)
>   
>  

Note : Change the titles together with supercede the # symbol alongside the URL address of each of your links  
  
Step 11. Click the "Save" button.  
  

[![](http://4.bp.blogspot.com/-vHuQ4iXW0YQ/UTD79mQXBeI/AAAAAAAAC2k/UDpF4RtWJms/s1600/save-html-javascript-blogger-widget.png)](http://4.bp.blogspot.com/-vHuQ4iXW0YQ/UTD79mQXBeI/AAAAAAAAC2k/UDpF4RtWJms/s1600/save-html-javascript-blogger-widget.png)

  
Important:  
\- if your card is on the sidebar, or footer, but drag it to your page header together with click Save again.  
\- if driblet downwards links are non showing, create the following:  
  
Go dorsum to Template > Edit HTML together with search (CTRL + F) this code:  

Change 1 with 3 together with no alongside yes similar this:

Save the Template.  
  
And again, become to Layout together with drag the card forthwith below the header  
  

[![](http://1.bp.blogspot.com/-QcnBEUnFa3s/UTH9-oOgnVI/AAAAAAAAC34/_zT0uBKIqwk/s1600/drag-widget-below-blogger-header-jquery-drop-down-menu.png)](http://1.bp.blogspot.com/-QcnBEUnFa3s/UTH9-oOgnVI/AAAAAAAAC34/_zT0uBKIqwk/s1600/drag-widget-below-blogger-header-jquery-drop-down-menu.png)

  
Click the "Save Arrangement" on the upper correct side together with that's it!  
  

[![](http://1.bp.blogspot.com/-c7Gs7TL2sdw/UTH_LEFG6PI/AAAAAAAAC4E/njjmOV9h0jQ/s1600/save-arrangement-blogger-widgets-page-elements.png)](http://1.bp.blogspot.com/-c7Gs7TL2sdw/UTH_LEFG6PI/AAAAAAAAC4E/njjmOV9h0jQ/s1600/save-arrangement-blogger-widgets-page-elements.png)

  
Here y'all tin run into the [DEMO](http://drop-down-menu1.blogspot.com/).