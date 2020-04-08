---
title: 'EvilPDF - Embedding Executable Files In PDF Documents'
date: 2019-10-08T14:54:00+01:00
draft: false
---

   

[![](https://1.bp.blogspot.com/-lHu5m1gtaW0/XZyRAmY4rHI/AAAAAAAACmk/J4NPmjFgHm8EtXnIR25CFveyl8knrEiaACLcBGAsYHQ/s320/evilpdf-run-www.codecrime.net%2B%25282%2529.png)](https://1.bp.blogspot.com/-lHu5m1gtaW0/XZyRAmY4rHI/AAAAAAAACmk/J4NPmjFgHm8EtXnIR25CFveyl8knrEiaACLcBGAsYHQ/s1600/evilpdf-run-www.codecrime.net%2B%25282%2529.png)

  

  
**EvilPDF** adalah tool untuk melakukan executable terhadap document, evilpdf ini bersifat mengelabui target dengan method url ,  tool ini akan men generate malware dan mencoba memasukkan paksa dengan di binary malware dan akan meng convert ke base64  
  
**Installation EvilPDF Tool**  
  
Untuk mendapatkan tool ini anda bisa melakukan cloning pada repository berikut  
  
```
git clone https://github.com/thelinuxchoice/evilpdf
```

[![](https://1.bp.blogspot.com/-ZMIXtTBUX1Y/XZyQ_pV0rnI/AAAAAAAACm4/fm1Hbt7tz8ga4AJk8HwpN8s1aqH0IXwfwCEwYBhgL/s320/evilpdf-git-www.codecrime.net.png)](https://1.bp.blogspot.com/-ZMIXtTBUX1Y/XZyQ_pV0rnI/AAAAAAAACm4/fm1Hbt7tz8ga4AJk8HwpN8s1aqH0IXwfwCEwYBhgL/s1600/evilpdf-git-www.codecrime.net.png)

  
  
Jika sudah melalukan cloning lalu anda masuk ke directory evilpdf tersebut dan install package berikut  
  
```
apt-get install mingw-w64
```

[![](https://1.bp.blogspot.com/-V9-sRUjoaP8/XZyQ_mszpjI/AAAAAAAACnM/konvE46KI4kka_Sk8necJx2ChpxRRR-gACEwYBhgL/s320/evilpdf-install-www.codecrime.net.png)](https://1.bp.blogspot.com/-V9-sRUjoaP8/XZyQ_mszpjI/AAAAAAAACnM/konvE46KI4kka_Sk8necJx2ChpxRRR-gACEwYBhgL/s1600/evilpdf-install-www.codecrime.net.png)

  
  
Tunggu hingga proses install **mingw-w64** selesai  
  
**Running EvilPDF Tool**  
  
Jika sudah menginstall package wajib di atas, anda bisa jalankan tool tersebut dengan melakukan perintah berikut  
  
```
python evilpdf.py
```

[![](https://1.bp.blogspot.com/-hj_duupaxdc/XZyRBBpoWRI/AAAAAAAACnM/BTBjU8QVagUKLY8oweyMduBWQjkFRryXwCEwYBhgL/s320/evilpdf-run-www.codecrime.net.png)](https://1.bp.blogspot.com/-hj_duupaxdc/XZyRBBpoWRI/AAAAAAAACnM/BTBjU8QVagUKLY8oweyMduBWQjkFRryXwCEwYBhgL/s1600/evilpdf-run-www.codecrime.net.png)

  
  
Disini saya menggunkan default pdf yang sudah di sediakan oleh tool tsb, jika anda ingin menggunakan pdf anda, lalu masukkan pdf anda kedalam folder evilpdf tsb  
  

[![](https://1.bp.blogspot.com/-FKnhynAR9mE/XZyRBG5e2SI/AAAAAAAACnE/lYyvL4i6r_MRXwUQmYGnOh4pV3C9PT_iwCEwYBhgL/s320/evilpdf-runY-www.codecrime.net.png)](https://1.bp.blogspot.com/-FKnhynAR9mE/XZyRBG5e2SI/AAAAAAAACnE/lYyvL4i6r_MRXwUQmYGnOh4pV3C9PT_iwCEwYBhgL/s1600/evilpdf-runY-www.codecrime.net.png)

  
Disini saya masih menggunakan default, anda bisa tulis sesuai selera anda, baik itu **Exe, Phising Url, Serveo (Forwadding),** disini saya menggunakan subdomain dengan nama codecrime, jika sudah ia akan mengenerate malware secara otomatis  

[![](https://1.bp.blogspot.com/-_va3l_STk6M/XZyRBhkkz1I/AAAAAAAACnE/vIn-XxbIGQ0FUvim5R0zHjUSAsz57tShwCEwYBhgL/s320/evilpdf-runauto-www.codecrime.net.png)](https://1.bp.blogspot.com/-_va3l_STk6M/XZyRBhkkz1I/AAAAAAAACnE/vIn-XxbIGQ0FUvim5R0zHjUSAsz57tShwCEwYBhgL/s1600/evilpdf-runauto-www.codecrime.net.png)

Salah satu keunggulan dari tool ini ia akan mengenerate sendiri, baik converting, inject dll, jika proses pembuatan sudah selesai nanti akan ada url, yang bertujuan untuk mengelabui target  

[![](https://1.bp.blogspot.com/-ErDPvWoQwp0/XZyRB5YYhJI/AAAAAAAACnI/uBT4qaYoWTMPM21ZImwm5N8CGcmLdawqACEwYBhgL/s320/evilpdf-rungeturl-www.codecrime.net.png)](https://1.bp.blogspot.com/-ErDPvWoQwp0/XZyRB5YYhJI/AAAAAAAACnI/uBT4qaYoWTMPM21ZImwm5N8CGcmLdawqACEwYBhgL/s1600/evilpdf-rungeturl-www.codecrime.net.png)

  
  
Jika proses sudah selesai, akan muncul seperti gambar di atas, copy direct linknya dan share ke target kalian, tunggu sampai ia download file pdf tersebut dan lihat apa yang terjadii