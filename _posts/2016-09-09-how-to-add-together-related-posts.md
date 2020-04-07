---
title: 'How To Add Together Related Posts Widget To Blogger Amongst Thumbnails'
date: 2020-02-16T06:39:00+01:00
draft: false
---

Now hither is a wonderful hack for displaying related posts beneath each of your spider web log posts along amongst ship service thumbnails. The related posts are picked from other posts having same category/label/tag. With this hack many of your readers volition rest on your site for longer periods of fourth dimension when they run across [related posts](https://rdbrry.blogspot.com//search?q=new-related-posts-widget-for-blogger) of interest.  
  

![Now hither is a wonderful hack for displaying related posts beneath each of your spider web log posts  How To Add Related Posts Widget To Blogger amongst Thumbnails](https://3.bp.blogspot.com/-q4p2PCdrG54/UF-DxElBWmI/AAAAAAAACmc/p-ghC0hQtHA/s1600/related-posts-blogger.png "How To Add Related Posts Widget To Blogger amongst Thumbnails")

Adding the Related Posts Widget to Blogger/Blogspot
---------------------------------------------------

Step 1. Log inwards to your [Blogger account](http://www.blogger.com/home) in addition to become to Template > Edit HTML  
  

![Now hither is a wonderful hack for displaying related posts beneath each of your spider web log posts  How To Add Related Posts Widget To Blogger amongst Thumbnails](https://3.bp.blogspot.com/-rP7Xdxqm5W0/UaJpKUUs7pI/AAAAAAAADfc/NP9sNObx2l4/s320/blogger_blogspot_template_edit_html_tutorial.png "How To Add Related Posts Widget To Blogger amongst Thumbnails")

  
Step 2. Click anywhere within the code surface area in addition to press the CTRL + F keys:  
  

![Now hither is a wonderful hack for displaying related posts beneath each of your spider web log posts  How To Add Related Posts Widget To Blogger amongst Thumbnails](https://4.bp.blogspot.com/-pNjafQlLYFU/U69TmT3-feI/AAAAAAAAJZQ/BRdO0NS6vvc/s1600/open-blogger-search-box-ctrl%252Bf.png "How To Add Related Posts Widget To Blogger amongst Thumbnails")

  
Step 3. Search for this tag that yous request to add together within the search box (hit Enter to honor it):  

Step 4. Copy in addition to glue the below code simply before/above the tag:  

>   
>   
> <br /> #related-posts{float:left;width:auto;}<br /> #related-posts a{border-right: 1px dotted #eaeaea;}<br /> #related-posts h4{margin-top: 10px;background:none;font:18px Oswald;padding:3px;color:#999999; text-transform:uppercase;}<br /> #related-posts .related\_img {margin:5px;border:2px venture #f2f2f2;object-fit: cover;width:<span style="color: red;"><b>110px</b></span>;<span style="color: red;"><b>height:100px;</b></span>-webkit-border-radius: 5px;-moz-border-radius: 5px; border-radius: 5px; }<br /> #related-title {<span style="color: #3d85c6;"><b>color:#333</b></span>;text-align:center;text-transform:capitalize;padding: 0px 5px 10px;font-size:12px;<span style="color: red;"><b>width:110px</b></span>; height: 40px;}<br />  
> <br /> //<!\[CDATA\[<br /> var relatedTitles=new Array();var relatedTitlesNum=0;var relatedUrls=new Array();var thumburl=new Array();function related\_results\_labels\_thumbs(json){for(var i=0;i<json.feed.entry.length;i++){var entry=json.feed.entry\[i\];relatedTitles\[relatedTitlesNum\]=entry.title.$t;try{thumburl\[relatedTitlesNum\]=entry.gform\_foot.url}catch(error){s=entry.content.$t;a=s.indexOf("<img");b=s.indexOf("src=\\"",a);c=s.indexOf("\\"",b+5);d=s.substr(b+5,c-b-5);if((a!=-1)&&(b!=-1)&&(c!=-1)&&(d!="")){thumburl\[relatedTitlesNum\]=d}else thumburl\[relatedTitlesNum\]='http://2.bp.blogspot.com/-ex3V86fj4dQ/UrCQQa4cLsI/AAAAAAAAFdA/j2FCTmGOrog/s1600/no-thumbnail.png'}if(relatedTitles\[relatedTitlesNum\].length>35)relatedTitles\[relatedTitlesNum\]=relatedTitles\[relatedTitlesNum\].substring(0,35)+"...";for(var k=0;k<entry.link.length;k++){if(entry.link\[k\].rel=='alternate'){relatedUrls\[relatedTitlesNum\]=entry.link\[k\].href;relatedTitlesNum++}}}}function removeRelatedDuplicates\_thumbs(){var tmp=new Array(0);var tmp2=new Array(0);var tmp3=new Array(0);for(var i=0;i<relatedUrls.length;i++){if(!contains\_thumbs(tmp,relatedUrls\[i\])){tmp.length+=1;tmp\[tmp.length-1\]=relatedUrls\[i\];tmp2.length+=1;tmp3.length+=1;tmp2\[tmp2.length-1\]=relatedTitles\[i\];tmp3\[tmp3.length-1\]=thumburl\[i\]}}relatedTitles=tmp2;relatedUrls=tmp;thumburl=tmp3}function contains\_thumbs(a,e){for(var j=0;j<a.length;j++)if(a\[j\]==e)return true;return false}function printRelatedLabels\_thumbs(){for(var i=0;i<relatedUrls.length;i++){if((relatedUrls\[i\]==currentposturl)||(!(relatedTitles\[i\]))){relatedUrls.splice(i,1);relatedTitles.splice(i,1);thumburl.splice(i,1);i--}}var r=Math.floor((relatedTitles.length-1)\*Math.random());var i=0;if(relatedTitles.length>0)document.write('<h4>'+relatedpoststitle+'</h4>');document.write('<div style="clear: both;"/>');while(i<relatedTitles.length&&i<20&&i<maxresults){document.write('<a style="text-decoration:none;margin:0 4px 10px 0;float:left;');if(i!=0)document.write('"');else document.write('"');document.write(' href="'+relatedUrls\[r\]+'"><img class="related\_img" src="'+thumburl\[r\]+'"/><br/><div id="related-title">'+relatedTitles\[r\]+'</div></a>');if(r<relatedTitles.length-1){r++}else{r=0}i++}document.write('</div>');relatedUrls.splice(0,relatedUrls.length);thumburl.splice(0,thumburl.length);relatedTitles.splice(0,relatedTitles.length)}<br /> //\]\]><br />  
>   

  
Note:  
\- to alter the width in addition to tiptop of thumbnails, modify the **110**px in addition to **100**px values inwards red  
\- to alter the color in addition to size of related posts titles, alter the #333 color value inwards blue  
\- take the trouble in violet if yous desire the related posts to last displayed both inwards homepage in addition to ship service pages.  
  
Step 5. Find the trouble below (you volition honor ii times, but yous request to terminate at the minute one):  

Step 6. Just higher upwards

glue this code:  

>   
>   
> 
>   
>   
>   
>   
> </b:loop><br /> <script type='text/javascript'><br /> var currentposturl="<data:post.url/>";<br /> var <b>maxresults=<span style="color: red;">5</span></b>;<br /> var relatedpoststitle="<b><span style="color: #3d85c6;">Related Posts:</span></b>";<br /> removeRelatedDuplicates\_thumbs();<br /> printRelatedLabels\_thumbs();<br />  
> 
> Related Posts Widget
> 
>   
>   

_**Note:**_  
\- alter the **5** value from **max-results=5** with the release of posts yous desire to last displayed  
\- if yous desire the related posts to last displayed on homepage too, thence take the b:if lines in violet  
  
**Update! If yous are unable to run across the related posts widget afterwards saving the template, add together the code (step 5) simply higher upwards the tag that yous tin honor higher upwards this line:**  

To larn an sentiment of the exact location, run across the screenshot below:  
  

![](https://3.bp.blogspot.com/-mHLx2gzbK_w/U2080khO0lI/AAAAAAAAJBA/W_pLHwDKUUw/s1600/how-to-add-related-posts-widget-to-blogger.png)

  
Step 7. Save the Template in addition to that's it. Now the Related Posts widget amongst Thumbnails should look below each Blogger ship service that has labels on it. Enjoy!