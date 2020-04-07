---
title: 'Simple Recent Posts Widget For Blogger/Blogspot'
date: 2020-01-25T06:39:00+01:00
draft: false
---

The brain wages on this [Recent Posts widget](https://rdbrry.blogspot.com//search?q=5-cool-recent-post-widgets-for-blogger) is that it volition demo non alone postal service titles, but every bit good postal service excerpts or snippets, in addition to it's slowly to customize or employ dissimilar fashion on it. To arrive check your ain design, y'all volition need to modify the CSS fashion - y'all tin attain notice modify the link or background color, the size in addition to color of text/links.  
  
What y'all tin attain notice create amongst this widget:  
\- display postal service titles alone  
\- modify the issue of posts  
\- modify the issue of characters of the postal service snippet/excerpt  
\- demo the postal service dates  
  
See the screenshot below:  

![](https://2.bp.blogspot.com/-q7SOzY4de4Q/T5wFy7i6p3I/AAAAAAAACAU/qiXglTJHxIc/s320/add+recent+posts+widget+for+blogger+blogspot.png)

  
  

How to add together Recent Posts Widget to Blogger
--------------------------------------------------

1\. Log inwards to your Blogger Dashboard > become to "Layout" in addition to click the "Add a Gadget" link:  
  

![](https://2.bp.blogspot.com/-LcW_xNLozrI/UTJQzFPdhEI/AAAAAAAAC4Y/o4QyC_MnUBg/s1600/blogger-layout-add+a+gadget-how-to.png)

  
2\. From the pop-up window, scroll downwardly in addition to pick out HTML/JavaScript from the list...  
  

![](https://4.bp.blogspot.com/-c2r6HAMX2EE/UTJRX0C3_eI/AAAAAAAAC4g/hoQcqhyvYU0/s1600/blogger-widgets-gadgets-tutorials-tricks-helplogger-html-javascrip.png)

  
3\. Select & re-create the code below the chosen widget in addition to glue it into the HTML/JavaScript content box:  
  

### Recent Posts Widget amongst Snippets

>   
> <br />function showrecentposts(t){for(var e=0;e<numposts;e++){var n,r=t.feed.entry\[e\],i=r.title.$t;if(e==t.feed.entry.length)break;for(var s=0;s<r.link.length;s++)if("alternate"==r.link\[s\].rel){n=r.link\[s\].href;break}i=i.link(n);var a="...",d=r.published.$t,u=d.substring(0,4),o=d.substring(5,7),c=d.substring(8,10),l=new Array;if(l\[1\]="Jan",l\[2\]="Feb",l\[3\]="Mar",l\[4\]="Apr",l\[5\]="May",l\[6\]="Jun",l\[7\]="Jul",l\[8\]="Aug",l\[9\]="Sep",l\[10\]="Oct",l\[11\]="Nov",l\[12\]="Dec","content"in r)var m=r.content.$t;else if("summary"in r)var m=r.summary.$t;else var m="";var w=/<\\S\[^>\]\*>/g;if(m=m.replace(w,""),document.write('<div class="rctitle">'),standardstyling&&document.write("<br/>"),document.write(i),1==showpostdate&&document.write(" - "+l\[parseInt(o,10)\]+" "+c+" "+u),document.write('</div><div class="rcsumm">'),1==showpostsummary)if(standardstyling&&document.write(""),m.length<numchars)standardstyling&&document.write("<i>"),document.write(m),standardstyling&&document.write("</i>");else{standardstyling&&document.write(""),m=m.substring(0,numchars);var g=m.lastIndexOf(" ");m=m.substring(0,g),document.write(m+a),standardstyling&&document.write("")}document.write("</div>"),standardstyling&&document.write("")}standardstyling||document.write('<div class="bbwidgetfooter">'),standardstyling&&document.write(""),document.write(""),standardstyling||document.write("")}<br />  
> <br />var numposts = <span style="color: red;"><b>5</b></span>;var showpostdate = <span style="color: red;"><b>true</b></span>;var showpostsummary = true;var numchars = <span style="color: red;"><b>100</b></span>;var standardstyling = true;<br />  
> http://blog-address.blogspot.com</span>/feeds/posts/default?orderby=published&alt=json-in-script&callback=showrecentposts"><br />
> 
> [Recent Posts Widget]( )  
> 
> Your browser does non back upward JavaScript!
> 
>   
> <br />.rctitle a{color:<span style="color: blue;">#000000</span>;text-transform:capitalize;font-size:<span style="color: #a64d79;"><b>13px</b></span>;}#hlrpsa {color: <span style="color: #38761d;"><b>#999999</b></span>; font-size: <span style="color: orange;"><b>12px</b></span>;}.rcsumm {border-bottom:1px dotted #cccccc; padding-bottom:10px;margin-top:5px;}<br />

  

### Recent Posts Widget Showing Post Titles Only

>   
> <br />function showrecentposts(t){for(var e=0;e<numposts;e++){var n,r=t.feed.entry\[e\],i=r.title.$t;if(e==t.feed.entry.length)break;for(var d=0;d<r.link.length;d++)if("alternate"==r.link\[d\].rel){n=r.link\[d\].href;break}i=i.link(n);var s=r.published.$t,a=s.substring(0,4),o=s.substring(5,7),l=s.substring(8,10),u=new Array;u\[1\]="Jan",u\[2\]="Feb",u\[3\]="Mar",u\[4\]="Apr",u\[5\]="May",u\[6\]="Jun",u\[7\]="Jul",u\[8\]="Aug",u\[9\]="Sep",u\[10\]="Oct",u\[11\]="Nov",u\[12\]="Dec",standardstyling||document.write(""),document.write('<div class="rctitles2">'),standardstyling&&document.write(""),document.write(i),standardstyling&&document.write(""),1==showpostdate&&document.write(" - "+l+" "+u\[parseInt(o,10)\]+" "+a),standardstyling||document.write("</div>"),document.write("</div>"),standardstyling&&document.write("")}standardstyling||document.write('<div class="bbwidgetfooter">'),standardstyling&&document.write(""),document.write(""),standardstyling||document.write("/div")}<br />  
> var numposts = <span style="color: red;"><b>10</b></span>;var showpostdate = <span style="color: red;"><b>false</b></span>;var standardstyling = true;  
> http://blog-address.blogspot.com</span>/feeds/posts/default?orderby=published&alt=json-in-script&callback=showrecentposts">
> 
> [Recent Posts Widget]( )  
> 
> Oops! Make certain JavaScript is enabled inwards your browser.
> 
>   
> <br />#hlrpsb a {color: <span style="color: blue;">#000000</span>;font-size:<span style="color: #a64d79;"><b>13px</b></span>;text-transform:capitalize;}.rctitles2 {padding-bottom:10px;margin-bottom:10px;border-bottom: 1px dotted #cccccc;}<br />

  

#### How to customize the recent posts widget:

*   To ready how many posts to display, modify the 5 value for the recent posts widget amongst snippets in addition to the 10 for the recent posts widget amongst postal service titles only.
*   If y'all desire to display the postal service dates, modify "false" to "true".
*   The recent posts widget amongst summary volition display 100 characters; if y'all desire about characters, modify the "100" value.
*   To modify the color of the links, modify the values inwards blueish in addition to for the font size, the values violet.
*   To modify the color of the posts snippets modify the values inwards greenish in addition to the values inwards orangish for the font size.
*   Replace the http://blog-address.blogspot.com text amongst your URL.

4\. Save your widget... in addition to that's it. Enjoy!