---
title: 'The Heat Of The Moments – Location Visualization In Python'
date: 2019-12-06T04:07:00+01:00
draft: false
---

Have you ever taken a look at all the information that Google has collected about you over all these years? That is, of course, assuming you _have_ a Google account, but that’s quite a given if you own an Android device and have privacy concerns overruled by convenience. And considering that GPS is a pretty standard smartphone feature nowadays, you shouldn’t be surprised that your entire location history is very likely part of the collected data as well. So unless you opted out from an everchanging settings labyrinth in the past, it’s too late now, that data exists — period. Well, we might as well use it for our own benefit then and visualize what we’ve got there.

Location data naturally screams for maps as visualization method, and \[luka1199\] thought what would be better than [an interactive Geo Heatmap written in Python](https://github.com/luka1199/geo-heatmap), showing all the hotspots of your life. Built around the [Folium](https://python-visualization.github.io/folium/) library, the script reads the JSON dump of your location history that you can request from [Google’s Takeout service](https://support.google.com/accounts/answer/3024190?hl=en), and overlays the resulting heatmap on the OpenStreetMap world map, ready for you to explore in your browser. Being Python, that’s pretty much all there is, which makes \[Luka\]’s script also a good starting point to play around with Folium and map visualization yourself.

While simply just looking at the map and remembering the places your life has taken you to can be fun on its own, you might also realize some time optimization potential in alternative route plannings, or use it to turn your last road trip route into an art piece. Just, whatever you do, be careful that you don’t accidentally [leak the location of some secret military facilities](https://hackaday.com/2018/01/28/opt-out-fitness-data-sharing-leads-to-massive-military-locations-leak/).

\[via [r/dataisbeautiful](https://www.reddit.com/r/dataisbeautiful/comments/e2zv4w/i_wrote_a_python_script_that_generates_a_geo/)\]

  
  
from Hackaday https://ift.tt/2DS1JSs  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)