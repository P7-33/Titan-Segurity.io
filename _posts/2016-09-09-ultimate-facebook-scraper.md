---
title: 'Ultimate Facebook Scraper'
date: 2019-12-08T10:31:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-XP4GRwvdIHw/XdNYvIlKquI/AAAAAAAAQ4E/6fmCNDqBmjcKJhF6kP0tpoYRkrRzaBvDQCNcBGAsYHQ/s640/Ultimate-Facebook-Scraper_19_screenshot.png)](https://1.bp.blogspot.com/-XP4GRwvdIHw/XdNYvIlKquI/AAAAAAAAQ4E/6fmCNDqBmjcKJhF6kP0tpoYRkrRzaBvDQCNcBGAsYHQ/s1600/Ultimate-Facebook-Scraper_19_screenshot.png)

**Ultimate Facebook Scraper - A Bot Which Scrapes Almost Everything About A Facebook User'S Profile Including All Public Posts/Statuses Available On The User'S Timeline, Uploaded Photos, Tagged Photos, Videos, Friends List And Their Profile Photos**

  

  
Tooling that **automates** your social media interactions to collect posts, photos, videos, friends, followers and much more on Facebook.

  

**Features**  
A bot which scrapes almost everything about a facebook user's profile including

*   uploaded photos
*   tagged photos
*   videos
*   friends list and their profile photos (including Followers, Following, Work Friends, College Friends etc)
*   and all public posts/statuses available on the user's timeline.

  

The best thing about this scraper is that the data is scraped in an organized format so that it can be used for educational/research purpose by researchers. Moreover, this scraper does not use Facebook's Graph API so there are no rate limiting issues as such.  
**This tool is being used by thousands of developers weekly and we are pretty amazed at this response! Thankyou guys!**  
For details regarding **citing/referencing** this tool for your research, check the 'Citation' section below.  
  
**Note**  
At its core, this tool uses xpaths of **'divs'** to extract data from them. Since Facebook keeps on updating its site frequently and the 'divs' get changed. Consequently, we have to update the divs accordingly to correctly scrape the data.  
The developers of this tool have devoted a lot of time and effort in developing and most importantly maintaining this tool for quite a lot time now. **In order to keep this amazing tool alive, we need support from you geeks.**  
The code is pretty intuitive and easy to understand, so you can update the relevant xpaths in the code when you feel that you have tried many profiles and the data isn't being scraped for any of them (that's a hint that Facebook has updated their site) and generate a pull request. That's quite an easy thing to do. Thanks!  
  
**Sample**

  

[![](https://1.bp.blogspot.com/-BZ-c7ezD4wE/XdNY3GfaEbI/AAAAAAAAQ4I/I2PvaxLFCIofbeuD86CywOoKjZ7Nbtt6QCNcBGAsYHQ/s640/Ultimate-Facebook-Scraper_18_main.png)](https://1.bp.blogspot.com/-BZ-c7ezD4wE/XdNY3GfaEbI/AAAAAAAAQ4I/I2PvaxLFCIofbeuD86CywOoKjZ7Nbtt6QCNcBGAsYHQ/s1600/Ultimate-Facebook-Scraper_18_main.png)

**Screenshot**

  

[![](https://1.bp.blogspot.com/-t5jFK84FK8U/XdNY8QTTbyI/AAAAAAAAQ4M/TdZEavyJhbs9f6hMXqSDAJz8bmoEujVHwCNcBGAsYHQ/s640/Ultimate-Facebook-Scraper_19_screenshot.png)](https://1.bp.blogspot.com/-t5jFK84FK8U/XdNY8QTTbyI/AAAAAAAAQ4M/TdZEavyJhbs9f6hMXqSDAJz8bmoEujVHwCNcBGAsYHQ/s1600/Ultimate-Facebook-Scraper_19_screenshot.png)

**Usage**  
  
**Installation**  
You will need to install latest version of [Google Chrome](https://www.google.com/chrome/ "Google Chrome"). Moreover, you need to install [selenium](https://www.kitploit.com/search/label/Selenium "selenium") module as well using

```
pip install selenium
```

Run the code using Python 3. Also, the code is multi-platform and is tested on both Windows and Linux. The tool uses latest version of [Chrome Web Driver](http://chromedriver.chromium.org/downloads "Chrome Web Driver"). I have placed the webdriver along with the code but if that version doesn't work then replace the chrome web driver with the latest one.  
  
**How to Run**  
There's a file named "input.txt". You can add as many profiles as you want in the following format with each link on a new line:

```
[https://www.facebook.com/andrew.ng.96](https://www.facebook.com/andrew.ng.96)  
[https://www.facebook.com/zuck](https://www.facebook.com/zuck)
```

Make sure the link only contains the username or id number at the end and not any other stuff. Make sure its in the format mentioned above.  
Note: There are two modes to download Friends Profile Pics and the user's Photos: Large Size and Small Size. You can change the following variables. By default they are set to Small Sized Pics because its really quick while Large Size Mode takes time depending on the number of pictures to download

```
# whether to download the full image or its thumbnail (small size)  
# if small size is True then it will be very quick else if its False then it will open each photo to download it  
# and it will take much more time  
friends_small_size = True  
photos_small_size = True
```

  
**Authors**  
You can get in touch with us on our LinkedIn Profiles:  
**Haris Muneer**  
**Hassaan Elahi**  
  

**[Download Ultimate-Facebook-Scraper](http://cigorsica.com/3RWG "Download Ultimate-Facebook-Scraper")**

**Regards**

**Kang Asu**