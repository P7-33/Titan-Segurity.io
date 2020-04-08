---
title: 'Lessons Learned Redesigning A SaaS Website With Gutenberg'
date: 2019-10-01T13:14:00+01:00
draft: false
---

The release of WordPress 5.0 in December 2018 was a landmark event for the WordPress world. We all knew the introduction of the Gutenberg editor would change much of how we all build, interact with, and manage our sites.

And overall it has been a very smooth transition.

But while we all know the best practice is to keep our sites up-to-date with the latest and greatest WordPress has to offer, changing the editor is a big step and something that (maybe rightfully) has caused some to slow their adoption of the block editor.

Indeed maybe you shouldn’t rush into taking the leap to rebuild a site for your business or clients in the new block editor environment.

Never one to back down from a challenge, our team at [Castos](https://castos.com/?utm_medium=wpmayor&utm_source=guestpost&utm_campaign=lessons-learned-redesign-a-saas-website-with-gutenberg) embarked upon the redesign of our website earlier this year with Gutenberg in mind.  We learned a LOT along the way and wanted to share much of that newly gained knowledge with you here.

Known Limitations Of The Native Block Editor
--------------------------------------------

While the new editing environment is a vast improvement over previous versions, it may lack some key elements you would like to see on your site. Some of these extensions are not yet available in the native editor or even through third-party block packages.

Third-party block packages do offer a lot of unique choices outside of the core blocks, but beware, some of their settings and features do not work across all blocks. Additionally, if you use several different sets of 3rd party block add-ons you may get different styles and looks on your site that are difficult to standardize.

After working with a few, we opted to use [one primary block package](https://coblocks.com/) that had the most features we were using and played nicely with WordPress core blocks.

Working in this way, we were able to maintain consistency while getting the most functionality.

A theme by any other name
-------------------------

Once you are ready to get started, you’ll need to select a [theme](https://wpmayor.com/gutenberg-ready-wordpress-themes-for-business/). For our design, we moved away from the [Genesis framework](https://wpmayor.com/create-stellar-photography-website-using-genesis-framework-4-steps/) that had served us well for years until now, opting to create a child theme from a Gutenberg-first theme, [Atomic Blocks](https://atomicblocks.com/).

There are many themes that are “Gutenberg” ready, including Genesis, but knowing that the blocks were going to do the heavy-lifting building the site, we opted for a very minimal, lightweight theme that provided only what we needed without a lot of extras that would get in the way.

### **Block considerations for your theme**

You’ll also want to make sure your theme has a wide-open basic page template to work with that takes advantage of the two new alignment options align wide and align full. Check if your theme is set up for

add\_theme\_support( 'align-wide' );

in the functions.php file and be sure to add support for this if it is not present.

Increased Productivity Using Gutenberg
--------------------------------------

There are a few areas working in the new Gutenberg editor that can save you time by allowing you to reuse page elements across your site.

### Reusable Blocks

The new Reusable Block feature is great for content that will not change from page to page, like a call-to-action. You can quickly assemble a group of blocks and save the grouping to use later.

We use this most commonly on what we call our “CTA Block” which is present on our homepage and just above the footer on most pages.

[](https://castos.com?utm_medium=wpmayor&utm_source=guestpost&utm_campaign=lessons-learned-redesign-a-saas-website-with-gutenberg)

### Copying Blocks Between Pages

Likewise, if you put together a great layout for landing page that you know you will want to reuse, you can copy the block layout and save it to a new page by going into the Inspector Controls, switching to the Code Editor view, copying all of the block elements for that page, and pasting them into a new page.

On our site we used this method to bring the format of pages across on many of our specific [feature pages](https://castos.com/features/?utm_medium=wpmayor&utm_source=guestpost&utm_campaign=lessons-learned-redesign-a-saas-website-with-gutenberg). So they all have the same look, feel, and format, and our marketing team is free to edit just the content for each page.

### Block Level CSS Selectors

In a few places, we found the ability to add a custom CSS selector to a block a great way to quickly target an element to make a style change. While not the most concise way of writing CSS, it can be useful in a pinch.

Specifically, we did this to add some shadowing and effects to the Testimonials block that [GhostKit](https://ghostkit.io/) provides.

[![Castos Testimonial block](https://wpmayor.com/wp-content/uploads/2019/08/Castos-Testimonial-block-e1566504064160.png)](https://castos.com?utm_medium=wpmayor&utm_source=guestpost&utm_campaign=lessons-learned-redesign-a-saas-website-with-gutenberg)

Between a block and a hard place
--------------------------------

Our front-end visitors won’t notice the changes going on behind the scenes in the new editor. But these changes have a huge impact on admin users.

Our admin users now have more flexibility, which is a big win. But this comes with a price tag that can mean being overwhelmed by having to make too many design decisions.

For theme and plugin developers, we will need to ensure that the new editing experience remains flexible and easy as intended, while carefully considering the options provided to admin users.

In the Castos redesign experience, we tried to provide guide rails to make creating new pages and posts in the future quick and painless. This included providing a few customizations to the Gutenberg Inspector Controls sidebar like a color palette and limiting block styles.

If your theme is Gutenberg ready, adding a color palette can be quite simple by adding theme support for the editor\-color\-palette. This snippet will do the trick:

PHP

add\_theme\_support( 'editor-color-palette', array( array( 'name' => \_\_( 'independence', 'castos-theme' ), 'slug' => 'independence', 'color' => '#555471', ), array( 'name' => \_\_( 'payne grey', 'castos-theme' ), 'slug' => 'payne grey', 'color' => '#5F5D7E', ), ) );

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

add\_theme\_support(

'editor-color-palette',

array(

array(

'name'\=&gt; \_\_( 'independence', 'castos-theme' ),

'slug'\=&gt; 'independence',

'color' \=&gt; '#555471',

),

array(

'name'\=&gt; \_\_( 'payne grey', 'castos-theme' ),

'slug'\=&gt; 'payne grey',

'color' \=&gt; '#5F5D7E',

),

)

);

Then our admin editor only needs to select the color and not try to remember the HEX value each time a color needs to be set.

If your site has a style guide already created then loading this right into the color picker will mean consistent colors across your site without any room for error.

Taking it one step further
--------------------------

Similarly, you can take this level of customization one step further by extending existing core blocks by using [Block Style Variations](https://developer.wordpress.org/block-editor/developers/filters/block-filters/). This method scores a big win for usability just like the color palette because you add functionality exactly where the admin user expects to find it — within existing block settings.

![](https://wpmayor.com/wp-content/uploads/2019/08/Castos-button-selector-e1566503907929.png)The best place to consider employing this technique is on the button block.

Most block packages and plugins offer their own button version, which quickly adds up to lots of buttons and button styles.

If you’re looking to maintain any type of consistent style on your site, limiting the options here for your admin user is a good idea because it becomes hard to keep track which button to use.

You can also make it easier for your admin by turning off button blocks you will not use. Many of the block packages have this functionality built-in to their block settings in the main dashboard. Eliminating the extraneous options can make it much easier for your admin user when they are creating a new page.

Making the most of Page Templates
---------------------------------

Considering that page building is primarily now done in the editor, page templates are also evolving.

In our redesign we allowed for a new page template that would remove the page title, opening the space to use a Heading Block from our primary header block package.

Reusable blocks in locations like this didn’t work for us because the content of the reusable block needs to be the same. In this instance, you could also code a block template for the admin user to select from that loads the necessary blocks without content so the admin user doesn’t need to reinvent the wheel each time.

This is perhaps the only place in the entire block editor experience we were looking for something we couldn’t easily find: Block Templates.

A “Block Template” would be something similar to a reusable block but where the content is easily changed for each instance where the block is used. We would’ve liked to use it in the secondary feature section in our homepage design.

Here the layout and structure of each of these 3 blocks are the same but all of the content is different.  So something like a Block Template would be ideal to save us time of reinventing the wheel each time we want to create one of these sections.

**In Hindsight**
----------------

Designing and developing a theme in the new block editor is a balancing act between providing the style that determines the look and feel of your site as well as the UI for your admin user to create pages that are consistent for your overall site design.

While the new editor provides an incredibly flexible experience, when considering your redesign using Gutenberg you’ll be much more successful in maintaining a consistent style guide creating a child theme that provides front end style in combination with guide rails that will eliminate design fatigue for the admin.

Overall the entire [Castos team](https://castos.com/our-team?utm_medium=wpmayor&utm_source=guestpost&utm_campaign=lessons-learned-redesign-a-saas-website-with-gutenberg), design, development, and marketing, have all been very happy with the outcome of our site redesign with using a Gutenberg first approach.

A few months after the relaunch we’ve found it particularly nice to be able to create new content that has a very similar, highly styled, look and feel as the existing content on the site.  This style consistency goes a long way towards providing a positive experience for site visitors, and should ultimately mean more conversions and happy customers.

![](https://secure.gravatar.com/avatar/8a66bec60f963fa948899db5af5aba6d?s=100&d=retro&r=g)

### About Craig Hewitt

### Related Articles

*   [Will Gutenberg Editor Make or Break WordPress?](https://wpmayor.com/will-gutenberg-editor-break-wordpress/)
    
    [![](https://wpmayor.com/wp-content/uploads/2017/12/image3.png)](https://wpmayor.com/will-gutenberg-editor-break-wordpress/)
    
    The new and controversial Gutenberg editor is expected to be rolled out together with the release of WordPress version 5.0 this coming 2018. Currently available only as a plugin, Gutenberg is set…
    
*   [Gutenberg Failing Hard - Should We Be Worried?](https://wpmayor.com/gutenberg-failing-hard/)
    
    [![](https://wpmayor.com/wp-content/uploads/2018/09/Gutenberg.jpg)](https://wpmayor.com/gutenberg-failing-hard/)
    
    The latest big innovation to come to WordPress, Gutenberg, appears to be failing hard, at least judging by user reception and reviews on the plugin's profile on WordPress.org. The Gutenberg…
    
*   [Change TinyMCE Editor Class](https://wpmayor.com/change-tinymce-editor-class/)
    
    [![Change TinyMCE Editor Class](https://wpmayor.com/wp-content/uploads/2016/12/wpmayor_logo_final.png)](https://wpmayor.com/change-tinymce-editor-class/)
    
    This hack will change TinyMCE's default class, useful for styling the post editor to look like the front end of your site. This function goes into your theme's functions.php file.
    
*   [How Will Gutenberg Affect WordPress Page Builders?](https://wpmayor.com/how-will-gutenberg-affect-wordpress-page-builders/)
    
    [![](https://wpmayor.com/wp-content/uploads/2018/09/Gutenberg.jpg)](https://wpmayor.com/how-will-gutenberg-affect-wordpress-page-builders/)
    
    Gutenberg has gotten off to a very shaky start, but it seems like it's here to stay. Hopefully, all the kinks will be ironed out over time. The next question…
    

**[Let's block ads!](https://blockads.fivefilters.org)** [(Why?)](https://blockads.fivefilters.org/acceptable.html)