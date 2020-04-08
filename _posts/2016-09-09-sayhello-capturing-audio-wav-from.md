---
title: 'Sayhello - Capturing audio (.wav) From Target Using a Link'
date: 2019-10-12T04:34:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-5KPnAOexz2c/XaFDiKFcYEI/AAAAAAAACqI/3Qe4BLOKgZEeB9uudKkOHsuVTZY-TutVgCLcBGAsYHQ/s320/sayhello-run-www.codecrime.net%2B%25282%2529.png)](https://1.bp.blogspot.com/-5KPnAOexz2c/XaFDiKFcYEI/AAAAAAAACqI/3Qe4BLOKgZEeB9uudKkOHsuVTZY-TutVgCLcBGAsYHQ/s1600/sayhello-run-www.codecrime.net%2B%25282%2529.png)

  
Tool ini menghasilkan halaman HTTPS berbahaya menggunakan metode Serveo atau Ngrok Port Forwarding, bisa di bilang ini temannya **[Saycheese](https://www.codecrime.net/2019/06/saycheese-reach-photos-with-malicious.html) **saycheese sendiri ia berfungsi untuk mengtrack **File Gambar** sedangkan Sayhello **Audio (.wav)**  
**Bagaimana Tool Ini Bekerja?**  
  
Setelah pengguna memberikan izin mikrofon, tombol pengalihan situs web pilihan Anda dilepaskan untuk mengalihkan target sementara file audio kecil (sekitar 4 detik dalam format wav) dikirim ke penyerang. Ini menggunakan Recorderjs, plugin untuk merekam / mengekspor output dari simpul-simpul API Audio Web ([https://github.com/mattdiamond/Recorderjs](https://github.com/mattdiamond/Recorderjs))  
  
**Features**  
Port Forwarding menggunakan **Serveo atau Ngrok**  
**Installation Sayhello Tool**  
  
Untuk mendapatkan tool tersebut anda bisa lakukan cloning pada sebuah repository github berikut  
  
```
git clone https://github.com/thelinuxchoice/sayhello
```

[![](https://1.bp.blogspot.com/-rEl2irVNJQo/XaFGCXFgHuI/AAAAAAAACqk/asrFZT1LPa4AYYJx_hmxzkPr3sNWPlUNQCEwYBhgL/s320/sayhello-git-www.codecrime.net.png)](https://1.bp.blogspot.com/-rEl2irVNJQo/XaFGCXFgHuI/AAAAAAAACqk/asrFZT1LPa4AYYJx_hmxzkPr3sNWPlUNQCEwYBhgL/s1600/sayhello-git-www.codecrime.net.png)

  
**Running Sayhello Tool**  
  
Jika sudah melakukan cloning seperti di atas, anda dapat masuk kedalam directory tool tersebut dan jalankan perintah berikut, dalam kasus ini saya menggunakan **PARROT OS**   
  
```
cd sayhello                                                                                                                                                  bash sayhello.sh
```

[![](https://1.bp.blogspot.com/-xHZaUcSBIo4/XaFGDZjAeuI/AAAAAAAACq4/r5mmWyB_FJ0cGOoDb7LuKzHd7ep6i5tPwCEwYBhgL/s320/sayhello-run-www.codecrime.net.png)](https://1.bp.blogspot.com/-xHZaUcSBIo4/XaFGDZjAeuI/AAAAAAAACq4/r5mmWyB_FJ0cGOoDb7LuKzHd7ep6i5tPwCEwYBhgL/s1600/sayhello-run-www.codecrime.net.png)

  
  
Disana ada dua pilihan port forwarding, dalam kasus ini saya menggunakan **Serveo.net** anda juga bisa menggunakan ngrok tapi harus install ngrok terlebih dahulu, option perintah 1  
  
```
1
```

[![](https://1.bp.blogspot.com/-tMjaI6MHXx4/XaFGA_A6qoI/AAAAAAAACq0/OujeDUlTONY8B3xkWzSGQ8adzlv49xtcgCEwYBhgL/s320/sayhello-custom-www.codecrime.net.png)](https://1.bp.blogspot.com/-tMjaI6MHXx4/XaFGA_A6qoI/AAAAAAAACq0/OujeDUlTONY8B3xkWzSGQ8adzlv49xtcgCEwYBhgL/s1600/sayhello-custom-www.codecrime.net.png)

  
Lalu kalian bisa mengkonfigurasikan sendiri, seperti **distracting** dan **subdomain** seperti contoh gambar di atas, jika sudah maka akan muncul **Direct Link** seperti gambar di atas  
Jika sudah mendapatkan **Direct Link,** kalian bisa copy dan kirim ke target kalian  
  

[![](https://1.bp.blogspot.com/-nWHAiAl2Oo8/XaFGCRz_jAI/AAAAAAAACq4/s5oIVkHhqM0kamd5nosAS5FG1JghnJUlQCEwYBhgL/s320/sayhello-microphoneGet-www.codecrime.net.png)](https://1.bp.blogspot.com/-nWHAiAl2Oo8/XaFGCRz_jAI/AAAAAAAACq4/s5oIVkHhqM0kamd5nosAS5FG1JghnJUlQCEwYBhgL/s1600/sayhello-microphoneGet-www.codecrime.net.png)

  
Sebagai contoh saya sebagai target, saya masuk ke url tersebut dan pastikan target tersebut mengklik tombol allow agar tool ini bisa berjalan  
  

[![](https://1.bp.blogspot.com/-3DhaZ09dpMU/XaFGBEVD7gI/AAAAAAAACq4/eKtyieT38P0WVGWZsTeoxrszsMeiF98QwCEwYBhgL/s320/sayhello-audioFile-www.codecrime.net.png)](https://1.bp.blogspot.com/-3DhaZ09dpMU/XaFGBEVD7gI/AAAAAAAACq4/eKtyieT38P0WVGWZsTeoxrszsMeiF98QwCEwYBhgL/s1600/sayhello-audioFile-www.codecrime.net.png)

  
Kembali ke terminal kalian dan lihat, jika muncul **Audio File Received** berarti target meng **allow** kan popup tersebut, jika kita periksa ke directory **sayhello**  

[![](https://1.bp.blogspot.com/-oCogF9ASbFw/XaFGBNhOpgI/AAAAAAAACqw/GIkYVEe4m-AUffyeSXQLAIzH_GI-hN2sACEwYBhgL/s320/sayhello-getAudioFile-www.codecrime.net.png)](https://1.bp.blogspot.com/-oCogF9ASbFw/XaFGBNhOpgI/AAAAAAAACqw/GIkYVEe4m-AUffyeSXQLAIzH_GI-hN2sACEwYBhgL/s1600/sayhello-getAudioFile-www.codecrime.net.png)

**Boom**, kita mendapatkan audio tersebut dalam bentuk format (.wav), lalu kita buka file audio tersebut   
  

[![](https://1.bp.blogspot.com/-zEL-DNSbZiI/XaFJbqha_PI/AAAAAAAACrA/vrcHIwACJOodDPPE4kLBXoUVeBMbioQFgCLcBGAsYHQ/s320/sayhello-OpeningFileAudio-www.codecrime.net.png)](https://1.bp.blogspot.com/-zEL-DNSbZiI/XaFJbqha_PI/AAAAAAAACrA/vrcHIwACJOodDPPE4kLBXoUVeBMbioQFgCLcBGAsYHQ/s1600/sayhello-OpeningFileAudio-www.codecrime.net.png)

  
Tutorial Saycheese klik link [Disini](https://www.codecrime.net/2019/06/saycheese-reach-photos-with-malicious.html)