---
title: 'Belajar Program Bahasa PHP #3'
date: 2020-01-04T11:12:00+01:00
draft: false
---

[Belajar Programan Bahasa PHP #3](https://crotdiluar.blogspot.com/)

  

[![](https://1.bp.blogspot.com/-ckDyhf5hzPc/XgkDhmbhxVI/AAAAAAAAAV8/ESnQNTnrR4Ez4QrTFUC5LBfYOmGbFLibgCLcBGAsYHQ/s1600/Raka.png)](https://1.bp.blogspot.com/-ckDyhf5hzPc/XgkDhmbhxVI/AAAAAAAAAV8/ESnQNTnrR4Ez4QrTFUC5LBfYOmGbFLibgCLcBGAsYHQ/s1600/Raka.png)

  

  
Hey yoyo wasap my prenn balik lagi sama mimin yang paling handsome awoakwok, jadi kali ini mimin mau lanjutin articles yang kemaren yah gaes yang belom selesai sampai akhir.  
  
Nah untuk kalian yang baru aja lihat blogspot ini atau yang ketinggalan articles yang kita bahasa sekarang ini, kalian langsung bisa lihat aja yah articles nya [klik disini part 1](https://crotdiluar.blogspot.com/2019/12/mengenal-mengetahui-sejarah-bahasa.html) and [klik disini #2](https://crotdiluar.blogspot.com/2019/12/mengenal-mengetahui-sejarah-bahasa_19.html) nah kalo sudah dibaca dari 1 dan 2 mari kita lanjut articles yang selanjut nya mengenai _Program Bahasa PHP,_ oke langsung saja gaes ke articles nya.  
  
**_  
\- Membuat Program PHP_**  
Untuk membuat program PHP kita diharuskan untuk menginstal web server terlebih dahulu, nah buat kalian yang belom install web server ? kalian bisa download di website nya langsung [disini](https://apachefriends.org/en/xampp.html), nah gaes kalo sudah di download langsung aja kalian aktifkan xampp nya dengan cara tekan tombol _Start_ di sebelah kanan tulisan _Apache_ dan kalian tekan juga _Start_ di sebelah tulisan _MySQl_ untuk menjalankan server _MySql_  
  
  
  

[![](https://1.bp.blogspot.com/-nX9PZ7V_C7w/XgkJO-jnJFI/AAAAAAAAAWI/bqD1xX89U785hg-KxymENchGj_rCADH2ACLcBGAsYHQ/s320/kl.png)](https://1.bp.blogspot.com/-nX9PZ7V_C7w/XgkJO-jnJFI/AAAAAAAAAWI/bqD1xX89U785hg-KxymENchGj_rCADH2ACLcBGAsYHQ/s1600/kl.png)  
Contoh seperti ini jika kalian sudah tekan start yah gan  

  
  
oke gan sekarang saat nya kalian aktifkan Web Server _Apache_ dengan cara mengklik tombol _Admin_ yang di sebelah kanan baris pertama, lalu kalian pilih bahasa inggris yah gaes.  
  
Nah sekarang kalian buka notepad ++ atau bisa juga dcoder dan sublime text apapun itu yang kalian pake buat coding, disini kalian lihat yah gan bahwa membuat program _PHP_ tidak terlalu berbeda dengan _HTML_. Agar lebih jelas jelasinnya kalian coba perhatikan code program _HTML_ dan _PHP_ dibawah ini:  
  
**_\- Program HTML_**

  

FRI3NDS CYBER ARMY  

  

#### Contoh program HTML By ./CR0T\_D1LU4R

Hello, ini program HTML

  

  
  
**\- Program PHP**  
  

**FRI3NDS CYBER ARMY  **

**

#### Contoh program PHP By ./CR0T\_D1LU4R

**

****/\* Display a text messege \*/****

****echo "Hello, ini program bahasa PHP";****

****?>****

**  
  
jika anda perhatikan pada program FCA._PHP_ diatas terdapat program _HTML_, karena _PHP_ di sebut program scripting inilah sehingga mudah di sisipkan pada bahasa markup sekalipun.  
  
Perhatikan gambar dibawah ini. Sebagai _CATATAN PENTING_, agar anda dapat melihat hasil program _PHP_ ini dengan benar anda harus menyimpan filenya pada directory _/xampp/htdocs_ lalu memanggil file yang tadi kalian save dengan mengetikan _localhost/xampp/FCA.php_ nah seperti itu sesuaikan dengan nama file kalian yah cuk.  
  
Coba kalian perhatikan cuk, ketika file FCA._PHP_ kalian simpan di _/xampp/htdocs_ maka tampilan nya akan sama seperti file _HTML_ cuk dan cara pemanggilannya pun berbeda gan coba perhatikan sedikit code dibawah ini  
  

****/\* Display a text messege \*/****

****echo "Hello, ini program bahasa PHP";****

****_?>_  
  
n**ah karena kalimat itu hanya bisa di tampilkan ketika file FCA.PHP berada dalam htdocs (web server direktori0 dan pemanggilannya juga harus menggunakan localhost (karena web yang dipelajari masih bersifat ofiline makan penggunaaan localhostadalah sebagai rootnya).  
  
Mudah bukan untuk membuat program PHP? Tapi tunggu dulu ternyata program di atas hanya contoh yang sangat sederhana, untuk membuat website yang memiliki kompleksitas tinggi tentu saja akan lebih membutuhkan waktu dan pengalaman untuk menguasai PHP.baiklah setelah ini selanjutnya kita akan membahas mengenai variable dan konstanta didalam PHP untuk membuat suatu program membutuhkan variable atau objek-objek tertentu dimana setiap bahasa programan atau bahasa scripting sekalipun memiliki sintaks tersendiri untuk mendefinisikannya. Oleh karna itu Mimin yang Handsome akan bahasa secara bertahap, sehingga memudahkan anda untuk memahami PHP dari dasar.  
  
\-_ Komponen Dasar PHP_  
  
_\- Syntax Dasar PHP_  
  
sebelum kita menggunakan PHP kita akan mempelajari Syntax dasar PHP itu sendiri, ada beberapa aturan Syntax yang harus kita penuhi ketika kita membuat file program PHP  
  
_\- PHP Opening dan Closing Tag_  
  
Dalam _HTML_ anda di haruskan menulis opening dan closing tag seperti  dan dalam PHP pun anda harus melakukan opening dan closing tag sebagai awal dan akhir program PHP, nah disini mimin kasih liat code opening dan penutup perhatikan di bawah ini gayn.  
  
 /\*Opening tag PHP\*/  
/\* isi program php \*/  
/\* Closing Tag PHP by ./CR0T\_D1LU4R \*/  
?>  
  
Namun ada saatnya anda memperhatikan closing tag PHP ketika anda menggunakan Function include(). Fungsi Include() ini akan sangat menarik dan mempermudah penggunaan PHP, namun penggunaan fungsi ini di bahas nanti yah gaes agar anda dapat belajar setahap demi setahap  
  
_\- Comentar dalam PHP_  
  
PHP mendukung Komentar seperti bahasa _C_ dan _C++_ dan _Unix Shell-style (perl style)_ contoh nya mimin kasih di bawah ini yah gaes.  
  
  echo 'ini adalah contoh'; //contoh gaya komentar satu baris  
   /\* ini adalah contoh komentar lebih dari dua baris \*/  
    echo 'contoh lagi :v'; #contoh gaya komentar satu baris pada shell by ./CR0T\_D1LU4R  
 ?>  
  
nah gaes mungkin segitu aja dulu yah pembelajaranya, yang pasti nya mimin nanti akan sambung gaes karna pegel anjay nulis nya wkwk.  
  
nah gaes untuk kalian yang ingin Join ke _OFFICIALFCA_ kalian bisa langsung cek di website kami dan Join jika sudah memenuhi syaratnyaah, silakan cek website nya di bawah ini  
  
\- [https://official-fca.club/](https://official-fca.club/)  
  

\- Support me by subscribe to my Youtube Channel [Touch her](https://www.youtube.com/c/FRI3NDSCYBERARMY)

  
#Author **_./CR0T\_D1LU4R_**

**

**