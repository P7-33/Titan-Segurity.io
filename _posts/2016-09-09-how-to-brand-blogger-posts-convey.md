---
title: 'How To Brand The Blogger Posts Convey A Calendar For The Engagement In'
date: 2020-01-11T06:39:00+01:00
draft: false
---

It's quite mutual to come across calendar agency dates adjacent to simply about WordPress posts but for the Blogger platform it isn't ever slow adding it. But who said you lot can't utilization it? You involve to expect no farther than this blog. In this tutorial, we'll larn how to utilization a calendar agency for your Blogger posts date!  
  

[![](http://4.bp.blogspot.com/-H-MSSyx63sg/UBTDuepMzJI/AAAAAAAACbM/cqLy0kgdk8A/s200/Creating-calendar-style-dates-for-your-Blogger-blog-posts-3.png)](http://4.bp.blogspot.com/-H-MSSyx63sg/UBTDuepMzJI/AAAAAAAACbM/cqLy0kgdk8A/s1600/Creating-calendar-style-dates-for-your-Blogger-blog-posts-3.png)

  
[**DEMO**](https://rdbrry.blogspot.com//search?q=demo-post1)

  

How to utilization calendar agency dates inwards Blogger
--------------------------------------------------------

  
  
**Step 1.** Go to "Settings" > "Language as well as Formatting" - "Date Header Format" as well as change the engagement format every bit you lot tin dismiss come across inwards this instance below (first add together day, calendar month as well as lastly year)  
  

[![](http://1.bp.blogspot.com/-j6rS3MgbGKc/UBS4DYwx50I/AAAAAAAACac/6wO6ZWSydo4/s400/Creating-calendar-style-dates-for-your-Blogger-blog-posts-1.png)](http://1.bp.blogspot.com/-j6rS3MgbGKc/UBS4DYwx50I/AAAAAAAACac/6wO6ZWSydo4/s1600/Creating-calendar-style-dates-for-your-Blogger-blog-posts-1.png)

  
**Step 2.** Go to Template > click the "Edit HTML" button  
  

[![](http://1.bp.blogspot.com/-9PJxe92QMdU/UTOPNGadxaI/AAAAAAAAC5Y/FvfeI-b1ymo/s400/blogger-template-edit-html.png)](http://1.bp.blogspot.com/-9PJxe92QMdU/UTOPNGadxaI/AAAAAAAAC5Y/FvfeI-b1ymo/s1600/blogger-template-edit-html.png)

  
**Step 3.** Click anywhere within the code surface area as well as press CTRL + F to opened upward the blogger' search box  

[![](http://1.bp.blogspot.com/-5nCDW329k6I/Us9kWq0wcqI/AAAAAAAAF1I/PIe9SpIdtjc/s1600/blogger-template-search-box.png)](http://1.bp.blogspot.com/-5nCDW329k6I/Us9kWq0wcqI/AAAAAAAAF1I/PIe9SpIdtjc/s1600/blogger-template-search-box.png)

  
**Step 4.** Type or glue the next trouble within the search box as well as hitting Enter to notice it:  

**Step 5.** In instance you lot notice it twice, supplant it twice amongst this code:  

>   
> changeDate('<data:post.dateHeader/>');  
> 
>   
>   
> 
>   
> changeDate('');  

**Step 6.** Now type this tag within the search box as well as hitting Enter to notice it:  

**Step 7.** Just inwards a higher house the tag, glue this code:  

> <br /> //<!\[CDATA\[<br /> var DateCalendar;<br /> component division changeDate(d){<br /> if (d == "") {<br /> d = DateCalendar;<br /> }<br /> var da = d.split(' ');<br /> twenty-four hr menstruation = "<strong class='date\_day'>"+da\[0\]+"</strong>";<br /> calendar month = "<strong class='date\_month'>"+da\[1\].slice(0,3)+"</strong>";<br /> twelvemonth = "<strong class='date\_year'>"+da\[2\]+"</strong>";<br /> document.write(month+day+year);<br /> DateCalendar = d;<br /> }<br /> //\]\]><br />  
>   
> <br /> /\* Calendar agency date<br /> ----------------------------------------------- \*/<br /> #Date {<br /> background: transparent url(<span style="color: blue;">http://1.bp.blogspot.com/-NVj6tUKJgLo/UBShW2dCLSI/AAAAAAAACZk/3TkTa8Hzqt0/s1600/calendar07.png</span>) no-repeat;<br /> display: block;<br /> width:60px;<br /> height:60px;<br /> float: left;<br /> margin: 15px 2px -40px <span style="color: red;">-108</span>px;<br /> padding: 0 0 8px 0px;<br /> border: 0;<br /> text-transform: uppercase;<br /> }<br /> .date\_month {<br /> display: block;<br /> font-size: 15px;<br /> font-weight:bold;<br /> margin-top:-1px;<br /> text-align:center;<br /> color:#ffffff; <span style="color: #6aa84f;">/\* Month's color \*/</span><br /> }<br /> .date\_day {<br /> display: block;<br /> font-size: 28px;<br /> font-weight:bold;<br /> margin-top:-8px;<br /> text-align:center;<br /> color:#282828; <span style="color: #6aa84f;">/\* Day's color \*/</span><br /> }<br /> .date\_year {<br /> display: block;<br /> font-size: 10px;<br /> margin-top:-8px;<br /> text-align:center;<br /> color:#282828; <span style="color: #6aa84f;">/\* Year's color \*/</span><br /> }<br />  

Before saving the Template, hither nosotros tin dismiss brand simply about changes:  
  
\- To modify the calendar style, supplant the url inwards bluish amongst yours;  
\- If the calendar doesn't appear every bit it should, modify **\-108** amongst 0;  
\- With light-green are marked the areas where you lot tin dismiss modify the color of the dates  
  
**Step 8.** Now Preview your Template as well as if everything looks ok, hitting the **Save Template** button.  
  
That was all... Enjoy!