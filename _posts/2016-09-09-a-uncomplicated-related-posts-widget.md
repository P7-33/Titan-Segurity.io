---
title: 'A Uncomplicated Related Posts Widget For Blogger'
date: 2020-02-15T06:39:00+01:00
draft: false
---

In the final tutorial, nosotros wrote most [how to add together the Related Posts widget amongst thumbnails inward Blogger](https://rdbrry.blogspot.com//search?q=how-to-add-related-posts-widget-to) to display related posts from the same category based on the given labels, which would look only at the terminate of your weblog posts. However, perhaps to a greater extent than or less of yous may prefer a elementary version of this related posts widget to display alone the posts titles.  
  
If yous desire to add together it, follow the side past times side steps below:  
  

![how to add together the Related Posts widget amongst thumbnails inward Blogger Influenza A virus subtype H5N1 Simple Related Posts Widget For Blogger](https://3.bp.blogspot.com/-xWsAasUTMuc/U9rIlC_EmtI/AAAAAAAAJxk/EVU6RgBnrQU/s1600/simple-related-posts-titles-for-blogger.png "A Simple Related Posts Widget For Blogger")

  
  

How to add together Related Posts Widget to Blogger
---------------------------------------------------

Step 1. Go to 'Template' together with hitting the 'Edit HTML' button.  
  
Step 2. Once the template editor opens, click anywhere within the code expanse together with press the CTRL + F keys, together with then type the next tag within the search box (hit Enter to abide by it):  

Step 3. Just to a higher house the tag, glue the next CSS code:  

> <br /> #related-posts {<br /> margin: 15px 0px;<br /> }<br /> #related-posts h2 {<br /> font-size: <span style="color: red;">27</span>px;<br /> font-weight: normal;<br /> color:<span style="color: red;"> #fff</span>;<br /> text-shadow: 1px 0px 2px #888;<br /> margin-bottom: 0.75em;<br /> }<br /> #related-posts a {<br /> font-size: 13px;<br /> color: <span style="color: #6aa84f;">#949494</span>;<br /> text-transform: capitalize;<br /> border-bottom:1px dotted #E2E2E2;<br /> display:block;<br /> padding:13px;<br /> text-decoration: none;<br /> }<br /> #related-posts a:hover {<br /> color: #555;<br /> background: <span style="color: red;">#F4F4F4</span>;<br /> }<br /> #related-posts ul {<br /> padding: 0px;<br /> list-style-type: none;<br /> background: <span style="color: red;">#f9f9f9</span>;<br /> border-left: 5px company #f2f2f2;<br /> }<br /> #related-posts li {<br /> padding: 0px;<br /> }<br />  
> <br /> var relatedpoststitle="Related Posts";<br />  
> <br /> //<!\[CDATA\[<br /> var relatedTitles=new Array();var relatedTitlesNum=0;var relatedUrls=new Array();function related\_results\_labels(json){for(var i=0;i<json.feed.entry.length;i++){var entry=json.feed.entry\[i\];relatedTitles\[relatedTitlesNum\]=entry.title.$t;for(var k=0;k<entry.link.length;k++){if(entry.link\[k\].rel=='alternate'){relatedUrls\[relatedTitlesNum\]=entry.link\[k\].href;relatedTitlesNum++;break}}}}function removeRelatedDuplicates(){var tmp=new Array(0);var tmp2=new Array(0);for(var i=0;i<relatedUrls.length;i++){if(!contains(tmp,relatedUrls\[i\])){tmp.length+=1;tmp\[tmp.length-1\]=relatedUrls\[i\];tmp2.length+=1;tmp2\[tmp2.length-1\]=relatedTitles\[i\]}}relatedTitles=tmp2;relatedUrls=tmp}function contains(a,e){for(var j=0;j<a.length;j++){if(a\[j\]==e){return true}};return false}function printRelatedLabels(currenturl){for(var i=0;i<relatedUrls.length;i++){if(relatedUrls\[i\]==currenturl){relatedUrls.splice(i,1);relatedTitles.splice(i,1)}}var r=Math.floor((relatedTitles.length-1)\*Math.random());var i=0;if(relatedTitles.length>1){document.write('<h2>'+relatedpoststitle+'</h2>')}document.write('<ul>');while(i<relatedTitles.length&&i<20&&i<maxresults){document.write('<li><a href="'+relatedUrls\[r\]+'">'+relatedTitles\[r\]+'</a></li>');if(r<relatedTitles.length-1){r++}else{r=0}i++}document.write('</ul>');relatedUrls.splice(0,relatedUrls.length);relatedTitles.splice(0,relatedTitles.length);}<br /> //\]\]><br />

  

### Customizing Simple Related Posts widget for Blogger

\- To modify the size (27px) together with color (#fff) of 'Related Posts' title, modify the values inward red.  
\- For the related ship service link color, supercede the #949494 value inward green.  
\- To modify the background color, supercede the #f9f9f9 hex color inward red.  
\- For the background color on mouseover, modify the #F4F4F4 value inward red.  
  
Note: You tin ship away utilisation this [Color code generator](https://rdbrry.blogspot.com//search?q=how-to-add-related-posts-widget-to) to choice your favourite color.  
  
Step 4. Now that nosotros added the script to brand the related posts work, nosotros postulate to add together the code that volition display it at the terminate of our weblog posts. Find the trouble below:  

Step 5. Once yous institute it, yous postulate to click the sideways arrow that volition expand the code. Scroll downward until yous abide by the tag - run into the screenshot for to a greater extent than info:  
  
![](https://3.bp.blogspot.com/-mHLx2gzbK_w/U2080khO0lI/AAAAAAAAJBA/W_pLHwDKUUw/s640/how-to-add-related-posts-widget-to-blogger.png)  
  
Step 6. Just to a higher house the tag, glue the code below:  

>   </b:if></b:loop><br /> <script type='text/javascript'> var<b> maxresults=5</b>; removeRelatedDuplicates(); printRelatedLabels("<data:post.url/>"); [Simple Related Posts Widget]( )

Note: To change the let on of maximum related posts for each label, modify the "5" value from **max-results=5**  
  
Step 7. Save the changes past times clicking the 'Save Template' push together with view your blog. Now, become to whatever of your posts to run into this elementary related posts widget for Blogger inward action.