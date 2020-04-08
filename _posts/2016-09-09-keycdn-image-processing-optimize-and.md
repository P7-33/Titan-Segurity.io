---
title: 'KeyCDN Image Processing: Optimize and Manipulate Images On-the-Fly'
date: 2019-10-09T12:13:00+01:00
draft: false
---

According to the [HTTP Archive](https://httparchive.org/), the average web page’s file size is about 50% images. Because images are such a weighty part of most websites, finding ways to optimize your WordPress site’s images is one of the biggest things you can do to speed up your site.

In this post, I’ll be taking a look at a service that helps you do just that – [KeyCDN’s new image processing functionality](https://www.keycdn.com/blog/image-processing).

If you’re not familiar, [KeyCDN](https://www.keycdn.com/) helps you speed up your site by delivering your content from a network of servers all around the world (_more on this second_). With the new image processing feature, KeyCDN can also help you dynamically optimize and manipulate the images you serve via KeyCDN _on-the-fly_.

It’s super flexible, easy to set up, and affordable to use alongside your KeyCDN service.

While I will touch on some general KeyCDN functionality in this post, I’ll mostly focus on just the new image processing feature.

How Does KeyCDN Work?
---------------------

Again, I’m focusing on KeyCDN’s new image processing feature for this review, but I first want to start with a deeper (_but still brief_) rundown of what KeyCDN is.

As the name suggests, KeyCDN is [a content delivery network (CDN)](https://wpmayor.com/cdn-how-to/), which is [a way to speed up your WordPress site](https://wpmayor.com/5-reasons-why-using-cdn-right-now/).

Essentially, you hook your website up to KeyCDN. Then, KeyCDN is responsible for delivering your site’s static files (like images) from its 34 data centers around the world. Your site’s visitors are automatically served files from the location that’s closest to them, which means your site loads faster no matter where in the world someone is located.

Because KeyCDN is already storing and serving your images, KeyCDN is in a unique position to automatically optimize your images, which brings me to the next question…

How Does KeyCDN Image Processing Work?
--------------------------------------

![](https://wpmayor.com/wp-content/uploads/2019/10/image-processing-1-630x315.png)

As you learned above, KeyCDN is already serving images for your site as part of its service.

The new image processing feature takes that one step further and lets KeyCDN process, optimize, and manipulate those images in _on-the-fly_. That is, no need to upload separate images.

By adding image parameters to your image URLs, you’ll be able to dynamically manipulate your images in a ton of different ways. Some of the things that you can do are:

*   Resize images
*   Change the quality level (_lower quality means a smaller file size_)
*   Choose between different compression methods
*   Crop images
*   Enlarge images
*   Flip images
*   Blur images
*   Change colors, like switching to grayscale

That’s just a partial list – there are tons of other manipulations like changing gamma, sharpening, tint, etc. You can [view a full list of options here](https://www.keycdn.com/support/image-processing).

You can also dynamically convert images to WebP as part of this process. If you’re not familiar with WebP, it’s a Google-backed image format that offers smaller file sizes without losing quality.

Currently, the WebP format is [supported by _most_ major browsers](https://caniuse.com/#feat=webp), though not all do. The most notable holdout is Safari, which still lacks WebP support.

The nice thing about this “on-the-fly” approach is that you don’t need to upload multiple images to your WordPress media library. All you do is upload the base image one single time and then you can have KeyCDN manipulate it as needed.

Once KeyCDN processes an image, it will store the processed image at its edge locations which further speeds up performance and saves you money (_more on that later_). That is, it doesn’t need to process the image for every single visit. It only processes the image once to store it in the cache.

### How Does KeyCDN Image Processing Benefit Your WordPress Site?

The biggest benefit of KeyCDN image processing is improved performance. Again, images are a huge component of most WordPress site’s page size, so optimizing them will help your site load faster.

To give you an idea of what can go wrong, I ran my test site through GTmetrix. You can see a few image-focused issues/recommendations:

![GTmetrix](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-1.png)

KeyCDN’s image processing tool can help you fix all those problems. Here’s how:

*   **Resizing/cropping images** – KeyCDN can automatically resize your images to the proper size for your website, which fixes the “serve scaled images” issue. You can either resize your images by keeping the same height/width ratio or you can dynamically crop images.
*   **Optimize images** – KeyCDN lets you apply varying levels of lossy or lossless compression to your images, which fixes the “optimize images” problem.

Beyond that, KeyCDN can help you serve images in the WebP format. [WebP Caching](https://www.keycdn.com/blog/webp-caching) is a feature that you can enable in the KeyCDN dashboard (it’s not automatically enabled together with the “Image Processing” feature). Once WebP Caching is enabled, KeyCDN will automatically deliver WebP assets without the need for any other changes. This is something that Google PageSpeed Insights recommends:

![Google PageSpeed Insights](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-2.png)

And another neat trick is the option to implement **adaptive images**. With this enabled, KeyCDN will automatically resize images based on each visitor’s device. So someone browsing on a smartphone will get a lower-resolution image, while someone browsing on a 4k screen gets a higher-resolution image.

So I would say performance is definitely the biggest benefit.

However, there are also some other perks.

For example, you can change an image’s looks on-the-fly. Want to make an image grayscale? No need to open an image editor and upload a new file – just tell KeyCDN to serve it in grayscale. You can also mess with other aspects of presentation, like adding a background, blurring an image, or flipping/rotating it.

Ready to see how it works? Let’s go hands-on.

How to Use KeyCDN Image Processing With WordPress
-------------------------------------------------

To get started with KeyCDN image processing, you’ll first need to set up the basic KeyCDN CDN service.

This is super easy – you just head to the **Zones** tab in your KeyCDN dashboard and create a new **Pull** zone with your WordPress site as the origin URL:

![Add zone in KeyCDN](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-3.png)

Once you’ve created your zone, KeyCDN will automatically “pull” your static files onto its network of global edge servers.

To tell your WordPress site to load images from KeyCDN rather than your WordPress site’s server, you can use [KeyCDN’s free CDN Enabler plugin](https://wordpress.org/plugins/cdn-enabler/) and enter your **Zone URL** in the plugin’s settings.

Here’s where you find your **Zone URL**:

![KeyCDN Zone URl for image processing](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-4.png)

And here’s how it looks in the CDN Enabler plugin:

![Set up CDN enabler](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-5.png)

Now, your WordPress site is configured to serve images (and other static files) from KeyCDN.

To finish things out, you’ll need to enable the image processing feature. To do this:

*   Edit your zone in your KeyCDN dashboard
*   Check the **Show Advanced Features** box
*   Use the drop-down to turn on **Image Processing**

![Enable KeyCDN image processing](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-6.png)

### How to Process Images Using Query Parameters

To process individual images, you’ll add query parameters to your image URLs – it’s super simple. You can [find the full list of query parameters here](https://www.keycdn.com/support/image-processing), but let’s run through two examples.

First, here’s my original image, which is located at this URL:

http://wpmayorexample-11c17.kxcdn.com/wp-content/uploads/2019/09/architectural-architectural-design-architecture-1029606.jpg

![Original image](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-7.jpg)

It’s over 4,000 px wide and just generally pretty unoptimized.

Let’s say you want to resize it to just 400 px wide and compress it a bit. To perform those two actions at the same time, you’d just need to add two query parameters to the end of the URL like this:

http://wpmayorexample-11c17.kxcdn.com/wp-content/uploads/2019/09/architectural-architectural-design-architecture-1029606.jpg?width=400&quality=70

And voila – a properly-sized and compressed image:

![Resized image](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-8.jpg)

It’s the same idea for other performance-focused processing. For example, you could add parameters for:

*   **crop** – crop images instead of just resizing and keeping the same aspect ratio.
*   **adaptive** – dynamically serve different sizes based on a visitor’s device.
*   Various compression-related parameters.

And it’s also the same idea for other tweaks. For example – want to make your image grayscale? Just add a grayscale\=1 parameter like this:

http://wpmayorexample-11c17.kxcdn.com/wp-content/uploads/2019/09/architectural-architectural-design-architecture-1029606.jpg?grayscale=1

And bam! Grayscale:

![Grayscale image](https://wpmayor.com/wp-content/uploads/2019/09/keycdn-image-processing-9.jpg)

I think you get the idea, right?

The main thing to remember here is that all of this happens on-the-fly using the exact same base image file.

That means you don’t need to upload multiple files to your WordPress media library to cover every possible situation – you can just upload your image one time and then have KeyCDN dynamically process it as needed by adding those query parameters from above.

KeyCDN Image Processing Pricing
-------------------------------

KeyCDN’s image processing feature is an extra cost on top of your existing KeyCDN usage.

It’s pretty affordable, though – it starts at just $1 per 2,000 operations.

Remember – KeyCDN will cache the image at its edge servers after processing it, so it does **not** count as an operation every time a visitor views a processed image. It only counts as an operation to process the image and put it into the cache.

That’s why I say it’s quite affordable.

Final Thoughts on KeyCDN Image Processing
-----------------------------------------

KeyCDN’s image processing functionality is a really nice addition to an already-great content delivery network service.

It makes it super easy to optimize and manipulate your images, without the need for an additional plugin or being forced to upload multiple images for every possible permutation. That will help you speed up your WordPress site and give you more design flexibility.

The only thing I’ll say is that I would love some type of WordPress plugin to make it easier to add query parameters to images in WordPress content. Right now, you seem to have to manually edit each image to add the parameters. While that’s not too difficult, I think there could be a simpler way, like having a plugin add the query parameter to resize all your images to a certain width unless you override it manually or automatically turn on adaptive images.

All in all, if you’re already using KeyCDN, you should definitely check out the image processing functionality. And if you’re not, give KeyCDN a look if you’re in the market for a content delivery network – the image processing is just the icing on top of a high-quality CDN service.

KeyCDN offers a free trial – no credit card required – and the setup process literally takes about 30 seconds. So – [give KeyCDN a try](https://www.keycdn.com/) and see if it works for you.

![](https://secure.gravatar.com/avatar/dbfc60b99dd357e490f84ef7099dc25c?s=100&d=retro&r=g)

### About Colin Newcomer

[Colin Newcomer](https://www.cnewcomer.com/) is a freelance blogger for hire with a background in SEO and affiliate marketing. He helps clients grow their web visibility by writing primarily about digital marketing, WordPress, and B2B topics.

### Related Articles

*   [Best Banner Image Plugin for WordPress](https://wpmayor.com/best-banner-image-plugin-for-wordpress/)
    
    [![Best Banner Image Plugin for WordPress](https://wpmayor.com/wp-content/uploads/2016/12/wpmayor_logo_final.png)](https://wpmayor.com/best-banner-image-plugin-for-wordpress/)
    
    WP Bannerize is an amazing Banner Image Manager. In your template insert: , use new shortcode featured or set it like Widget.
    
*   [How to Remove Image Sizes in WordPress](https://wpmayor.com/remove-image-sizes-in-wordpress/)
    
    [![How to Remove Image Sizes in WordPress](https://wpmayor.com/wp-content/uploads/custom-image-sizes-in-WordPress.png)](https://wpmayor.com/remove-image-sizes-in-wordpress/)
    
    In an earlier post about image sizes in WordPress, we had shown you a way to choose which image sizes are available for choosing when you're inserting an image in…
    
*   [The Image Wall Free WordPress Plugin](https://wpmayor.com/the-image-wall/)
    
    [![](https://wpmayor.com/wp-content/uploads/screenshot-11.jpg)](https://wpmayor.com/the-image-wall/)
    
    Nothing is more effective at capturing the fleeting attention of readers than engaging images. Bloggers do well to pepper their posts with strong imaging, and now there is a way…
    
*   [Extract All Image Sources from a WordPress Post](https://wpmayor.com/extract-all-image-sources-from-a-wordpress-post/)
    
    [![Extract All Image Sources from a WordPress Post](https://wpmayor.com/wp-content/uploads/2016/12/wpmayor_logo_final.png)](https://wpmayor.com/extract-all-image-sources-from-a-wordpress-post/)
    
    Here's a handy piece of code that extracts all the images from a WordPress post:
    
    \[crayon-5d9dbf686286d395160138/\]
    
    The resulting output will be in this form:
    
    \[crayon-5d9dbf6862873325730516/\]
    

**[Let's block ads!](https://blockads.fivefilters.org)** [(Why?)](https://blockads.fivefilters.org/acceptable.html)