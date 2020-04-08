---
title: 'SocialPath - Track Users Across Social Media Platforms'
date: 2019-10-09T16:06:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-jeOCgC14VL4/XZ3r4Tl6urI/AAAAAAAACnc/bn-WLhSt3EM3gEEc39Z4sHYSSMRjvMzlQCLcBGAsYHQ/s320/socialpath-logo.png)](https://1.bp.blogspot.com/-jeOCgC14VL4/XZ3r4Tl6urI/AAAAAAAACnc/bn-WLhSt3EM3gEEc39Z4sHYSSMRjvMzlQCLcBGAsYHQ/s1600/socialpath-logo.png)

  
  
SocialPath adalah aplikasi Django untuk mengumpulkan intelijen media sosial pada nama pengguna tertentu. Ia memeriksa Twitter, Instagram, Facebook, Reddit, dan Stackoverflow. Data yang dikumpulkan diurutkan berdasarkan frekuensi kata, tagar, garis waktu, sebutan, akun serupa, dan disajikan dalam bentuk grafik dengan bantuan D3js. Teknik ini memungkinkan saya untuk **melacak pengguna darknet yang tidak menggunakan nama panggilan unik****.**  
**Supported Services**  

*   Twitter
*   Stackoverflow
*   Instagram
*   Reddit
*   Facebook (Post Only)

  

**Requirements**

*   Django
*   Tweepy
*   PRAW
*   Django related packages
*   facebook\_scraper

  

**Installation SocialPath**  
  
Untuk artikel ini cukup lumayan panjang, kalian bisa mengukutinya step by step dengan baik dan siapkan kopi biar tidak bosan:D  
**SocialPath** dapat di install di windows, linux, android (termux), dalam kasus ini saya menggunakan kalilinux, untuk pengguna termux kalian juga bisa mengikuti tutorial ini  
sebelum menjalankan **SocialPath** kalian harus menginstall repo github berikut   
  
  
```
git clone https://github.com/woj-ciech/SocialPath
```

[![](https://1.bp.blogspot.com/-SCtHLjGV6H0/XZ3x80iK90I/AAAAAAAACno/Cq5TlCIOKPM4Fmd5J0erZDtH441WD6OFQCLcBGAsYHQ/s320/socialpath-git-www.codecrime.net.png)](https://1.bp.blogspot.com/-SCtHLjGV6H0/XZ3x80iK90I/AAAAAAAACno/Cq5TlCIOKPM4Fmd5J0erZDtH441WD6OFQCLcBGAsYHQ/s1600/socialpath-git-www.codecrime.net.png)

  
  
Jika sudah menginstall socialpath, sekarang anda masuk ke dalam directory tersebut  
  
  
```
cd SocialPath
```**Installation Setup **  
  
Install setup socialpath dengan menjalankan perintah berikut, jika sudah masuk kedalam directory socialpath  
  
  
```
pip3 install -r requirements.txt
```

[![](https://1.bp.blogspot.com/-tJjWkmAxEWs/XZ3yywxfTiI/AAAAAAAACoE/4cHZ5ewoBWoFWvFYiilsd-U6yZw6RZd9wCLcBGAsYHQ/s320/socialpath-install-www.codecrime.net.png)](https://1.bp.blogspot.com/-tJjWkmAxEWs/XZ3yywxfTiI/AAAAAAAACoE/4cHZ5ewoBWoFWvFYiilsd-U6yZw6RZd9wCLcBGAsYHQ/s1600/socialpath-install-www.codecrime.net.png)

  
  
Proses install sedang berlangsung, pastikan internet anda cepat dan kuota banyak agar proses installasi setup socialpath cepat selesai  
  
**Installation Setup Manage**  
  
Jika proses install di atas sudah selesai, sekarang anda dapat meningstall setup manage dan install dengan satu" berikut yang harus di install  
  
  

*   python3 manage.py makemigrations social
*   python3 manage.py migrate
*   python3 manage.py migrate social

  
  
  
  

[![](https://1.bp.blogspot.com/-RJ4EtYeuCmA/XZ3yzjAk4eI/AAAAAAAACoo/rlXjkHSZNUYmhv2XJPbPbGi9SJpIxtu-ACEwYBhgL/s320/socialpath-managePy-www.codecrime.net.png)](https://1.bp.blogspot.com/-RJ4EtYeuCmA/XZ3yzjAk4eI/AAAAAAAACoo/rlXjkHSZNUYmhv2XJPbPbGi9SJpIxtu-ACEwYBhgL/s1600/socialpath-managePy-www.codecrime.net.png)

  
  

[![](https://1.bp.blogspot.com/-tcG4lgLH-AE/XZ3y0EdHd6I/AAAAAAAACoQ/JExi_en5kngNP0QFegA4b5a6JxJ6r4seQCEwYBhgL/s320/socialpath-managePy2-www.codecrime.net.png)](https://1.bp.blogspot.com/-tcG4lgLH-AE/XZ3y0EdHd6I/AAAAAAAACoQ/JExi_en5kngNP0QFegA4b5a6JxJ6r4seQCEwYBhgL/s1600/socialpath-managePy2-www.codecrime.net.png)

  
  
  
Lakukan penginstallan berikut secara bertahap dan jika manage sudah di install semua, ada lagi kita akan mengkonfigurasi untuk membuat users dan password ketika login di django nanti, jalankan dengan perintah berikut  
  
  
```
python3 manage.py createsuperuser
```

[![](https://1.bp.blogspot.com/-o76UhPs-Reo/XZ3yxuAHsiI/AAAAAAAACoc/Pe9JkLmdlFMHt0eeo9UbTtHpNLSn4tq0gCEwYBhgL/s320/socialpath-createUsernamePassworddll-www.codecrime.net_LI.jpg)](https://1.bp.blogspot.com/-o76UhPs-Reo/XZ3yxuAHsiI/AAAAAAAACoc/Pe9JkLmdlFMHt0eeo9UbTtHpNLSn4tq0gCEwYBhgL/s1600/socialpath-createUsernamePassworddll-www.codecrime.net_LI.jpg)

  
  
Masukkan username kalian, disini saya menggunakan username default **(root),** masukkan email dan password yang benar, karena nanti ini akan kita gunakan untuk login di django nanti, jika semua sudah selesai akan ada tulisan **Superuser created successfully** seperti gambar di atas  
  
**Running SocialPath**  
  
Semua sudah selesai, sekarang kita jalankan server socialpath nya menggunakan perintah berikut  
  
  

[![](https://1.bp.blogspot.com/-I3KXJ326n1Y/XZ3yxFyh8lI/AAAAAAAACoY/sOaSk_dlqf8xhU7FYZ7f1s3cUb_yIRECgCEwYBhgL/s320/socialpath-Wait-www.codecrime.net.png)](https://1.bp.blogspot.com/-I3KXJ326n1Y/XZ3yxFyh8lI/AAAAAAAACoY/sOaSk_dlqf8xhU7FYZ7f1s3cUb_yIRECgCEwYBhgL/s1600/socialpath-Wait-www.codecrime.net.png)

  
  
Nahhh, jika penginstallan sudah berhasil semua dan pastinya tidak akan ada errors, jika kita lihat gambar di atas ada url server **http://127.0.0.1:8000/**  
Sekarang buka browser kalian dan ketik url server berikut   
  
  

[![](https://1.bp.blogspot.com/-T7ptvrB1O9I/XZ3yyfYmwVI/AAAAAAAACn8/sXY2vtRUR7AANaSuzkWi-jWwkkfJCYgaACEwYBhgL/s320/socialpath-djangologin-www.codecrime.net.png)](https://1.bp.blogspot.com/-T7ptvrB1O9I/XZ3yyfYmwVI/AAAAAAAACn8/sXY2vtRUR7AANaSuzkWi-jWwkkfJCYgaACEwYBhgL/s1600/socialpath-djangologin-www.codecrime.net.png)

  
  
Masukkan url berikut **http://127.0.0.1:8000/admin** untuk masuk ke halaman login seperti gambar di atas, masukkan username dan password yang telah kita input tadi, karena username saya default **(root),** maka masukkan username tersebut dan password yang sudah anda inputkan tadi  
  
  

[![](https://1.bp.blogspot.com/-vujEqNHicFQ/XZ3yxK6sT2I/AAAAAAAACn0/isUrU9329KkyT9zRz2uQxoD98bKOTGw4QCEwYBhgL/s320/socialpath-djangoadmin-www.codecrime.net.png)](https://1.bp.blogspot.com/-vujEqNHicFQ/XZ3yxK6sT2I/AAAAAAAACn0/isUrU9329KkyT9zRz2uQxoD98bKOTGw4QCEwYBhgL/s1600/socialpath-djangoadmin-www.codecrime.net.png)

  
  
Boom, berhasil masuk untuk tutorial lebih lengkap tentang cara menggunakannya kalian bisa kunjungi github resminya [Disini](https://github.com/woj-ciech/socialpath)