---
title: 'HOWTO : VirtualBox on Ubuntu, Kali and macOS'
date: 2020-02-04T05:44:00+01:00
draft: false
---

  
  
**(A) Virtualbox guest on Ubuntu, Kali and macOS**  
  
  
  
On Kali Linux 2020.1 guest, you are not required to install the "Guest Additions CD Image". However, Ubuntu and macOS are required to do so.  
  
  
  
On Virtualbox guest with "Shared Folder" feature enabled, you are required to run the following command on the guest and then reboot the guest.  
  
  
  
`sudo usermod -aG vboxsf $USER`  
  
  
  
**(B) Virtualbox host on Kali linux 2020.1**  
  
  
  
You are also required to install the following packages on the Kali Host :  
  
  
  
`sudo apt install virtualbox virtualbox-guest-additions-iso virtualbox-ext-pack virtualbox-qt virtualbox-dkms`  
  
  
  
The default Virtualbox theme will not displayed properly with Kali Linux xfce's dark theme. You are required to run the following command to make it displaying properly on the host.  
  
  
  
`sudo sed -i "s/virtualbox \%U/virtualbox \-style Fusion \%U/g" \  
  
/usr/share/applications/virtualbox.desktop`  
  
  
  
**(C) Update bash script for Ubuntu and Kali**  
  
  
  
On Ubuntu, you are required to install "git" beforehand.  
  
  
  
`sudo apt install git`  
  
  
  
On Kali, you are required to install "reboot-notifier" beforehand.  
  
  
  
`sudo apt install reboot-notifier  
  
  
  
git clone https://github.com/samiux/update-scripts  
  
  
  
cd update-script  
  
  
  
chmod +x update_*`  
  
  
  
When you are using Ubuntu, run :  
  
  
  
`sudo ./update_ubuntu`  
  
  
  
When you are using Kali, run :  
  
  
  
`sudo ./update_kali`  
  
  
  
That's all! See you.