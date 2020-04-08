---
title: 'Cara Membuat Animasi Gradasi Warna di SVG icon dengan CSS'
date: 2019-10-29T21:11:00+01:00
draft: false
---

  
  
#Contoh1 > a:before {  
\-webkit-mask-image:url("data:image/svg+xml,");  
background:#de0985;  
margin-right: 10px;  
display: inline-block;  
width: 60px;  
height: 60px;  
vertical-align: -5px;  
background-repeat: no-repeat!important;  
content: '';  
}  
#Contoh1 > a:hover:before{  
background:green;  
}  
#Contoh2 > a:before {  
\-webkit-mask-image:url("data:image/svg+xml,");