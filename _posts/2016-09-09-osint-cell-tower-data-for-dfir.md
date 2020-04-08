---
title: 'OSINT Cell Tower Data for DFIR'
date: 2019-12-03T02:56:00+01:00
draft: false
---

![](https://osintcurio.files.wordpress.com/2019/08/2.png?w=1432&h=623&crop=1)

[FORENSICS](https://osintcurio.us/category/forensics/), [GEOLOCATION](https://osintcurio.us/category/geolocation/), [OSINT](https://osintcurio.us/category/osint/), [PYTHON](https://osintcurio.us/category/python/), [TOOLS](https://osintcurio.us/category/tools/), [WIRELESS](https://osintcurio.us/category/wireless/)

Making Sense of OSINT Cell Tower Data for DFIR
==============================================

_Guest blog post by Jeff Lomas ([@BleuBloodHound](https://twitter.com/BleuBloodHound)). Jeff is a detective and digital forensic examiner for a large metropolitan police department in Las Vegas where he has worked for the past 11 years. Jeff executes search warrants on every imaginable digital devices for other detectives and turns the data extracted from these devices into actionable intelligence for other investigators._

The video of this blog post is on YouTube at [https://youtu.be/oVgazTQp7nw](https://youtu.be/oVgazTQp7nw).

Understanding where cell towers and Wi-Fi locations are physically located is big business for mobile apps. Knowing precise user location means potentially greater profits for companies trying to target users with ads or promotions. For OSINT and digital forensic practitioners, we can grab cell phone tower information from the mobile devices we image and cross-reference those towers with the tower’s physical location. When we combine this data with the date and time of the device owner’s activities, we can better understand where the device (and the owner) were at given times.

The Data Points
---------------

First off, this tower data comes from the herrevad.db (database file) present in most Android devices. This database contains dates and times along with MCC (mobile country code), MNC (mobile carrier code), LAC (location area code), and CID (cell ID). The MCC and MNC are country and carrier dependent whereas the LAC and CID are cell tower-dependent. If you don’t have all of these numbers, you won’t find the tower’s physical location. Using a forensic tool such as [Cellebrite](https://www.cellebrite.com/), you can export the herrevad database to a CSV file and inspect the cells to check for the required data. It should look something like the image below.

![](https://osintcurio.files.wordpress.com/2019/08/1.png)

This data is all in one cell when exported in latest versions of tools like Cellebrite. This is convenient because you know exactly where to look for the data, but as we will see later this format also makes automating the extraction process more difficult.

Inputting the Data
------------------

I started using this technique three years ago when I didn’t even know what an MCC was. The first site I found was [opencellid.org](http://opencellid.org/). Open Cellid is free to use and requires you to create a login to use their API. Once you’ve done this, you can enter the cell tower information you’ve retrieved from the Android device by hand (as I’ve done below).

![](https://osintcurio.files.wordpress.com/2019/08/2.png)

OpenCellId Web Page API Request and Response

NOTE: While we used a USA-specific example (due to the data set we had), these cell towers are all over the world. Here are the cell towers in [Singapore (click here) ](https://www.cellmapper.net/map?MCC=525&MNC=1&type=LTE&latitude=1.2437407597602572&longitude=103.81199665869605&zoom=12&showTowers=true&showTowerLabels=false&clusterEnabled=true&tilesEnabled=true&showOrphans=false&showNoFrequencyOnly=false&showFrequencyOnly=false&showBandwidthOnly=false&DateFilterType=Last&showHex=false&showVerifiedOnly=false&showUnverifiedOnly=false&showLTECAOnly=false&showENDCOnly=false&showBand=0&mapType=undefined&showSectorColours=true)and some in [Australia (click here)](https://www.cellmapper.net/map?MCC=505&MNC=1&type=LTE&latitude=-31.91166754752102&longitude=129.1237895350228&zoom=5&showTowers=true&showTowerLabels=false&clusterEnabled=true&tilesEnabled=true&showOrphans=false&showNoFrequencyOnly=false&showFrequencyOnly=false&showBandwidthOnly=false&DateFilterType=Last&showHex=false&showVerifiedOnly=false&showUnverifiedOnly=false&showLTECAOnly=false&showENDCOnly=false&showBand=0&mapType=undefined&showSectorColours=true).

Great! Now we have a physical location associated with our cell tower data both plotted on a map (on the right in the image above) and the latitude and longitude in the middle pane. This method of manully retrieving the locations is easy for a few data points but would be very cumbersome for 500 data points. If you have an older version of Cellebrite Physical Analyzer from a couple of years ago, you will definitely want to check out an excellent write-up by Matt Edmonson on how to automate this process at this link: [https://digitalforensicstips.com/2016/08/python-script-to-map-cell-tower-locations-from-an-android-device-report-in-cellebrite/](http://%20https//digitalforensicstips.com/2016/08/python-script-to-map-cell-tower-locations-from-an-android-device-report-in-cellebrite/).

Giving the Data Higher Confidence
---------------------------------

In the intelligence world, we want to give our clients the most up-to-date and comprehensive intel possible. With this in mind, I am very leary on trusting one source, even if it is an amazing site like Open Cellid. Cell ID Finder ([cellidfinder.com](http://cellidfinder.com/)) is another free site and requires no login. As you can see in the screenshot below, the results are very similar and the site is user friendly.

![](https://osintcurio.files.wordpress.com/2019/08/3.png)

CellID Finder Web Site

Yet another site you can use Cell Phone Trackers ([cellphonetrackers.org](http://cellphonetrackers.org/)). I would recommend creating a user account (no email verification needed!), because the site allows a batch feature so you can enter in multiple data points and receive multiple GPS points back instantaneously.

Automating It
-------------

_\[Hey there…this is Micah (WebBreacher) Hoffman chiming in here since I gave Jeff a hand with altering the original amazing Anaximander script from Matt Edmonson ([https://github.com/azmatt/Anaximander](https://github.com/azmatt/Anaximander)). Figured I’d note how we can do the above quicker than manually.\]_

As Jeff noted above, Matt Edmonson wrote a script to take the Cellebrite location exported XML file and look up each cell tower. How do you use the script? Steps are below.

*   You need to have Python ([https://python.org](https://python.org/)) version 3.7.x or more recent on your system for this to work. Go install that if you don’t have it.
*   To get the CSV of cell tower locations, go to [https://opencellid.org](https://opencellid.org/) and sign up for a free account.
*   Log into the OpenCellid platform and you will see the Download link as shown in the image below (arrow 1). Click it.

![](https://osintcurio.files.wordpress.com/2019/08/4.png)

Downloading the OpenCellid Data

*   Notice that, as of August 2019, the size of this CSV is 924MB compressed (arrow 3 above). It will expand to over 3GB on your system. Press the “here” link (arrow 2 above) to download the data.
*   Go to [https://github.com/azmatt/Anaximander](https://github.com/azmatt/Anaximander) and download the project in ZIP format or via git clone (need info on how to do this “git clone”? Check out our 10 Minute Tip on it [https://www.youtube.com/watch?v=QgLu-IF1XTA](https://www.youtube.com/watch?v=QgLu-IF1XTA)).
*   Move the downloaded cell\_towers.csv.gz file into the directory with Matt’s Anaximander scripts.
*   Uncompress the cell\_towers.csv.gz file to extract the cell\_towers.csv CSV.
*   You will need to launch a terminal window or command prompt (depending on your operating system) to run the next commands.
*   Run the dbFill.py to create a SQLite database from the CSV.
*   Put your exported XML location file from Cellebrite into the directory with Anaximander.
*   To run the newest Anaximander script, type: python Anaximander\_72.py -t YOURFILENAME.xml
    *   NOTE: This Anaximander\_72.py version of the script requires Python 3.7.x or more recent. You may need to change the above command to python3 Anaximander\_72.py -t YOURFILENAME.xml
*   The script should run (as shown in the animated GIF below). It will take a bunch of time (minutes to hours) depending on how many exported cell towers it needs to look up. If you want to stop it and look at the data you’ve already processed, press CONTROL-C and it’ll end the script and generate the cellTowers.kml file.

![](https://osintcurio.files.wordpress.com/2019/08/animatedgif1.gif)

Anaximander\_72.py Running Against Cellebrite 7.2 Exported Location Data

*   If you let it finish, you should have a cellTowers.kml file in the Anaximander directory now (see image below). This can be opened using Google Earth ([https://www.google.com/earth/](https://www.google.com/earth/)) so install that application and then double click on the file.

![](https://osintcurio.files.wordpress.com/2019/08/1-2.png)

cellTowers.kml Google Earth File

*   Inside Google Earth, you should see something that looks similar to the image below. Arrow 1 points to the pink paddle icons that note each of the cell towers that the script extracted and plotted. Arrows at 2 show the names of the plotted points are the time stamps for the data extracted from the Cellebrite application.

![](https://osintcurio.files.wordpress.com/2019/08/2-1.png)

Cellebrite Data Plotted in Google Earth

*   One neat thing that Matt included in the original script (and I kept here) is the ability to use the Google Earth time slider to move forward and backwards in time to have the plotted points show the order in which they were seen. Check out the animation below to see an example using data from 2017.

![](https://osintcurio.files.wordpress.com/2019/08/animatedgif2.gif)

Animation of Using the Google Earth Time Slider

Making It Pretty
----------------

_\[Back to Jeff!\] _These steps were relating cell tower data to physical locations and I needed a way to show my client (detectives, prosecutors, and juries) the data in a visual format without running running a Python script. Earth Point ([earthpoint.us/ExcelToKML.aspx](http://earthpoint.us/ExcelToKML.aspx)) is a site that converts Excel files to KML files. KML files are used to represent data in [Google Earth](https://www.google.com/earth/). To convert, simply choose your Excel file and the site will return a KML file. Open your KML file with Google Earth and it should look something like the image below.

![](https://osintcurio.files.wordpress.com/2019/08/1-1.png)

Google Earth Visualization of Cell Tower Locations

That’s It!
----------

So, what we did was:

*   Dump location data from an Android mobile device
*   Extract cell tower identifiers from the dump
*   Use a web site or script to convert the cell tower IDs to physical locations
*   Plot these data points in Google Earth

Why does this matter? We can place a certain device near a certain location at a certain time. A very valuable ability!

This was a quick introduction to converting cell tower data into physical locations. Remember, this data represents the general location of a cell tower, not the precision location of the device. If you have a different method for doing this, feel free to comment below and share with the group!

[WEBBREACHER](https://osintcurio.us/author/webbreacher/)[2019-08-19](https://osintcurio.us/2019/08/19/making-sense-of-osint-cell-tower-data-for-dfir/)[CELL PHONE](https://osintcurio.us/tag/cell-phone/), [CELL TOWER](https://osintcurio.us/tag/cell-tower/), [DFIR](https://osintcurio.us/tag/dfir/), [FORENSICS](https://osintcurio.us/tag/forensics/), [GEOLOCATION](https://osintcurio.us/tag/geolocation/), [GOOGLE EARTH](https://osintcurio.us/tag/google-earth/), [MOBILE DEVICE](https://osintcurio.us/tag/mobile-device/), [OSINT TOOLS](https://osintcurio.us/tag/osint-tools/), [PYTHON](https://osintcurio.us/tag/python/), [WI-FI](https://osintcurio.us/tag/wi-fi/), [WIFI](https://osintcurio.us/tag/wifi/)