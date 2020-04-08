---
title: 'TUTORIAL CARA MEMBUAT POP UP DI ANDROID STUDIO || CATATAN HARIAN PELAJAR'
date: 2019-11-26T20:20:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-CjxieBYXzCg/Xd12ZCNJKeI/AAAAAAAAAYM/gCFKkzsejhkj7FdOma-foJcVl0RL22c3wCLcBGAsYHQ/s320/TUTORIALCARAMEMBUATMENUPOPUPDIANDROIDSTUDIO.PNG)](https://1.bp.blogspot.com/-CjxieBYXzCg/Xd12ZCNJKeI/AAAAAAAAAYM/gCFKkzsejhkj7FdOma-foJcVl0RL22c3wCLcBGAsYHQ/s1600/TUTORIALCARAMEMBUATMENUPOPUPDIANDROIDSTUDIO.PNG)

  
Halo semua.... disini saya akan membagikan tutorial cara membuat pop up di android studio.  
  
disini saya hanyaaa membagikan berdasarkan apa yang saya alami, saya menulis ini hanya karna supaya ingat saja bahwa saya pernah belajar ini (apodio oy).  
  
Untuk membuat menu pop up tidaklah susah teman...  
  
oke langsung saja saya akan membagikan tutorial cara membuat menu pop up di android studio  
by [Muhamad Ilham Saputra](http://milhamsptr.blogspot.com/)  
  
  
1\. buka android studio, kemudian setelah ini buat project baru(nama nya bebas, tp saya sarankan beri nama optionmenu saja biar enak mengikuti tutorial ini).  
  
2\. langkah selanjutnya, buat direktori bernama menu, klik kanan di folder res-new-directory. (ingat beri nama directory dengan nama "menu")  
  
3.  jika sudah, selanjutnya klik kanan pada directory menu yang ada di folder res, kemudian klik kanan-new-Menu resourcefile, klik finis, maka akan ada yang tampil, kemudian, isi file name dengan nama optionmenu (hanya itu saja yang di isi atau di ganti).  
  
5\. Selanjutnya, silahkan isi dengan coding berikut di optionenu.xml (isi dengan benar ya)  

[![](https://1.bp.blogspot.com/-Lx2GkNytTvg/Xd13CPzgtAI/AAAAAAAAAYU/gTRLUPqDrTgN1YeOyW3NE6nCgoK4kLg2gCLcBGAsYHQ/s320/optionmenuxml.PNG)](https://1.bp.blogspot.com/-Lx2GkNytTvg/Xd13CPzgtAI/AAAAAAAAAYU/gTRLUPqDrTgN1YeOyW3NE6nCgoK4kLg2gCLcBGAsYHQ/s1600/optionmenuxml.PNG)

  
6\. Kemudian, buat 3 activity menu di folder java, terus pilih nama package yang kita buat. klik kanan di package terus pilih new, pilih activity, dan pilih empty activity, kemudian isi dengan nama HelpActivity. setelah itu ulangi lagi cara seperti tadi, kemudian isi activity name nya, AboutActivity dan SettingActivity (dibuat satu-satu)  
  
7\. Kemudian jika benar maka akan seperti ini sususan folder nya  

[![](https://1.bp.blogspot.com/-iaW6q8OIIPE/Xd13zMW4y9I/AAAAAAAAAYg/RSncBYf7t0AkC4MAG7-kP7RbwXYcKHVuACLcBGAsYHQ/s320/TUTORIALCARAMEMBUATMENUPOPUPDIANDROIDSTUDIO2.PNG)](https://1.bp.blogspot.com/-iaW6q8OIIPE/Xd13zMW4y9I/AAAAAAAAAYg/RSncBYf7t0AkC4MAG7-kP7RbwXYcKHVuACLcBGAsYHQ/s1600/TUTORIALCARAMEMBUATMENUPOPUPDIANDROIDSTUDIO2.PNG)

  
  
8\. Isi mainActivity.java dengan coding ini..  

[![](https://1.bp.blogspot.com/-I6z99AE16KU/Xd15TGD0i3I/AAAAAAAAAY0/cx-x9BqZjpUgxKEZcuP6OpbS2k4uqLD0QCLcBGAsYHQ/s320/tutorial%2Bpopup.PNG)](https://1.bp.blogspot.com/-I6z99AE16KU/Xd15TGD0i3I/AAAAAAAAAY0/cx-x9BqZjpUgxKEZcuP6OpbS2k4uqLD0QCLcBGAsYHQ/s1600/tutorial%2Bpopup.PNG)

  

[![](https://1.bp.blogspot.com/-6oca0tBedG0/Xd15XlZb__I/AAAAAAAAAY4/JWlkviUXQjEHLZb7oPj5wTePXgSFWDtmgCLcBGAsYHQ/s320/tutorial%2Bpopup2.PNG)](https://1.bp.blogspot.com/-6oca0tBedG0/Xd15XlZb__I/AAAAAAAAAY4/JWlkviUXQjEHLZb7oPj5wTePXgSFWDtmgCLcBGAsYHQ/s1600/tutorial%2Bpopup2.PNG)

  
  
9\. Selanjutnya isi Androidmanifest yang ada di folder manifest dengan coding berikut...  

[![](https://1.bp.blogspot.com/-lopIJL1mRS8/Xd14MiGmS8I/AAAAAAAAAYo/wjFxnmOCOu0-NeT8qttsh2P5upf7jn_pACLcBGAsYHQ/s1600/tutorialpopup3.PNG)](https://1.bp.blogspot.com/-lopIJL1mRS8/Xd14MiGmS8I/AAAAAAAAAYo/wjFxnmOCOu0-NeT8qttsh2P5upf7jn_pACLcBGAsYHQ/s1600/tutorialpopup3.PNG)

  
  
10\. Langsung Run, jika berhasil maka tampilannya akan seperti ini... (ketika di running melalui HP, jika teman-teman belum mengetahui cara untuk menyambungkan nya ke hp, ada baik nya teman membuka tautan ini [Tutorial cara mengaktifkan debugging usb di hp android](https://milhamsptr.blogspot.com/2019/10/tutorial-mudah-untuk-mengaktifkan.html) agar teman tau cara mengaktifkan debbuging USB di HP)  
  
  
Oke sekian dulu tutorial cara membuat menu pop up di android studio, mohon maaf jika masih terdapat kesalahan, jika berkenan silahkan komentar, semoga bermanfaat, jangan lupa di share agar teman-teman kita yang lain mengetahuinya, terima kasih