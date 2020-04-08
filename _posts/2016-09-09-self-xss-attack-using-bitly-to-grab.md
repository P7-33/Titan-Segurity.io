---
title: 'self-xss - Attack Using bit.ly to Grab Cookies Tricking Users Into
Running Malicious Code'
date: 2019-10-15T15:33:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-_hvm58zZrBg/XaXRz3l1DiI/AAAAAAAACrY/vIeUgEl-LdIyg9llDMsZcTuitHK3MzquwCLcBGAsYHQ/s320/self-xss-run-www.codecrime.net.png)](https://1.bp.blogspot.com/-_hvm58zZrBg/XaXRz3l1DiI/AAAAAAAACrY/vIeUgEl-LdIyg9llDMsZcTuitHK3MzquwCLcBGAsYHQ/s1600/self-xss-run-www.codecrime.net.png)

  
**Self-XSS** adalah penyerangan social engineering yang digunakan untuk mengendalikan akun web korban dengan menipu pengguna agar menyalin dan menempelkan konten jahat ke browser mereka. Karena vendor peramban web dan situs web telah mengambil langkah-langkah untuk mengurangi serangan ini dengan memblokir tempelkan tag javascript, saya mencari cara untuk melakukan itu menggunakan Bit.ly, sehingga kami dapat membuat pengalihan yang menunjuk ke "website.com/javascript:malicious\_code" . Jika pengguna ditipu untuk menjalankan kode setelah "situs web.com/" cookie dari sesi yang disahkan dari situs web.com akan dikirim ke penyerang.  
  
**Features: **  
Port forwarding menggunakan Serveo.net dan Ngrok  
  
**Installation Self-Xss Tool**  
  
sebelum menjalankan tool tersebut anda harus menginstall repository github berikut  
  
```
git clone https://github.com/thelinuxchoice/self-xss
```

[![](https://1.bp.blogspot.com/-QJpau17CX94/XaXR1Qw1hcI/AAAAAAAACr8/fEnLVb1TCqM5a003DldLPkJdfZtNouHIwCEwYBhgL/s320/self-xss-git-www.codecrime.net.png)](https://1.bp.blogspot.com/-QJpau17CX94/XaXR1Qw1hcI/AAAAAAAACr8/fEnLVb1TCqM5a003DldLPkJdfZtNouHIwCEwYBhgL/s1600/self-xss-git-www.codecrime.net.png)

  
  
**Running Self-Xss Tool**  
  
tool ini di tulis menggunakan bash, jika anda sudah melakukan cloning pada repos github di atas sekarang anda masuk ke folder tersebut dan jalankan perintah berikut  
  
```
cd self-xss                                                                 bash self-xss.sh
```

[![](https://1.bp.blogspot.com/-oDJS4fLMxTE/XaXR1WqmcQI/AAAAAAAACr4/luqOQGV3oiMXJjZmqQ5KuWhOSSkqonGdgCEwYBhgL/s320/self-xss-run-www.codecrime.net.png)](https://1.bp.blogspot.com/-oDJS4fLMxTE/XaXR1WqmcQI/AAAAAAAACr4/luqOQGV3oiMXJjZmqQ5KuWhOSSkqonGdgCEwYBhgL/s1600/self-xss-run-www.codecrime.net.png)

  
Jika sudah di jalankan sekarang lihat, ada 2 option pilihan, anda bisa memilih **serveo dan ngrok** dalam kasus ini saya menggunakan **serveo**   
  

[![](https://1.bp.blogspot.com/-ybw11c2E_4c/XaXR11yeJkI/AAAAAAAACr8/T912SS667bsXFQmDmZGSgQZuha7kWfQDQCEwYBhgL/s320/self-xss-runGetConf-www.codecrime.net.png)](https://1.bp.blogspot.com/-ybw11c2E_4c/XaXR11yeJkI/AAAAAAAACr8/T912SS667bsXFQmDmZGSgQZuha7kWfQDQCEwYBhgL/s1600/self-xss-runGetConf-www.codecrime.net.png)

  
Pilih 1, anda juga bisa menggunakan subdomain, jika tidak menggunakan subdomain disana ada defaultnya yang nanti akan kita gunakan  
  

[![](https://1.bp.blogspot.com/-Cp6v65QZ514/XaXR365LlRI/AAAAAAAACsE/-fENPVlbUfYDa_sgnzM13j7ybH7dsFr1ACEwYBhgL/s320/self-xss-runconf2-www.codecrime.net_LI.jpg)](https://1.bp.blogspot.com/-Cp6v65QZ514/XaXR365LlRI/AAAAAAAACsE/-fENPVlbUfYDa_sgnzM13j7ybH7dsFr1ACEwYBhgL/s1600/self-xss-runconf2-www.codecrime.net_LI.jpg)

  
Jika anda sudah memilih subdomain disana nanti anda bisa memasukkan kresidensial akun bitly anda, contohnya seperti gambar di atas masukkan **email** dan **password**  

> bitly boleh di tulis berdasarkan kresidensial asli akun bitly anda. dan anda juga boleh tidak mengisi kresidensial bitly tersebut 

  

[![](https://1.bp.blogspot.com/-CCEloGpLWY8/XaXR3lo8m4I/AAAAAAAACsA/mUTKC_wisswV2AQkgU446TUJR59PFku0ACEwYBhgL/s320/self-xss-runwithBitLy-www.codecrime.net_LI.jpg)](https://1.bp.blogspot.com/-CCEloGpLWY8/XaXR3lo8m4I/AAAAAAAACsA/mUTKC_wisswV2AQkgU446TUJR59PFku0ACEwYBhgL/s1600/self-xss-runwithBitLy-www.codecrime.net_LI.jpg)

  
  
Jika semuanya syaratnya sudah terpenuhi, anda bisa share link bitly yang sudah di sediakan di terminal seperi gambar di atas, jika kalian tidak mengisi kresidensial bitly kalian bisa share link servernya contoh seperto gambar di atas **https://nubychan.serveo.net**  
jika target sudah membuka link tersebut, sekarang anda kembali ke terminal  
  

[![](https://1.bp.blogspot.com/-J3MGqsC-TkY/XaXYTgMELVI/AAAAAAAACsQ/ImeP0ypTLHQ6SjKwMzBn9BSK9S1fzPg-ACLcBGAsYHQ/s320/self-xss-runwithlink-www.codecrime.net_LI.jpg)](https://1.bp.blogspot.com/-J3MGqsC-TkY/XaXYTgMELVI/AAAAAAAACsQ/ImeP0ypTLHQ6SjKwMzBn9BSK9S1fzPg-ACLcBGAsYHQ/s1600/self-xss-runwithlink-www.codecrime.net_LI.jpg)

  
Jika berhasil akan ada tulisan seperti gambar di atas, dan sekarang buka folder self-xss tersebut  
  

[![](https://1.bp.blogspot.com/-yN38D8DZCRo/XaXYjKBedII/AAAAAAAACsU/4auzndOQIuAQrjILlh8-QYS5Qn16QJZGQCLcBGAsYHQ/s320/self-xss-getcoockies-www.codecrime.net.png)](https://1.bp.blogspot.com/-yN38D8DZCRo/XaXYjKBedII/AAAAAAAACsU/4auzndOQIuAQrjILlh8-QYS5Qn16QJZGQCLcBGAsYHQ/s1600/self-xss-getcoockies-www.codecrime.net.png)