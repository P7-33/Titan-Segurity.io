---
title: 'Google Berencana Memblokir Konten Campuran Dengan HTTPS Di Browser
Chrome'
date: 2019-10-07T18:06:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-doy-6wJkkhw/XZttcEpYzMI/AAAAAAAACmM/8xmwKyHLFc4lhHNtjIR4jHkLIgIYQn7KgCLcBGAsYHQ/s320/google.jpg)](https://1.bp.blogspot.com/-doy-6wJkkhw/XZttcEpYzMI/AAAAAAAACmM/8xmwKyHLFc4lhHNtjIR4jHkLIgIYQn7KgCLcBGAsYHQ/s1600/google.jpg)

  
  
Baru-baru ini, Google telah terlibat dalam banyak perubahan privasi dan keamanan dalam Google Chrome. Yang paling penting dari ini adalah penekanan pada HTTPS untuk situs web. Sekarang, mereka telah mengumumkan langkah ketat lain dalam hubungan ini. Google bermaksud untuk memblokir konten campuran HTTPS dalam browser Chrome mereka.  
  
**Google Memblokir Konten Campuran**  
  
Dikabarkan, Google berencana untuk memblokir konten campuran untuk HTTPS di masa mendatang. Menurut [posting blog](https://security.googleblog.com/2019/10/no-more-mixed-messages-about-https_3.html) baru-baru ini oleh Tim Keamanan Chrome, Google pada akhirnya akan memblokir konten campuran seluruhnya dalam Chrome. Ini akan memastikan implementasi HTTPS sepenuhnya saja.  
  
**Apa itu Konten Campuran?**  
  
Sebagaimana dijelaskan secara [terpisah](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content), 'Konten Campuran' mengacu pada jenis konten di situs web yang menggunakan HTTPS tempat elemen tertentu pada halaman web memuat melalui HTTP.  
  

> Konten campuran terjadi ketika HTML awal dimuat melalui koneksi HTTPS yang aman, tetapi sumber daya lainnya (seperti gambar, video, stylesheet, skrip) dimuat melalui koneksi HTTP yang tidak aman. Ini disebut konten campuran karena konten HTTP dan HTTPS sedang dimuat untuk menampilkan halaman yang sama, dan permintaan awal diamankan melalui HTTPS.

  
**Bagaimana Pengaruhnya terhadap Keamanan Browser?**  
  
Meskipun, Chrome digunakan untuk memberi tahu pengguna tentang keberadaan konten tersebut. Itu tidak bisa melindungi pengguna dari potensi kejahatan konten HTTP di halaman web. Dengan demikian, keberadaan konten tersebut menurunkan tingkat keamanan sebagaimana dipastikan dengan situs HTTPS lengkap.  
  

> Meminta sub-sumber daya menggunakan protokol HTTP tidak aman melemahkan keamanan seluruh halaman, karena permintaan ini rentan terhadap serangan man-in-the-middle, di mana seorang penyerang menguping pada koneksi jaringan dan melihat atau memodifikasi komunikasi antara dua pihak.

  
Akhirnya, keberadaan konten semacam itu bahkan dapat memungkinkan musuh mengambil kendali penuh atas halaman yang terpengaruh. Google menjelaskan bahwa konten tersebut juga memengaruhi keamanan browser UX. Browser tidak dapat menampilkannya sebagai HTTPS, atau HTTP.   
  
**Implementasi Untuk Terjadi Secara Bertahap**  
Meskipun Google telah mengumumkan rencana mereka untuk memastikan tidak ada konten yang tercampur, itu akan dilakukan dalam sejumlah langkah berbeda. Akibatnya, situs web HTTPS dengan konten campuran memiliki cukup waktu untuk memodifikasi halaman yang terpengaruh. Sesuai dengan timeline yang diungkapkan, pada awalnya, Google akan meluncurkan pengaturan bagi pengguna untuk membuka blokir konten campuran di situs.   
  
Ini akan berlangsung dengan rilis Chrome 79 pada Desember 2019. Kemudian, dengan Chrome 80, Google akan memblokir sumber daya audio / video yang gagal dimuat di HTTPS secara default.   
  
Pengguna masih dapat membuka blokir konten melalui pengaturan yang diberikan. Namun, itu akan memungkinkan gambar campuran, di mana browser akan meminta situs sebagai 'Tidak Aman'. Akhirnya, dengan Chrome 81 datang pada Februari 2020, Google akan memblokir gambar campuran juga. Untuk kenyamanan, Google telah berbagi panduan terperinci untuk [bermigrasi ke HTTPS](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/enable-https) dan [mencegah konten campuran](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/fixing-mixed-content) juga  
  
  
  

>