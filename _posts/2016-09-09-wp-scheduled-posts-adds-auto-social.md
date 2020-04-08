---
title: 'WP Scheduled Posts Adds Auto Social Share & More Features (+ Limited
Time Offer)'
date: 2019-11-14T12:10:00+01:00
draft: false
---

A few months back, we [took a look at WP Scheduled Posts](https://wpmayor.com/how-to-manage-your-content-with-wp-scheduled-posts/), a convenient tool that lets you manage all of your WordPress posts from a great-looking calendar view.

It lets you use drag-and-drop to rearrange your content as needed. And you can also create or edit content right from the calendar view.

Since our first post in July, the team behind WP Scheduled Posts has been working on new features, like a social media auto-poster to help you share your content on Facebook and Twitter.

In this post, we’re going to take a fresh look at [WP Scheduled Posts](http://social.appsumo.com/k1syos) with an eye specifically on those new features.

If you like what you see, WP Scheduled Posts has [a great AppSumo deal running](http://social.appsumo.com/k1syos) for a limited time, which is definitely worth checking out. You can get lifetime access for use on up to 5 sites for just $39 or use on limited sites for $117.

WP Scheduled Posts: What the Plugin Does
----------------------------------------

In case you missed [our previous look at WP Scheduled Posts](https://wpmayor.com/how-to-manage-your-content-with-wp-scheduled-posts/), we covered the core features in its initial release:

*   A calendar view dashboard where you can view all your posts and use drag-and-drop to rearrange them.
*   A dashboard widget that lists all of your upcoming posts in the main **Dashboard** area.
*   An auto-scheduling tool to automatically suggest scheduling dates/times based on your preferences. For example, you can say you want “2 posts on Monday between 12 pm and 8 pm” and WP Scheduled Posts will handle it for you in a way that makes sense.
*   A “missed schedule” handler to fix situations where WP cron might make you miss a post’s scheduled time. _Basically, WP cron only fires when you have a visitor. So if you don’t have a visitor around the scheduled time, WordPress won’t be able to publish the post by default_.

All those features are still there. But in this post, we’re going to focus on the “new” stuff, which includes…

*   A complete redesign of the calendar view dashboard. In addition to a new design, the new calendar view also uses a new JavaScript library to power its functionality.
*   Social media auto-posting. You can automatically share new content on Facebook and/or Twitter and configure the template that WP Scheduled Posts uses.
*   The ability to schedule content from multiple post types, which is great if your WordPress site relies on [custom post types](https://wpmayor.com/ultimate-guide-wordpress-custom-post-types/). For example, if you have a WooCommerce store, you can publish products to go live at specific times.
*   A new setup wizard to help you configure all the plugin’s settings.

Let’s take a look at the new features…

A New Helpful Setup Wizard
--------------------------

In the latest version of WP Scheduled Posts, the plugin will launch a getting started wizard as soon as you activate it.

This wizard helps you configure all the important basics for how the plugin functions.

First, you can choose whether or not to display information from the plugin in various areas, like the WordPress toolbar and main dashboard area:

![WP Scheduled Posts Setup wizard](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-1.png)

Next, you can choose which post types the plugin supports. Again, the ability to support multiple post types is a new addition and one that’s really convenient.

For example, depending on how your site is set up, you could use your calendar to manage the schedules for…

*   eCommerce products
*   Events
*   Job posts
*   Coupons
*   Videos
*   Etc.

The real-world applications of this are really neat.

Beyond supporting custom post types, you can also choose which categories to show and which user roles have access to the plugin. For example, you could give your editors access to help them manage your content efforts:

![Choose post types](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-2.png)

Next up, you can choose your preferred scheduling approach from two options:

*   **Auto Scheduler** – enter how many posts you want for each day of the week plus a time range and let WP Scheduled Posts handle the rest. WP Scheduled Posts will automatically suggest schedules that match your preference. For example, you want one post on weekdays between 12 pm and 6 pm.
*   **Manual Scheduler** – enter the specific days and times to publish content. For example, you want a post every single Tuesday at exactly noon.

Here’s what the **Auto Scheduler** looks like. Note how you can enter a unique number of posts for each day and set the time range for when posts can be published:

![Automatic scheduler](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-3.png)

And with the **Manual Scheduler**, you can enter the exact time(s) of day for each day of the week:

![Manual scheduler](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-4.png)

If you go with the **Manual Scheduler**, you can also enable the **Missed Schedule** tool, which helps make sure your content still gets published if WordPress misses the publish date for some reason. _For example, your site not getting a visit to trigger WP Cron._

Finally, you can set up social integration, which I’ll save for its own dedicated section because it’s one of the biggest new features:

![Social media](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-5.png)

And that’s it for the scheduler! Let’s take a look at some other new features.

### A Brand New Calendar View

Recent versions of WP Scheduled Posts offer a brand new calendar view design, rewritten with a new JavaScript library.

It still shows the same information as previous versions, but I think the interface is a little nicer:

![New content calendar](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-6.png)

As before, you can still:

*   See all of your past and upcoming content for the month on the calendar.
*   View a list of unscheduled drafts (_it’s on the left side now_).
*   Use drag-and-drop to rearrange content on the calendar or drag content to/from the unscheduled list.
*   Quickly edit or create content right from the calendar view.

For example, here’s what it looks like to “quick edit” or create a piece of content from the calendar view.

![Edit content](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-7.png)

### Social Media Autoposting on Facebook and Twitter

One of the biggest new features is the ability to automatically share newly-published posts on Facebook or Twitter.

To enable this functionality, you’ll need to create a Facebook and/or Twitter app, which was what you saw in the setup wizard above.

To help you do this, the developer includes detailed documentation for both [Facebook](https://wpdeveloper.net/docs/share-scheduled-posts-facebook/) and [Twitter](https://wpdeveloper.net/docs/share-scheduled-posts-twitter/).

Once you’ve set up your app, you can then go to **Scheduled Posts → Social Templates** to configure the share template for both Facebook and Twitter.

Using variables, you can dynamically include a piece of content’s…

*   Title
*   Content
*   URL
*   Tags

You can also include a piece of content’s category with the tags:

![](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-8.png)

Currently, WP Scheduled Posts shares your content on social media as soon as it’s published.

### Support for Custom Post Types

I showed you this during the setup wizard, but another neat new feature is the ability to schedule content from custom post types.

For example, you can see that I’ve added **Product** as a supported post type at my WooCommerce store:

![post type support](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-9.png)

Now, when I create a new product, WP Scheduled Posts will suggest a schedule date:

![Schedule suggestions](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-10.png)

WP Scheduled Posts will also add a new “Calendar” sub-menu to that custom post type where you can manage the schedule for just that post type.

For example, I can now go to **Products → Calendar** to manage the publishing calendar for just my WooCommerce products:

![Product calendar](https://wpmayor.com/wp-content/uploads/2019/11/wp-scheduled-posts-review-11.png)

Similarly, to manage the calendar for just your blog posts, you could go to **Posts → Calendar** and so on.

Get Started With WP Scheduled Posts Today
-----------------------------------------

As you can see, the WP Scheduled Posts developers haven’t been resting on their laurels and are continuously improving the product.

Overall, it’s a really neat tool that can be helpful for anyone with a busy WordPress site.

The addition of custom post type support also makes WP Scheduled Posts helpful beyond just blogs and I believe there are lots of custom content WordPress sites who could benefit from this.

If you want to get started with WP Scheduled Posts, there’s a limited free version at WordPress.org that gets you access to the calendar and manual scheduling.

Then, if you want access to the auto-scheduler, social media auto-posting, and custom post type support, you’ll need to go Pro:

*   1 site – $39
*   5 sites – $59
*   25 sites – $149
*   100 sites – $299

Each plan comes with one year of support and updates. You can also get a 25% discount when you renew your license.

### Limited Time Offer with AppSumo!

For a limited time, WP Scheduled Posts also has an AppSumo deal running that gets you **lifetime** access to the plugin with the following pricing:

*   5 sites – $39
*   10 sites – $78
*   Unlimited sites – $117

If you’re interested in the premium version, that AppSumo deal is obviously pretty dang attractive! Not only is it cheaper per site, but you also get a lifetime license vs a one-year license with the normal pricing.

If you’re interested in getting started, **[grab the AppSumo deal now](http://social.appsumo.com/k1syos)!** (A_gain, the AppSumo deal is only available for a limited time._)

![](https://secure.gravatar.com/avatar/dbfc60b99dd357e490f84ef7099dc25c?s=100&d=retro&r=g)

### About Colin Newcomer

[Colin Newcomer](https://www.cnewcomer.com/) is a freelance blogger for hire with a background in SEO and affiliate marketing. He helps clients grow their web visibility by writing primarily about digital marketing, WordPress, and B2B topics.

### Related Articles

*   [How to Manage Your Content With WP Scheduled Posts](https://wpmayor.com/how-to-manage-your-content-with-wp-scheduled-posts/)
    
    [![A schedule displayed on a laptop.](https://wpmayor.com/wp-content/uploads/2019/06/featured-schedule-posts-175x200.jpg)](https://wpmayor.com/how-to-manage-your-content-with-wp-scheduled-posts/)
    
    Scheduling posts in WordPress is a smart move for managing your content. You'll be able to give your readers a predictable routine for new posts, manage your workload, and even…
    
*   [WP Latest Posts: Recent Content Display](https://wpmayor.com/wp-latest-posts-recent-content-display/)
    
    [![](https://wpmayor.com/wp-content/uploads/2015/07/intro-e1435748482819.png)](https://wpmayor.com/wp-latest-posts-recent-content-display/)
    
    WP Latest Posts is a plugin that displays the WordPress recent content in few click and the way you want. It comes with 4 themes + a custom one where…
    
*   [Add Default Content to New Posts](https://wpmayor.com/add-default-content-to-new-posts/)
    
    [![Add Default Content to New Posts](https://wpmayor.com/wp-content/uploads/2016/12/wpmayor_logo_final.png)](https://wpmayor.com/add-default-content-to-new-posts/)
    
    With WordPress hooks you can easily add default content to new posts, if you are repeatedly entering some content into all your posts this is a great productivity aid. Learn…
    
*   [When should you use WP\_Query vs query\_posts() vs get\_posts()?](https://wpmayor.com/when-use-wp_query-vs-query_posts-vs-get_posts/)
    
    [![When should you use WP_Query vs query_posts() vs get_posts()?](https://wpmayor.com/wp-content/uploads/query_functions.png)](https://wpmayor.com/when-use-wp_query-vs-query_posts-vs-get_posts/)
    
    I recently came across a fantastic diagram by Rarst showing the difference between WP\_Query(), query\_posts() and get\_posts(). As you may know, these are all ways of retrieving posts in WordPress,…
    

**[Let's block ads!](https://blockads.fivefilters.org)** [(Why?)](https://blockads.fivefilters.org/acceptable.html)