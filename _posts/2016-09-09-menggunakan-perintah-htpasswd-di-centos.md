---
title: 'Menggunakan Perintah Htpasswd di CentOS 7'
date: 2019-11-15T19:52:00+01:00
draft: false
---

Menggunakan Perintah Htpasswd di CentOS 7. Pada tutorial cara install ELK Stack yang pernah saya tulis, mungkin kalian akan menemukan error saat menjalankan perintah htpasswd, command tidak ditemukan.  
  
  
  
  
Di CentOS 7, utility htpasswd disediakan oleh paket httpd-tools. Kalian bisa install menggunakan perintah  
  
sudo yum install httpd-tools  
Selanjutnya tinggal jalankan command htpasswd. Sebagai