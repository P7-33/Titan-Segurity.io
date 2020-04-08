---
title: 'Install John the Ripper on Ubuntu'
date: 2019-10-01T14:20:00+01:00
draft: false
---

Install John the Ripper on Ubuntu
---------------------------------

  
  
cd src  
sudo apt-get install libnss3-dev  
sudo apt-get install libkrb5-dev  
sudo apt-get install libgmp-dev  
sudo apt-get install gcc  
sudo apt-get install openssl  
sudo apt-get install libssl-dev  
sudo apt-get install make  
sudo ./configure && make  
  
If needed:  
make -s clean && make -sj4