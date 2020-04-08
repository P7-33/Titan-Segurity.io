---
title: 'Redirect Website Dengan htaccess'
date: 2019-10-17T09:38:00+01:00
draft: false
---

Assalamu'alaikum Guys.  
Balik Lagi Dengan Aing, H3h3.  
  

[![](https://1.bp.blogspot.com/-Zn_S3BVSCS0/XagiXpjzOuI/AAAAAAAABU0/-WoMfL_45zMUtHHnBzsC40JX_TtSOfbPgCLcBGAsYHQ/s640/redirect-htaccess.png)](https://1.bp.blogspot.com/-Zn_S3BVSCS0/XagiXpjzOuI/AAAAAAAABU0/-WoMfL_45zMUtHHnBzsC40JX_TtSOfbPgCLcBGAsYHQ/s1600/redirect-htaccess.png)

  
  
Kali ini, Kita Mau Buat Tutorial **Redirect Website Dengan .htaccess**.  
Mungkin Sebagian Dari Kalian Udah Ada Yang Tau, Dan Ada Juga Yang Belom Tau.  
  
Langsung Aja Ke Tutorialnya  
  
Bahan - Bahannya :  
\- **Akses Shell / Cpanel**  
\- **.htaccess** ( Dengan Source Code Seperti Di Bawah Ini )  

  

       **_RewriteEngine on_**

**_       RewriteCond %{HTTP\_HOST} ^domainlama.com \[NC\]_**

**_       RewriteRule ^(.\*)$ domainkalian.com/$1 \[L,R=301,NC\]_**

Kalo Semua Bahannya Sudah Ada, Kita Lanjut Ke Cara - Caranya : 

**Pertama**, Buka **Akses Shell Atau Cpanel** Kalian

Karna Aing Dah Ada Akses Shell, Aing Make Itu Aja, Biar Ga Cape - Cape Nyarinya, H3h3

  

  

[![](https://1.bp.blogspot.com/-eEQE8fJTZLs/Xagh1hzrnMI/AAAAAAAABUs/4vR66qvRuQ8S-w1QQTBGZOrVU2ITBw3AwCLcBGAsYHQ/s640/Screenshot%2B%25283%2529.png)](https://1.bp.blogspot.com/-eEQE8fJTZLs/Xagh1hzrnMI/AAAAAAAABUs/4vR66qvRuQ8S-w1QQTBGZOrVU2ITBw3AwCLcBGAsYHQ/s1600/Screenshot%2B%25283%2529.png)

  

Seperti Gambar Di Atas, Terdapat **.htaccess** Orinya / htaccess Bawaan Dari Webnya.

Sebelum Kita Mengupload File **.htaccess** Kita, File .htaccess Bawaannya Kita Backup Dulu / Kita Rename

Setelah Itu Upload File **.htaccess** Yang Kita Buat Dengan Source Code Diatas Di Dir public\_html

  

  

[![](https://1.bp.blogspot.com/-Z7HaWVXwQmk/XagkQQmU6HI/AAAAAAAABVE/LHklKczZnbgUEOHWwhPZC1XZZp8leeK-QCLcBGAsYHQ/s640/Screenshot%2B%25285%2529.png)](https://1.bp.blogspot.com/-Z7HaWVXwQmk/XagkQQmU6HI/AAAAAAAABVE/LHklKczZnbgUEOHWwhPZC1XZZp8leeK-QCLcBGAsYHQ/s1600/Screenshot%2B%25285%2529.png)

  

Yang Aing Tandai, Ganti Dengan Domain Dari **Akses Shell** Kalian.

  
  
  
  

[![](https://1.bp.blogspot.com/-tzSAXklpnRM/XagkzqteAwI/AAAAAAAABVQ/QuGvPt2_LhQoYt8TTiB_PkUC_x4Otsb9ACLcBGAsYHQ/s640/Screenshot%2B%25286%2529.png)](https://1.bp.blogspot.com/-tzSAXklpnRM/XagkzqteAwI/AAAAAAAABVQ/QuGvPt2_LhQoYt8TTiB_PkUC_x4Otsb9ACLcBGAsYHQ/s1600/Screenshot%2B%25286%2529.png)

  

Yang Dibawahnya, Isi Dengan Web / Blog Yang Ingin Kalian Redirectkan Kesitu

Save, Dan Buka Web Yang Baru Kalian Set **.htaccess** nya

Kalo Webnya Redirect Ke Web / Blog Kalian, Berarti Sukses.

Kalo Kaga, Berarti Faktor Face, h3h3

  

Sekian Ya, Wassalamu'alaikum

  

TTD : Wannabe\_ID