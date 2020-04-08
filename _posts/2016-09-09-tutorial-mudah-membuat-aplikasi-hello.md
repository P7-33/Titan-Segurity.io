---
title: 'TUTORIAL MUDAH MEMBUAT APLIKASI HELLO TOAST DI ANDROID STUDIO ||
CATATAN HARIAN PELAJAR'
date: 2019-10-19T14:40:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-SN8R03UjB54/XasLUbYgI7I/AAAAAAAAALc/hKMOLzQ9HeAegOY4X79nzqS2OVQs2m4wwCLcBGAsYHQ/s320/a.PNG)](https://1.bp.blogspot.com/-SN8R03UjB54/XasLUbYgI7I/AAAAAAAAALc/hKMOLzQ9HeAegOY4X79nzqS2OVQs2m4wwCLcBGAsYHQ/s1600/a.PNG)

wazzzaaaap gayssss  
  
Disini saya akan membagikan tutorial cara membuat Hello Toast di android studio, Membuat Hello toast ini sebenarnya adalah tugas di kampus saya, tujuan membuat ini adalah untuk membuat teman-teman mampu untuk mengerjakan-nya dengan mudah.  
  
Aplikasi Hello toast ini nantinya  memiliki 2 tombol dan 1 teks pada tampilan-nya, yang mana masing-masing memiliki fungsi yang berbeda, tombol toast akan menampilkan text yang melayang(float), sedangkan tombol count berfungsi untuk menampilkan angka dan jika di klik akan menambah jumlah angka yang ada di text view, oke langsungg saja saya akan membagikan tutorialnya.  
  
1\. Buka android studio, jika sudah terbuka maka tampilan seperti ini,  
  

[![](https://1.bp.blogspot.com/-uW2QGcu16ss/XasLiYu9qQI/AAAAAAAAALg/uX0F4V4-q5gPsm6BuZ00Nr4rUuhorHcgQCLcBGAsYHQ/s320/1.PNG)](https://1.bp.blogspot.com/-uW2QGcu16ss/XasLiYu9qQI/AAAAAAAAALg/uX0F4V4-q5gPsm6BuZ00Nr4rUuhorHcgQCLcBGAsYHQ/s1600/1.PNG)

  
2\. langsung teman-teman memilih empty activity, jika sudah isi nama project sesuai dengan keinginan teman  
  

[![](https://1.bp.blogspot.com/-9tJo3yosleU/XasLtpTMfaI/AAAAAAAAALo/Omxf_lqrLjk34d0VZllI7E0reolNPfLNgCLcBGAsYHQ/s320/2.PNG)](https://1.bp.blogspot.com/-9tJo3yosleU/XasLtpTMfaI/AAAAAAAAALo/Omxf_lqrLjk34d0VZllI7E0reolNPfLNgCLcBGAsYHQ/s1600/2.PNG)

  
3\. setelah itu buka file activity\_main.xml yang ada di folder res, pilih layout dan klik activity\_main.xml  
  
4\. lalu buang komponen yang ada di dalam layout(Helloword), lalu masuk ke mode text, ubah android.support.constain.ConstrainLayout menjadi text LinearLayout lalu tambahkan atribut baru android:orientation="vertical" . lebih jelas-nya akan menjadi seperti ini.  
  
5\. setelah itu masuk ke mode design, tambahkan 2 button dan 1 text view secara berurutan, button-text-button seperti ini,  

[![](https://1.bp.blogspot.com/-86OUKTxGcj8/XasMLgo1wYI/AAAAAAAAAL0/h2EuVLp3N6Q1TDrPSUDzoXDigi3qG1_-wCLcBGAsYHQ/s200/tutorial%2B4.PNG)](https://1.bp.blogspot.com/-86OUKTxGcj8/XasMLgo1wYI/AAAAAAAAAL0/h2EuVLp3N6Q1TDrPSUDzoXDigi3qG1_-wCLcBGAsYHQ/s1600/tutorial%2B4.PNG)

  
6\. Setelah itu, kembali ke mode text isi dengan persis seperti ini( Maaf gambar dibawah terpotong, teman-teman lanjutkan saja)  

[![](https://1.bp.blogspot.com/-NiBeSZqUdus/XasMhBHRNzI/AAAAAAAAAL8/AXkBPgJ4WlggsRQrJXtYaPUmLdq9RhOFgCLcBGAsYHQ/s400/tutorial%2B5a.PNG)](https://1.bp.blogspot.com/-NiBeSZqUdus/XasMhBHRNzI/AAAAAAAAAL8/AXkBPgJ4WlggsRQrJXtYaPUmLdq9RhOFgCLcBGAsYHQ/s1600/tutorial%2B5a.PNG)

  

[![](https://1.bp.blogspot.com/-tg9yb_GoPBM/XasMsllZVsI/AAAAAAAAAMA/n2fXfFNgE4cpE1xndd9LZwsQ2EK9it8gACLcBGAsYHQ/s320/tutorial%2B5b.PNG)](https://1.bp.blogspot.com/-tg9yb_GoPBM/XasMsllZVsI/AAAAAAAAAMA/n2fXfFNgE4cpE1xndd9LZwsQ2EK9it8gACLcBGAsYHQ/s1600/tutorial%2B5b.PNG)

  
7\. Setelah itu, jika kalian mendapati sintaks berwarna merah (digambar itu saya tidak memiliki sintaks warna merah, dikarenakan saya sudah membuat file dimen.xml), tak perlu risau itu artinya variabel belum terdekralasikan, untuk mengilangkannya teman-teman direktori res, values, buka file color.xml dan string.xml. lalu buat file baru di dalam values yang bernama dimen dengan cara klik kanan pada values , new, XML, Values XML file, terus berinama dimen  
  
8\. Setelah itu isi dengan text seperti di bawah ini,  
 - dimen.xml  

[![](https://1.bp.blogspot.com/-8_EqwvbY3lo/XasNn76eGXI/AAAAAAAAAMY/YtV5oTMf9jYFyKn9vgKqhSpGOG1WjooVQCLcBGAsYHQ/s320/tutorial%2B6.PNG)](https://1.bp.blogspot.com/-8_EqwvbY3lo/XasNn76eGXI/AAAAAAAAAMY/YtV5oTMf9jYFyKn9vgKqhSpGOG1WjooVQCLcBGAsYHQ/s1600/tutorial%2B6.PNG)

  
\- string  

[![](https://1.bp.blogspot.com/-kjBgygFa0K8/XasNxvl7yuI/AAAAAAAAAMc/z7Xlj64EfN4i84T8TgVZqE7zY54VQiXQQCLcBGAsYHQ/s320/tutorial%2B7.PNG)](https://1.bp.blogspot.com/-kjBgygFa0K8/XasNxvl7yuI/AAAAAAAAAMc/z7Xlj64EfN4i84T8TgVZqE7zY54VQiXQQCLcBGAsYHQ/s1600/tutorial%2B7.PNG)

  
\-color  

[![](https://1.bp.blogspot.com/-OY9SvBS2hFM/XasOVz7SncI/AAAAAAAAAMs/OzUPFFRcv04JY3myDMrnd2HSZ4FZp0nYQCLcBGAsYHQ/s320/tutorial%2B8%2Bcolor.PNG)](https://1.bp.blogspot.com/-OY9SvBS2hFM/XasOVz7SncI/AAAAAAAAAMs/OzUPFFRcv04JY3myDMrnd2HSZ4FZp0nYQCLcBGAsYHQ/s1600/tutorial%2B8%2Bcolor.PNG)

  
  
9\. jika sudah lihat ke mode design maka tampilan aku sesuai dengan di bawah ini  

[![](https://1.bp.blogspot.com/-owBWiJcmScM/XasOiNybLxI/AAAAAAAAAMw/O6Y2OwCdscUadCva7jsVwGFPxuf9kL7yACLcBGAsYHQ/s320/tutorial%2B9.PNG)](https://1.bp.blogspot.com/-owBWiJcmScM/XasOiNybLxI/AAAAAAAAAMw/O6Y2OwCdscUadCva7jsVwGFPxuf9kL7yACLcBGAsYHQ/s1600/tutorial%2B9.PNG)

  
  
  
10\. setelah itu buka file Mainactivity.java fi folder java, setelah itu isi dengan text berikut  
package harus sama dengan nama yang sudaha kita beri di awalan membuat project, disitu nama saya berikan tester)  

[![](https://1.bp.blogspot.com/-ePHOS2Mnbm4/XasOycOiILI/AAAAAAAAAM8/qnsm0G5lf7ETcJk_rtUwjmnl473Y5tHLQCLcBGAsYHQ/s400/java%2Brev.PNG) ](https://1.bp.blogspot.com/-ePHOS2Mnbm4/XasOycOiILI/AAAAAAAAAM8/qnsm0G5lf7ETcJk_rtUwjmnl473Y5tHLQCLcBGAsYHQ/s1600/java%2Brev.PNG)

11\. Setelah itu run aplikasi, maka tampilan-nya akan seperti ini ketika berhasil dijalankan  

[![](https://1.bp.blogspot.com/-tGzXza7Fih0/XasQd_5oDXI/AAAAAAAAANI/015v79MhBUYil7nqcyBGbT3YXN0zeh8JwCLcBGAsYHQ/s320/Screenshot_2019-10-19-20-06-34-19.png)](https://1.bp.blogspot.com/-tGzXza7Fih0/XasQd_5oDXI/AAAAAAAAANI/015v79MhBUYil7nqcyBGbT3YXN0zeh8JwCLcBGAsYHQ/s1600/Screenshot_2019-10-19-20-06-34-19.png)

  
Oke, sekian dulu TUTORIAL MUDAH MEMBUAT APLIKASI HELLO TOAST DI ANDROID STUDIO, kira-nya terdapat kesalah mohon berikan komentar-nya dibawah, agar bisa saya koreksi lagi. Terima kasih, see you