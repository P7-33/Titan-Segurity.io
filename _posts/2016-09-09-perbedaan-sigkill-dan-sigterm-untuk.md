---
title: 'Perbedaan SIGKILL dan SIGTERM untuk Menghentikan Proses di Linux'
date: 2019-11-08T17:43:00+01:00
draft: false
---

Perbedaan SIGKILL dan SIGTERM untuk Menghentikan Proses di Linux. Oke kali ini saya akan sharing sedikit mengenai SIGKILL dan SIGTERM. Keduanya sama-sama bisa digunakan untuk mematikan proses yang sedang berjalan, namun mekanisme nya berbeda.  
  
  
  
  
SIGTERM  
Secara default perintah kill akan mengirim sinyal SIGTERM. Namun secara spesifik SIGTERM bisa juga menggunakan perintah kill -15. Sebagai contoh