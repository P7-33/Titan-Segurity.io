---
title: 'Mengubah TimeOut Pada Boot Linux'
date: 2019-10-16T05:25:00+01:00
draft: false
---

Assalamualaikum Hey..  
  

[![](https://www.wallpaperflare.com/static/971/769/277/linux-minimalism-foxyriot-tux-wallpaper.jpg)](https://www.wallpaperflare.com/static/971/769/277/linux-minimalism-foxyriot-tux-wallpaper.jpg)

  
Yaaa, bareng sama gw Lagi. Crusher.  
Lagi bingung soalnya, mau cari" bug sama Exploit tapi gw nya sibuk, :v  
Yaudah gw posting ini aja. Walaupun ini Ezz yakali dari sekian banyak orang ada yang belum tau. Nah gw post aja skrg yeeekan :  
  
  

[![](https://1.bp.blogspot.com/-5gFTJnejVyg/XaaYr1cRvNI/AAAAAAAABeY/CjeeFticcA46AqDmvgpCidSI3mQKdHJ_wCNcBGAsYHQ/s640/1.png)](https://1.bp.blogspot.com/-5gFTJnejVyg/XaaYr1cRvNI/AAAAAAAABeY/CjeeFticcA46AqDmvgpCidSI3mQKdHJ_wCNcBGAsYHQ/s1600/1.png)

  
Gw bikin ss an ini aja, biar ga dikatain Gambar Copas hihihi...  
  
  

[![](https://1.bp.blogspot.com/-xzHoNAd0k8w/XaaZDWYHDTI/AAAAAAAABeg/zHKSA504Qb0SVNpTZ5Hjo-yw4cQFVjgPQCNcBGAsYHQ/s640/2.png)](https://1.bp.blogspot.com/-xzHoNAd0k8w/XaaZDWYHDTI/AAAAAAAABeg/zHKSA504Qb0SVNpTZ5Hjo-yw4cQFVjgPQCNcBGAsYHQ/s1600/2.png)

  
$locate grub  
  
  
  
  

[![](https://1.bp.blogspot.com/-6NRvP8uOMsA/XaaZRajt5zI/AAAAAAAABek/cQ5abXzsDbMIuw2-L6aIkjEH3p58BWaYwCNcBGAsYHQ/s640/3.png)](https://1.bp.blogspot.com/-6NRvP8uOMsA/XaaZRajt5zI/AAAAAAAABek/cQ5abXzsDbMIuw2-L6aIkjEH3p58BWaYwCNcBGAsYHQ/s1600/3.png)

  
$nano /etc/default/grub  
  
\*Pake nano, gedit, pluma, leafpad dll gpp.  
  
  
  
  

[![](https://1.bp.blogspot.com/-uXV1Ri1tdTw/XaaZ0V9e0jI/AAAAAAAABew/9HOdedFXQ1EE5JcjYKee0ABXFsClW5C_gCNcBGAsYHQ/s640/4.png)](https://1.bp.blogspot.com/-uXV1Ri1tdTw/XaaZ0V9e0jI/AAAAAAAABew/9HOdedFXQ1EE5JcjYKee0ABXFsClW5C_gCNcBGAsYHQ/s1600/4.png)

  
Default nya 5, kalian ubah sesuka kalian sendiri :v  
  
Abis tu Save  
  
  
  

[![](https://1.bp.blogspot.com/-6Z2IT34GwVQ/XaabACqv1QI/AAAAAAAABe4/zOXd49wjUkcQB07SHk90ktgap_x6ATHRwCNcBGAsYHQ/s640/5.png)](https://1.bp.blogspot.com/-6Z2IT34GwVQ/XaabACqv1QI/AAAAAAAABe4/zOXd49wjUkcQB07SHk90ktgap_x6ATHRwCNcBGAsYHQ/s1600/5.png)

  
$update-grub  
  
tunggu sejenak, proses update config grub berjalan, kalo ada 2 os di 1 laptop, dia bakal mendeteksi dgn sendirinya...  
Ini ae lah, cukup yaakk  
  
  
See You Next Time, Good Bye  
  
  
Wassalamu'alaikum.