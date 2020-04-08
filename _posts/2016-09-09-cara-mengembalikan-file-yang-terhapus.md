---
title: 'Cara Mengembalikan File Yang Terhapus di Flashdisk'
date: 2019-12-07T03:15:00+01:00
draft: false
---

  

Bila anda mempunyai flashdisk yang sudah terkena virus sudah pasti anda kesal apalagi isi dalam flashdisk itu sangat penting seperti skripsi anda. Mungkin anda juga bingung, ketika flashdisk anda masukkan ke komputer semua data-data anda hilang, folder-folder dalam flashdisk anda sudah berbentuk shortcut sehingga ketika anda buka  isinya tidak ada lagi. Namun ketika anda melihat properties dari flashdisk maka di sana terlihat banyak isinya tentu anda semakin bingung karena pada saat anda buka flashdisk isinya tidak ada.

  

Bila masalah di atas anda temukan maka anda tidak perlu takut, karena itu semua adalah ulah dari virus dan ketika anti virus anda mendeteksinya maka anti virus anda secara otomatis menghidden folder/file anda tersebut sehingga tidak bisa lagi anda buka. Namun semua folder/file anda tersebut masih bisa dikembalikan dengan menggunakan **CMD** (Command Prompt).

  

### Berikut adalah langkah-langkah mengembalikan data anda yang sudah terkena virus menggunakan **CMD :**

1.  Pilih View kemudian ceklist pada “Show Hiden Files And Folder” Lalu klik  Apply dan/ OK.
2.  Klik start > All Programs > Accessories pilih Command Prompt Bisa juga dengan menekan Windows + R
3.  Setelah Command Prompt terbuka maka ketikkan attrib -h -r -s -a /s /d f:     (Anda harus berada di drive C, Contoh: C:\\Documents and Settings\\Server> attrib -h -r -s -a /s /d f:) Kemudian tekan Enter
4.  Tunggu beberapa detik, kemudian buka flashdisk anda dan lihat data-datanya.

  

[![Cara Mengembalikan File Yang Terhapus di Flashdisk](https://4.bp.blogspot.com/-o_Q-4CYHN-A/WH4-d4gEG8I/AAAAAAAAF44/_ODFRV9M_EIPN2raykd99W3J-fHkfLRMwCLcB/s320/cara-mengembalikan-file-yang-terhapus.jpg "Cara Mengembalikan File Yang Terhapus di Flashdisk")](https://4.bp.blogspot.com/-o_Q-4CYHN-A/WH4-d4gEG8I/AAAAAAAAF44/_ODFRV9M_EIPN2raykd99W3J-fHkfLRMwCLcB/s1600/cara-mengembalikan-file-yang-terhapus.jpg)

Cara Mengembalikan File Yang Terhapus di Flashdisk
--------------------------------------------------

  

Bila datanya belum kembali maka maka pindahkan drive C menjadi Drive dimana Flashdisk anda  (biasanya ada di F) Caranya ikuti langkah berikut :

1.  apabila posisi flash disk di komputer atau laptop ada di drive F, maka (sebagai contoh):       C:\\Documents and Settings\\Server> F: kemudian enter 
2.  maka akan pindah ke drive F:\\> 
3.  Setelah berada di posisi drive flashdisk kemudian ketik perintah yang sama seperti diatas tadi , namun untuk f: yang berada di belakang dihilangkan. Sebagai contoh : F:\\> attrib -h -r -s -a /s /d 
4.  kemudian tekan Enter.
5.  Selesai

  

Bila anda  kurang paham menggunakan CMD maka anda bisa juga menggunakan softwere seperti Get Data Back, Recovery, atau pun software yang lainnya.