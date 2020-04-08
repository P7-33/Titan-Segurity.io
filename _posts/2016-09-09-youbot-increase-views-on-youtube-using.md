---
title: 'YouBot - Increase Views On Youtube Using Tor'
date: 2019-10-11T14:48:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-_Bz_7Hix-Zw/XaCFzt3gheI/AAAAAAAACpo/2JEOsVRnZ8Evtkpi7FM6EtCez_9coGI2QCLcBGAsYHQ/s320/Youtube.png)](https://1.bp.blogspot.com/-_Bz_7Hix-Zw/XaCFzt3gheI/AAAAAAAACpo/2JEOsVRnZ8Evtkpi7FM6EtCez_9coGI2QCLcBGAsYHQ/s1600/Youtube.png)

  
**YouBot** adalah tool untuk meningkatkan Viewers youtube menggunakan Tor, tool ini di buat menggunakan program bash  
  
**Installation YouBot**  
  
Untuk mendapatkan tool tersebut, anda harus melakukan cloning terhadap repository berikut  
  
```
git clone https://github.com/thelinuxchoice/unfollower
```

[![](https://1.bp.blogspot.com/-9FCqKbibVK8/XaCF0OVDJ4I/AAAAAAAACps/ie8B1mcBK4Iy1Jb74zhfaVLEbrJEckPAACLcBGAsYHQ/s320/youbot-git-www.codecrime.net.png)](https://1.bp.blogspot.com/-9FCqKbibVK8/XaCF0OVDJ4I/AAAAAAAACps/ie8B1mcBK4Iy1Jb74zhfaVLEbrJEckPAACLcBGAsYHQ/s1600/youbot-git-www.codecrime.net.png)

  
  
Jika sudah melakukan cloning sekarang anda masuk kedalam directory tool tersebut dan jalankan perintah berikut untuk menginstall tor, proxychains  
  
```
apt-get install -y xdotool tor proxychains
```

[![](https://1.bp.blogspot.com/-LC53sa8LH4M/XaCF1cxPJUI/AAAAAAAACp0/wmRm33JKKBMg6W6QzXXwxHrskdwjIjEmwCLcBGAsYHQ/s320/youbot-install2-www.codecrime.net.png)](https://1.bp.blogspot.com/-LC53sa8LH4M/XaCF1cxPJUI/AAAAAAAACp0/wmRm33JKKBMg6W6QzXXwxHrskdwjIjEmwCLcBGAsYHQ/s1600/youbot-install2-www.codecrime.net.png)

  
**Running YouBot**  
  
Jika sudah melakukan berhasil melakukan beberapa tahap penginstallan, sekarang anda jalankan perintah berikut  
  
```
service tor start                                                           sudo ./youbot.sh URL             
```