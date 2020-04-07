---
title: 'Building a Low-Tech Website for Energy Efficiency'
date: 2020-01-11T04:32:00+01:00
draft: false
---

In an age of flashy jQuery scripts and bulky JavaScript front-end frameworks, loading a “lite” website is like a breath of fresh air. When most of us think of lightweight sites, though, our mind goes to old-style pure HTML and CSS sites or the intentionally barebones websites of developers and academics. [Low-tech Magazine](https://solar.lowtechmagazine.com/2018/09/how-to-build-a-lowtech-website.html), an intentionally low-tech and solar-powered website, manages to incorporate both modern web aesthetics and low-tech efficiency in one go.

Rather than hosting the site on data centers – even those running on renewable power sources – they have a self-hosted site that is run on solar power, causing the site to occasionally go off-line. Their model contrasts with the cloud computing model, which allows more energy efficiency at the user-side while increasing energy expense at data centers. Each page on the blog declares the page size, with an average page weight of 0.77 MB, less than half of the average page size of the top 500,000 most popular blogs in June 2018.

Some of the major choices that have limited the size of the website include building a static site as opposed to a dynamic site, “dithering” images, sparing a logo, staying with default typefaces, and eliminating all third-party tracking, advertising services, and cookies. Their [GitHub repository](https://github.com/lowtechmag/solar/wiki/Solar-Web-Design) details the front-end decisions  including using unicode characters for the site’s logo rather than embedding an SVG. While the latter may be scalable and lightweight in format it requires distribution to the end-user, which can involve a zipped package with eps, ai, png, and jpeg files in order to ensure the user is able to load the image.

As for the image dithering, the technique allows the website to maintain its characteristic appearance while still minimizing image quality and size. Luckily for Low-tech Magazine, the theme of the magazine allows for black and white images, suitable for dithering. Image sprites are also helpful for minimizing server requests by combining multiple small images into one. Storage-wise, the combined image will take up less memory and only load once.

There are also a few extraneous features that emphasize the website’s infrastructure. The background color indicates the capacity of the solar-charged battery for the website’s server, while other stats about the server’s location (time, sky conditions, forecast) also help with making the website availability in the near future more visible. Who knows, with the greater conscience on environmental impact, this may be a new trend in web design.

  
  
from Hackaday https://ift.tt/2QIN43l  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)