---
title: 'New reports for review snippets in Search Console'
date: 2020-02-10T18:36:00+01:00
draft: false
---

A [review snippet](https://developers.google.com/search/docs/data-types/review-snippet) is a short excerpt of a review or a rating from a website, usually an average of the combined rating scores from many reviewers. This is one of the most used structured data types on the web, used by millions of web sites for many content types such as [Book](https://schema.org/Book), [Movie](https://schema.org/Movie), [Event](https://schema.org/Event), [Product](https://schema.org/Product) and more.  
  
When Google finds valid reviews or ratings markup, we may show a rich result that includes stars and other summary info. This rich result can appear directly on search results or as part of a Google Knowledge panel, as shown in the screenshots below.  
  
Today we are announcing support for review snippets in [Google Search Console](https://search.google.com/search-console), including new reports to help you find any issues with your implementation and monitor how this rich result type is improving your performance. You can also use the [Rich Results Test](https://search.google.com/test/rich-results) to review your existing URLs or debug your markup code before moving it to production.  
  

[![](https://1.bp.blogspot.com/-sgVbWH071Ho/XkGErZVL_eI/AAAAAAAAD58/kVJG6Y8nKsAqyzUa5bWo0LQQy73d9LZCQCLcBGAsYHQ/s640/reviews-snippet.png)](https://1.bp.blogspot.com/-sgVbWH071Ho/XkGErZVL_eI/AAAAAAAAD58/kVJG6Y8nKsAqyzUa5bWo0LQQy73d9LZCQCLcBGAsYHQ/s1600/reviews-snippet.png)

  

Review snippet Enhancement report
---------------------------------

To help site owners make the most of their reviews, a new review snippet report is now available in Search Console for sites that have implemented reviews or ratings [structured data](https://developers.google.com/search/docs/data-types/review-snippet#structured-data-type-definitions). The report allows you to see errors, warnings, and valid pages for markup implemented on your site.  
  
In addition, if you fix an issue, you can use the report to validate it, which will trigger a process where Google recrawls your affected pages. The report is covering all the content types currently supported as review snippets. Learn more about the [Rich result status reports](https://support.google.com/webmasters/answer/7552505).  
  

[![](https://1.bp.blogspot.com/-KpWAaIZ1Hrc/XkGFlDYMKXI/AAAAAAAAD6E/7GSz6jcfBaMVphtG4SlVJ0znKNJ_YVaVACLcBGAsYHQ/s640/reviews-snippet-enhancement.png)](https://1.bp.blogspot.com/-KpWAaIZ1Hrc/XkGFlDYMKXI/AAAAAAAAD6E/7GSz6jcfBaMVphtG4SlVJ0znKNJ_YVaVACLcBGAsYHQ/s1600/reviews-snippet-enhancement.png)

  

Review snippet appearance in Performance report
-----------------------------------------------

The Search Console [Performance report](https://support.google.com/webmasters/answer/7576553) now allows you to see the performance of your review or rating marked-up pages on Google Search and Discover using the new “Review snippet” search appearance filter.  
  

[![](https://1.bp.blogspot.com/-ZmlbfAXV5W0/XkGGr9BFd3I/AAAAAAAAD6Q/2-j1-yHRbNkyiCvd1K6fk_iU03nFT_ZFACLcBGAsYHQ/s640/reviews-snippet-performance.png)](https://1.bp.blogspot.com/-ZmlbfAXV5W0/XkGGr9BFd3I/AAAAAAAAD6Q/2-j1-yHRbNkyiCvd1K6fk_iU03nFT_ZFACLcBGAsYHQ/s1600/reviews-snippet-performance.png)

  
  
This means that you can check the impressions, clicks and CTR results of your review snippet pages and check their performance to understand how they are trending for any of the dimensions available. For example you can [filter your data](https://support.google.com/webmasters/answer/7576553#filteringdata) to see which queries, pages, countries and devices are bringing your review snippets traffic.  

Review snippet in Rich Results Test
-----------------------------------

[![](https://1.bp.blogspot.com/-cYLHBM0WjE4/XkGR3z8s1tI/AAAAAAAAD6g/StrQUg74NMcfMX8f2kZ-6vQ05lcTCWy3ACLcBGAsYHQ/s640/rich-results-test.png)](https://1.bp.blogspot.com/-cYLHBM0WjE4/XkGR3z8s1tI/AAAAAAAAD6g/StrQUg74NMcfMX8f2kZ-6vQ05lcTCWy3ACLcBGAsYHQ/s1600/rich-results-test.png)

  
  

After adding Review snippets structured data to your pages, you can test them using the [Rich Results Test tool](https://search.google.com/test/rich-results). You can test a code snippet or submit a URL of a page. The test shows any errors or suggestions for your structured data.  
  

These new tools should make it easier to understand how your marked-up review snippet pages perform on Search and to identify and fix review issues.  
  
If you have any questions, check out the [Google Webmasters community](https://support.google.com/webmasters/threads?hl=en&thread_filter=(category:search_console)).  
  
_Posted by Tomer Hodadi and Yuval Kurtser, Search Console engineering team_