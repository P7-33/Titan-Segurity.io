---
title: 'Membersihkan File Log Journal Systemd di Ubuntu'
date: 2019-11-13T16:37:00+01:00
draft: false
---

Membersihkan File Log Journal Systemd di Ubuntu. Log yang dihasilkan oleh systemd lambat laun akan terus menumpuk jika tidak diperiksa. Ini juga merupakan jeleknya sistem operasi yang menggunakan systemd.  
  
Memeriksa Log Journal Systemd  
Pertama, kalian bisa cek penggunaan disk oleh log journal menggunakan perintah berikut  
  
du -h /var/log/journal/  
atau  
  
journalctl --disk-usage  
Itu merupakan log