---
title: 'Cara Memeriksa Kondisi Baterai CMOS di Ubuntu'
date: 2019-11-13T14:58:00+01:00
draft: false
---

Cara Memeriksa Kondisi Baterai CMOS di Ubuntu. Kali ini saya akan sharing tutorial singkat bagaimana cara mengecek kondisi baterai CMOS di Ubuntu Linux.  
  
  
Caranya cukup simple, buka terminal dan jalankan perintah berikut  
  
cat /proc/driver/rtc | grep batt\_status  
Contoh output  
  
  
  
Jika batt\_status bernilai okay maka baterai CMOS masih dalam keadaan bagus. Namun jika output yang dihasilkan adalah