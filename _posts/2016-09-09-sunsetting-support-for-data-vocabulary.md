---
title: 'Sunsetting support for data-vocabulary'
date: 2020-01-21T11:07:00+01:00
draft: false
---

Structured data schemas such as [schema.org](http://schema.org/) and [data-vocabulary.org](http://data-vocabulary.org/) are used to define shared meaningful structures for markup-based applications on the Web. With the increasing usage and popularity of schema.org we decided to focus our development on a single SD scheme. As of April 6, 2020, data-vocabulary.org markup will no longer be eligible for [Google rich result features](https://developers.google.com/search/docs/guides/search-gallery).  
  
As a preparation for the change and starting today, Search Console will issue warnings for pages using the data-vocabulary.org schema so that you can prepare for the sunset in time. This will allow you to easily identify pages using that markup and replace the data-vocabulary.org markup with schema.org.  

A bit more about structured data
--------------------------------

Google uses [structured data](https://developers.google.com/search/docs/guides/intro-structured-data) standardized formats and shared schemas to provide information about a page and the things described by the page. This information is used for two main purposes  

1.  Understand the content of the page 
    
2.  Enable special search result features and enhancements
    

What are structured data formats?
---------------------------------

Structured data formats like JSON-LD, RDFa and Microdata define a small number of fixed structures that can be used to encode descriptive data. They typically build upon lower-level standards like JSON and HTML. To learn more about the supported and recommended formats, please check out our [developers guide](https://developers.google.com/search/docs/guides/intro-structured-data#structured-data-format).  

What are structured data schemas?
---------------------------------

Alongside the structured data formats, structured data schemas work like a kind of dictionary, defining terms for types of thing (e.g. "Person", "Event", "Organization"), and for properties and relationships (e.g. "name", "worksFor"). By maintaining this separation between format and schema, it is possible for users of different formats to take advantage of the same, widely shared, schemas.  

Data-vocabulary schema
----------------------

Google's "Data Vocabulary" project was an important milestone in the development of structured data on the Web, because it led to our collaboration with other search engines to create schema.org. However it is now very outdated and it is generally preferable to use more widely shared vocabulary from Schema.org. Therefore data-vocabulary.org markup will stop being eligible for Google search result features and enhancements.  
  
Please note that this is the only consequence of this change. Pages using data-vocabulary schema will remain valid for all other purposes.  
  
In order to be eligible for Google rich result features we recommend converting your data-vocabulary.org structured data to schema.org.  
  
For example, here is how you would change the data vocabulary to schema.org  

#### Data-vocabulary.org

[![](https://1.bp.blogspot.com/-Evqfp5OvXt4/XibNP487ZHI/AAAAAAAAD4k/xuoR555onXMURDNC1UpRnrjNBifdLRUOACLcBGAsYHQ/s640/data-vocabulary-markup.jpg)](https://1.bp.blogspot.com/-Evqfp5OvXt4/XibNP487ZHI/AAAAAAAAD4k/xuoR555onXMURDNC1UpRnrjNBifdLRUOACLcBGAsYHQ/s1600/data-vocabulary-markup.jpg)

  

#### Schema.org

[![](https://1.bp.blogspot.com/-NLxeSZjQWqE/XibKeraOuqI/AAAAAAAAD4U/l0y-P4BYAng0hsc0HIvkLBo7FL_hqkjWgCLcBGAsYHQ/s640/schema-markup.jpg)](https://1.bp.blogspot.com/-NLxeSZjQWqE/XibKeraOuqI/AAAAAAAAD4U/l0y-P4BYAng0hsc0HIvkLBo7FL_hqkjWgCLcBGAsYHQ/s1600/schema-markup.jpg)

  
You can test any code snippet live on [Rich Results Test](https://search.google.com/test/rich-results) by pasting it into the search box. Try it out! And if you have any questions or comments, check out the [Google Webmasters community](https://support.google.com/webmasters/threads?hl=en&thread_filter=(category:structured_data)).  
  
_Posted by Dan Brickley, Standards Developer Advocate, and Moshe Samet, Search Console Product Manager_