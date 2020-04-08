---
title: 'Offline and back again: Surviving the PHP 7 upgrade by adding one letter'
date: 2019-12-14T03:33:00+01:00
draft: false
---

Offline and Back Again
======================

This site was offline for a couple days. It’s back again.

What happened? Initially, I wasn’t quite sure, although I had a strong suspicion that it was related to an automated upgrade from PHP 5.6 to PHP 7.2 performed by my web host.

Loading any page on my site resulted in a blank white screen. No error message was sent, but the HTTP response was error code 500: Internal server error.

I host a number of websites on the same web host. Most of them were still up. They run on WordPress or static HTML, for the most part. The only other one of my domains that was also down was [LessnMore.net](https://lessnmore.net). That site and this one (alanhogan.com) are the only two powered by the [custom content management system I wrote myself](https://alanhogan.com/hscms) a dozen years ago.

Using my web host’s control panel, I flipped the PHP engine for the affected sites back to PHP 5.6. After a few minutes, the change took effect, and my websites came back online.

That’s good, but it’s not a permanent fix.

At this point I was confident that the most likely cause was that something in my custom CMS that had become incompatible with PHP 7. While I did some of my first and most exciting programming in PHP as a self-taught teenager, and was later a professional PHP developer for some time, it has now been years since I have written a significant amount PHP. As a result, I am increasingly out of touch with the evolution of the language.

Now disappointingly enough, I was unable to locate any PHP errors in the log files made available to me on my host. I am not entirely sure why that is. It is possible that I have misconfigured something.

Luckily I already had a staging version of alanhogan.com set up on the web host. It is basically the same as alanhogan.com, but it has a different domain and it runs code I want to test. I use it on the rare occasions I am changing the functionality of my CMS or of my site’s custom code. And since it was still set to PHP 7.2, it was failing to load. Time to figure out how to make it work with this newever version of PHP!

I added a `die()` call at the top of my CMS’s entry point. This function sends whatever string you want to the browser and then immediately stops script execution. I saw the message I sent to `die` when I reloaded my page, so that was good. Then I moved it down the script until a page refresh failed to show the message. This let me quickly isolate the failure to something that was happening when I first attempt to query the database backing this website. That database is powered by MySQL.

At this point, I brought up a page documenting [breaking changes in PHP 7](https://www.php.net/manual/en/migration70.incompatible.php) and searched in-page for “MySQL.” Sure enough, the page noted that after years of deprecation, “ext/mysql” had been removed from PHP. This was the oldest method of connecting to a MySQL database. I knew that “MySQLi” was a newer and preferred set of APIs for connecting to MySQL. I hoped I would not be in for a slog of an upgrade. It would be annoying if I needed to change code for every database query in my CMS.

When I originally wrote HS-CMS, I used a database abstraction library that supported multiple database drivers. Could I simply switch “mysql” to “mysqli”?

I opened the configuration file I created long ago that tells my CMS everything it needs to know specifically about my site. Look at this line of code and the surrounding comments:

```
//"Designator" for ADOdb Lite: http://adodblite.sourceforge.net/howtoinstall.php $HS_config['databaseType'] = 'mysql'; //mysql, mysqli, postgres8... 
```

Hey, alright! It is always a treat when a piece of past programming shows enough forethought to save you a lot of time in the future. I don’t even need to go visit the ADOdb Lite documentation page to see, from the in-line comment, that `mysqli` is indeed likely to be a valid value here. So I changed the line, reloaded, and hoped for the best:

```
$HS_config['databaseType'] = 'mysqli'; //mysql, mysqli, postgres8... 
```

Success! Immediately the staging version of alanhogan.com whirred to life. All it took was the insertion of the letter `i` in a key place, thanks to a long-ago, prudent use of a generic database connection library.

However, while the home page was working, article pages were still disappearing with a 500 status. In short, I was quickly able to determine that this was due to use of some caching functions powered by an old and [abandoned caching library that did not survive the jump to PHP 7](https://pear.php.net/bugs/bug.php?id=17774), so I made some very small changes to my code in order to skip calls to the caching library. And that’s how I got my site back to 100% again after the upgrade to PHP 7, despite not being to see any meaningful error logs! (I will have to look into that. While it is kind of fun, in a puzzle-box sort of way, debugging without an error message, it’s also rather absurd and a waste of time.)

  
  
from Hacker News https://ift.tt/2LMnGqy