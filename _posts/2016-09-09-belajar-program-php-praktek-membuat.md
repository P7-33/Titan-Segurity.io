---
title: 'Belajar program php & praktek membuat uploader'
date: 2019-10-04T16:34:00+01:00
draft: false
---

B**_ahasa program php beserta fungsi / pemahaman function"nya_**  

[![](https://1.bp.blogspot.com/-kTcJQygEQJc/XZdmRE-vV0I/AAAAAAAAAPM/9OBSFyEIjK8Z1oSuId2vMBsqxith8MlcQCLcBGAsYHQ/s320/IMG-20190904-WA0006.jpg)](https://1.bp.blogspot.com/-kTcJQygEQJc/XZdmRE-vV0I/AAAAAAAAAPM/9OBSFyEIjK8Z1oSuId2vMBsqxith8MlcQCLcBGAsYHQ/s1600/IMG-20190904-WA0006.jpg)

  
Hey yo wasap ges balik lagi sama gua _./CR0T\_D1LU4R_ kali ini gua mau membahas + belajar program bahasa php ya gaes, nah disini gua cuma copy paste aja ya, karna pemateri nya itu member gua si Mr.CryszTaL#301  
  
Ok gaes jadi tanpa banyak bacot langsung aja kita ke materi  
  
Kali ini gw mau bahas tentang program php ea ;v dan masing² function dri program php itu sndiri  
  
Kalau kyta mau buat projeck php awalan sourcenya pake ini ya:  
Trus abis itu di situ ada echo ? Apa sih fungsi echo..  
  
Jadi echo itu buat nampilin kata² ya beda ama hateemel yg naro kata2 asal aja , kalau di php musti ada function khususnya jadi kalau mau buat kata² musti pake echo 'isi kata2 lu'; nah tanda ; buat nutup ya dan ruang terbuka ' ' itu buat mulai dan akhir dari kata2 yg lu katain sndiri  
  
Di echo kita jg blh nyisipin basic sc html kyk  
/

**

dan lainnya asal msh di di dlm echo '  
';  
  
Nah dsini kita mau buat uploader ya jadi pake function

  
Setelah itu ada   
Setelah itu ada   
Next setelah itu ada value="upload" nah value="upload" ini cm nama button/submit lu mau namain apa biasanya Crotsz atau apa lah sesuka kalean mau di ksh nama apa :v  
  
Di awal kita awalin functionnya kalo gk di tutup dia gk bakal jdi sbuah program php pasti crash :v alert / notice di chroome/browswr kalean , situs tidak di ketahui error lah ;v  
  
Next if ( $\_Post\['\_upl'\] nah if dia ngsh fungsi setalah tanda kurung $\_post jdi fungsi $ ini buat manggil / call ya karna di atas kan method nya post , nah sambung ke \['\_upl'\] jadi metod post nya kan di atas tentang upload file yg brusan kita buat dan == itu hasilnya upload  jdi post dan \_upl itu hasil uploader  
  
Nah setelah if pertama dia ada if kedua tapi dia ngelanjutin if yg pertama dgn di ksh ruang terbuka pake karakter { nah brti di if pertama dia punya function lg di bawahnya kbetulan di if kedua if(@copy($\_FILES\['file'\]\['tmp\_name'\]  nah jdi if kedua itu dia bertugas copy/hasil dri if pertama di copy di if kedua disini yg di copy yg di panggil  $\_FILE inget ea cug tanda $ buat call/manggil nah jdi if kedua itu intinya manggil / copy hasil file yg kita upload bakal lari ke dir / direktori karna disitu dia otw ke tmp\_name jdi dia kedirektori dri si uploader  dri manah berasal contoh kalau lo pusinh nih cuwg mksd gw :v  
  
https://crotdiluar.blogspot.com/images/uploader.php  
  
Jadi akases uploader.phpnya ada di dir https://crotdiluar.blogspot.com/images/ada disini ya  
  
Nah jdi function tmp\_name itu ketika kita upload dia bakal lari ke dir target.com/image/dsini pokoknya sama larinya ke tmpt akses uploader kita  
  
Lanjut abis tmp\_name'\],$\_FILES\['file'\]\['name'\] jadi setelah kita klik upload Filenya lari ke direktori tmpt uploader kita ya kyk contoh https://crotdiluar.blogspot.com/image/disini  
  
Trus ada karakter )) dobel knp sih ? Karna if kedua itu ada tanda kurung dua di if(@copy sama di ($\_FILES jadi kita wajib nutup ya brp jumlah karakter kurung yg terbuka :v  
  
Nah abis dri kedua if tadi dan akhiran )) ada karakter lg { sprti gw blng di atas kalau ada karakter ini { brti dia ngsh tugas / ada tugas di bawahnya ata ada function lg ya serah lu sih mau ngsh tugas apa lg karna nyampe disini function uploader bs tapi kalau lu mau biar ada variasinya ya di ksh ajah jadi disini { ngsh tugas  
  
Bahwasannya kedua if di atas gmnh sih setelah upload jadinya, nah jadi setelah upload bakal ada alert/notice dgn cara di ksh function echo'berhasil uplooad / success crotsz dimari'; :v nah akhiran ksh penutup ya } karna disini ada else function else sndiri buat ngsh tau kalau misal dir/directori kita di disable ama admin / setingan pacar :v eh setingan server itu sndiri :v jdi kita gk bs upload maka akan muncul function else itu sndiri jadi ksh notice lg { echo ' gagal crotsz ';}} nah ksh kurung dua ya lah kok dua ;v knp ? Ya  bukannya dah di tutup di ataa tdi sblm else ? ;v ya itu cm 1 coba liat lg ke atas teliti di bagian :  
  
Setelah =="Upload"){if(@copy  
  
Nah ada karakter yg terbuka kan ;v  jadi kita tutup di akhiran ya bambank :v biar gk error program uploadernya ;v  
  
nah tanda penutup dah rapeet smua dah ketutup smua :v brti udah  
  
Akhiran php psti ini ?>  
  
Jadi php itu bagian utamannya  
  
Pembuka  
Isi program  
  
?> penutup  
  
Ok wallaikumsallam :v materi kali ini  
  
source code yang kyta bahas:  
  
';echo '  
';echo '';echo '

';if( $\_POST\['\_upl'\] == "Upload" ) {if(@copy($\_FILES\['file'\]\['tmp\_name'\], $\_FILES\['file'\]\['name'\])) { echo '**Upload !!!**  
  
'; }else { echo '**Upload !!!**  
  
'; }}?>  
  
**_Thanks to:_**  
**_\- FRI3NDS CYBER ARMY_**  
**_\- ./CR0T\_D1LU4R_**  
**_\- _**Mr.CryszTaL#301
==========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

**