---
title: 'How To Shroud Blogger Sidebar To Display Adsense For Search Results'
date: 2020-01-20T06:39:00+01:00
draft: false
---

When visitors are searching for content on your blog, you lot possess got 3 options to display the search results: opening the results inwards the same window, inwards a novel window or within your ain site using an iframe.  
  
The best selection would be, however, to display the search results within your ain site/blog, mainly because you lot are non sending people off your spider web log when they are taken to a novel page of search results which could live confusing for many because it doesn't await anything similar your site or Google. Therefore, displaying the search results within your site, could larn inwards await much to a greater extent than professional person in addition to may too increase the page views in addition to the revenue from the ads on the search page.  
  
Influenza A virus subtype H5N1 work that many bloggers are facing is that the page which displays the AdSense for search results must live at to the lowest degree of 800 px wide, thus the posting surface area must live of minimum 800px in addition to there's zilch similar this inwards nearly of the blogs.  
So, what nosotros volition practice inwards this tutorial is to develop the search results to live displayed inwards a static page (none of other posts or pages volition live affected) inwards which we'll take the sidebar thus that we'll possess got plenty infinite to brand the post/page department of 800px wide. Moreover, nosotros volition [create a static page](https://rdbrry.blogspot.com//search?q=how-to-create-static-pages-in-blogger) designed solely for the search results, in addition to thus practice a novel AdSense for search inwards our AdSense concern human relationship in addition to live add together a small-scale snippet of code move on inwards your Blogger template to shroud the sidebar inwards that specific page.  
  
_Search results bridge the width of the page amongst the sidebar hidden:_  
  

[![](http://2.bp.blogspot.com/-mkHxxOmhYKc/UTEbIGKv78I/AAAAAAAAC3Q/0avTg4Mfi6M/s1600/HOW-TO-HIDE-REMOVE-SIDEBAR-FOR-ADSENSE-SEARCH-RESULTS.png)](http://2.bp.blogspot.com/-mkHxxOmhYKc/UTEbIGKv78I/AAAAAAAAC3Q/0avTg4Mfi6M/s1600/HOW-TO-HIDE-REMOVE-SIDEBAR-FOR-ADSENSE-SEARCH-RESULTS.png)

  
**Display AdSense For Search Results Within Blogger Page**  
  
**Step 1.** Create a novel static page on your blog, you lot tin sack laissez passer on it the championship 'Search Results' but exit the content department empty in addition to and thus **Publish** the page.  
  
**Step 2.** When you lot issue the page you lot possess got the selection to add together the page to a menu, lead the 3rd selection 'No Gadget Link To Pages Manually' click 'Save in addition to Publish'. In example this concealment doesn't show, correct click on _View Page_ in addition to select _Copy Link Address_. We volition take this URL of the page after when nosotros volition practice the AdSense for search.  
  
**Step 3.** Go To Your AdSense account, in addition to thus larn to **My ads** tab, select the **Search** selection in addition to Create a **New custom search engine**. Follow the steps until you lot come upward to the **Search results** option.  
  
**Step 4.** Select the 3rd method "_on my website using an iframe_", in addition to thus Enter the URL of the page you lot created into the URL plain in addition to continue.  
  

[![](http://1.bp.blogspot.com/-t1Hj-vylG0E/UTEVzbJ7P2I/AAAAAAAAC3A/DVI9QrudX90/s1600/hide-blogger-sidebar-for-adsense-search-results.png)](http://1.bp.blogspot.com/-t1Hj-vylG0E/UTEVzbJ7P2I/AAAAAAAAC3A/DVI9QrudX90/s1600/hide-blogger-sidebar-for-adsense-search-results.png)

  

**Step 5.** Follow the balance of the develop procedure in addition to at the cease you lot volition live given 2 pieces of code. The get-go slice of code is for the actual search bar which you lot tin sack glue into a Html/JavaScript gadget on your sidebar or wherever you lot desire it. The minute slice of code you lot take to re-create in addition to glue it into a novel HTML/JavaScript gadget, click on Save, in addition to thus drag it inwards a higher house the [_**Blog Posts**_](http://4.bp.blogspot.com/-3mhw8qkhn9I/UTEbl2a2yCI/AAAAAAAAC3Y/bPhdDTw07QI/s1600/adsense-search-results-blogger.png) surface area  
  

[![](http://4.bp.blogspot.com/-3mhw8qkhn9I/UTEbl2a2yCI/AAAAAAAAC3Y/bPhdDTw07QI/s1600/adsense-search-results-blogger.png)](http://4.bp.blogspot.com/-3mhw8qkhn9I/UTEbl2a2yCI/AAAAAAAAC3Y/bPhdDTw07QI/s1600/adsense-search-results-blogger.png)

  
Now that you lot possess got your page develop amongst the search results code in addition to your search bar code inwards your sidebar, it is fourth dimension to add together a snippet of code to your template to take the sidebar.  
  
**Adding The Code In Blogger To Change the Results Page Layout**  
  
**Step 1.** From Your Blogger Dashboard, larn to **Template** in addition to click on the **Edit HTML** button  
  

[![](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)](http://2.bp.blogspot.com/-gSc5N-5w_cA/US_icNFtWbI/AAAAAAAAC0M/yu6B_3h-ubg/s1600/remove-blogger-labels.png)

  
**Step 2**. Click anywhere within the code surface area in addition to press the CTRL + F keys to opened upward the Blogger' search box  

[![](http://1.bp.blogspot.com/-5nCDW329k6I/Us9kWq0wcqI/AAAAAAAAF1I/PIe9SpIdtjc/s1600/blogger-template-search-box.png)](http://1.bp.blogspot.com/-5nCDW329k6I/Us9kWq0wcqI/AAAAAAAAF1I/PIe9SpIdtjc/s1600/blogger-template-search-box.png)

  
**Step 3.** Find (CTRL + F) the next slice of code  

> \]\]>

**Step 4.** Just below it, glue this code:  

>   
> <br /> .main-inner .columns {<br /> padding-left: 0px !important;<br /> padding-right: 0px !important;<br /> }<br /> .main-inner .fauxcolumn-center-outer {<br /> left: 0px !important;<br /> right: 0px !important;<br /> }<br /> .main-inner .fauxcolumn-left-outer, .main-inner .fauxcolumn-right-outer, .main-inner .column-left-outer, .main-inner .column-right-outer {<br /> display: none !important;<br /> }<br />  

  
Note: Replace PAGE-URL-HERE amongst the url of the page where the search results volition live displayed (the ane you lot possess got added at the **step 4**)

  

**Step 5.** Now **Save Template** in addition to you're done!  
  
This elementary play a trick on allows you lot non solely to shroud the sidebar inwards the search results page, you lot tin sack every bit well, shroud it on whatever page you lot want... but practice your page in addition to follow the same steps. It is too recommended to shroud the sidebar inwards Privacy Policy Pages, Contact Pages in addition to on all the non-content-based pages amongst petty content or no content at all.