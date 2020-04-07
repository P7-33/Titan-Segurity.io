---
title: 'RansomCoin'
date: 2020-01-03T11:55:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-UC13nDaV1pU/XgJ3e7NHTPI/AAAAAAAARR0/bnkcjZwuq3ATZXGlQFYpHjCP88-0OwwjQCNcBGAsYHQ/s640/RansomCoinPublic_1_ransomware.png)](https://1.bp.blogspot.com/-UC13nDaV1pU/XgJ3e7NHTPI/AAAAAAAARR0/bnkcjZwuq3ATZXGlQFYpHjCP88-0OwwjQCNcBGAsYHQ/s1600/RansomCoinPublic_1_ransomware.png)

**RansomCoin - A DFIR Tool To Extract Cryptocoin Addresses And Other Indicators Of Compromise From Binaries**

  

  
Extracting metadata and hardcoded [Indicators of Compromise](https://www.kitploit.com/search/label/Indicators%20of%20Compromise "Indicators of Compromise") from ransomware, in a scalable, efficient, way with cuckoo integrations. Ideally, is it run during cuckoo dynamic analysis, but can also be used for [static analysis](https://www.kitploit.com/search/label/Static%20Analysis "static analysis") on large collections of ransomware. Designed to be fast, with low false positive for [cryptocurrency](https://www.kitploit.com/search/label/Cryptocurrency "cryptocurrency") addresses. Limited false positives for emails, urls, onions, and domains (which is pretty hard to make perfect).  
In short, this is fast and easy initial triage if you only want monetisation vectors.  
  
  
**Installation instructions**  
Please ensure you have Python3 installed.  
  
**In a Linux Virtual Machine**  
It is advisable to download and install a virtualizer such as [VirtualBox](https://www.virtualbox.org/wiki/Downloads "VirtualBox"). Install your desired [Linux virtual machine](https://www.osboxes.org/virtualbox-images/ "Linux virtual machine") (i.e. Lubuntu, Kali Linux, etc) then follow the instructions below.  
From the tools folder:

```
sudo apt-get install build-essential libpoppler-cpp-dev pkg-config python-dev python3-tlsh
``````
python3 -m pip install -r requirements.txt
```

Note: If you get an error saying No module named pip, try running

```
sudo apt-get install python3-pip
```

  
**Usage instructions**  
A tutorial video is available: [https://youtu.be/3pUDh5HvqVI](https://youtu.be/3pUDh5HvqVI "https://youtu.be/3pUDh5HvqVI")  
The following commands can be run from the "Tools" folder to analyse [malware samples](https://www.kitploit.com/search/label/Malware%20Samples "malware samples") located in this directory. This will run the code across all files in the directoy and provide feedback on the estimated time to completion via TQDM. You will need write access for a file called Ransomware.csv in the directory you are working in (which contains the results). It should be possible to run the code across read only malware files though, so only Ransomware.csv need write access.  
  
**Coinlector.py**  
After running coinlector.py the results are output to a file in the same directory called Ransomware.csv

```
python3 coinlector.py
```

View the results by running

```
less Ransomware.csv
```

  

[![](https://1.bp.blogspot.com/-UC13nDaV1pU/XgJ3e7NHTPI/AAAAAAAARR0/bnkcjZwuq3ATZXGlQFYpHjCP88-0OwwjQCNcBGAsYHQ/s640/RansomCoinPublic_1_ransomware.png)](https://1.bp.blogspot.com/-UC13nDaV1pU/XgJ3e7NHTPI/AAAAAAAARR0/bnkcjZwuq3ATZXGlQFYpHjCP88-0OwwjQCNcBGAsYHQ/s1600/RansomCoinPublic_1_ransomware.png)

  
Currently we are testing for:

*   Bitcoin Addresses (BTC)
*   Bitcoin Cash Addresses (BCH)
*   Monero Addresses (XMR)
*   Bitcoin Private Keys
*   Ethereum addresses (ETH)
*   Ripple addresses (XRP)
*   LTC addresses (LTC)
*   DOGECOIN addresses (DOGE)
*   NEO addresses (NEO)
*   DASH addresses (DASH)
*   Domains (Address)
*   Email Addresses (Email)
*   Onion Addresses (Address)

View URLs, email addresses, and cryptocurrency addresses by running the following grep commands.

```
less Ransomware.csv | grep URL
``````
less Ransomware.csv | grep Email
``````
less Ransomware.csv | grep Address
```

Grep for Monero addresses by running

```
less Ransomware.csv | grep XMR
```

The same command can be used to search for other cryptocurrencies using the abbreviations in the list above.  
  
**Tempuscoin.py**  
tempuscoin.py outputs a list of timestamped ransom transactions. The file TemporalRansoms.csv is created showing the sending and receiving Bitcoin addresses, the amount in BTC and its equivalent value in EUR, USD at the time of the transaction.

```
python3 tempuscoin.py
```

View the results by running.

```
less TemporalRansoms.csv
```

  

[![](https://1.bp.blogspot.com/-BUwm6Kt7kDY/XgJ3sNB3UXI/AAAAAAAARR4/wgD0coZIE5MjSGRNwn6zvVKmBamSc2JfQCNcBGAsYHQ/s640/RansomCoinPublic_2_temporal-ransoms.png)](https://1.bp.blogspot.com/-BUwm6Kt7kDY/XgJ3sNB3UXI/AAAAAAAARR4/wgD0coZIE5MjSGRNwn6zvVKmBamSc2JfQCNcBGAsYHQ/s1600/RansomCoinPublic_2_temporal-ransoms.png)

  
**Eventcoin.py**  
This code will probably need to be altered to be made usable with your own MISP instance. It uses PyMISP to create events from the Ransomware.csv file, and groups of events share the same name. The default is to create events that are not published, and then to add details by hand before publishing. YMMV.  
  

**[Download RansomCoin](http://libittarc.com/3EAc "Download RansomCoinPublic")**

**  
Regards**

**Kang Asu**