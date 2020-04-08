---
title: 'How to Install OneUI 2.0 Beta Based on Android 10'
date: 2019-10-25T13:16:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

OneUI was launched last year by Samsung and it was well-received by the tech community for its new design language and easy accessibility of features. Now, Samsung has released the OneUI 2.0 Beta based on Android 10 for the Galaxy S10 series. It looks quite refined with the new animation and gestures. You also get slow-motion selfies like iPhone 11 Pro and updated Digital well-being features like Focus Mode. So, if you want to be the early tester, follow our guide and install OneUI 2.0 Beta on your Galaxy S10 device right now.  

Install OneUI 2.0 Beta Based on Android 10
------------------------------------------

  

Before moving forward, let me clarify that OneUI 2.0 Beta update is **currently available only for Galaxy S10, S10+, and S10e**. Also, we have mentioned two ways to install the update. The first one is quite easy and straightforward and another one is a manual method. Be assured, **Knox does not trip with either method** so your warranty remains intact. Now having said that, let’s go ahead and learn about the steps.  

Install OneUI 2.0 Beta Through the Members App
----------------------------------------------

  

The OneUI 2.0 update is only available to users from the following countries as of now: **Germany, South Korea, United States, India, Poland, and France**. So, if you are from any of these countries, follow the steps below.  

1\. Open the Samsung Members app on your device and you should see a **“OneUI Beta Program” banner on the top**. If you don’t have the Members app pre-installed on your device then get it from the Galaxy Store ([Free](http://apps.samsung.com/appquery/appDetail.as?appId=com.samsung.android.voc)) or Play Store ([Free](https://play.google.com/store/apps/details?id=com.samsung.android.voc&hl=en_IN)).  

![Install OneUI 2.0 Beta Through the Members App 2](https://beebom.com/wp-content/uploads/2019/10/Install-OneUI-2.0-Beta-Through-the-Members-App-2.jpg)

2\. Tap on the banner and it should take you to the registration page. Here, **enroll your device** into the OneUI Beta program and shortly after that, you will receive an OTA for the OneUI 2.0 update.  

![Install OneUI 2.0 Beta Through the Members App](https://beebom.com/wp-content/uploads/2019/10/Install-OneUI-2.0-Beta-Through-the-Members-App.jpg)

3\. Now download the update and install it. Following that, your device will restart and boot into the new OneUI 2.0 interface. While your data will not be erased in the process, **make sure to back up your important files** as a precaution.  

![Install OneUI 2.0 Beta Through the Members App](https://beebom.com/wp-content/uploads/2019/10/Install-OneUI-2.0-Beta-Through-the-Members-App-1.jpg)

  
  

  

Install OneUI 2.0 Beta Manually
-------------------------------

  

In case, the update is not available in your country or the slots are full for beta testing then you can update your S10 series manually. However, keep in mind, the process is quite complex and you will need some degree of knowledge on how to flash system files and deal with Android recovery. Also, **there are chances of bricking your device** so proceed only if you are sure what you are doing.  

*     
    
    ### Install the Latest ASII Build
    
      
    
  

To install the OneUI 2.0 beta, **we need a specific “G97xFXXS3_ASII_” build** and that’s why we are downloading a United Kingdom (Country Code: BTU) firmware first. To check your build, open the dialer app on your Samsung device and type \*#1234#. If you are already on this build then you can skip this section altogether and jump straight to OneUI 2.0 installation in the next section. Also, Indian users will have to install this firmware first as we have not got the _ASII_ build update yet.  

1\. Download the [Frija Tool](https://forum.xda-developers.com/s10-plus/how-to/tool-frija-samsung-firmware-downloader-t3910594) from the XDA Forum and open it. It lets you download the latest firmware for Samsung devices.  

2\. Now, open the Frija tool and enter the model number of your device in the Model field (such as SM-G970F for S10e) and **enter “BTU” in the CSC field**.  Now, click on the “Check Update” button and then “Download” the file once it pulls the firmware details.  

![Install the Latest ASII Build](https://beebom.com/wp-content/uploads/2019/10/Install-the-Latest-ASII-Build.jpg)

_**Note:** To find your device’s model number, open Settings -> About Phone and look for your device Model Number._  

3\. After the download is complete, **install another tool called Odin** from [here](https://odindownload.com/). Click on “Odin 3.13.1” to download the latest version. It lets you flash system images on Samsung devices.  

4\. Now back to your device, open “Developer Options” from Settings and **enable “USB debugging”.** After that, turn off your device and then press and hold the Bixby and volume down buttons. The phone will boot into Download mode.  

![USB Debugging](https://beebom.com/wp-content/uploads/2019/10/USB-Debugging.jpg)

  
  

  

5\. Having done that, launch Odin on your PC and then **connect the smartphone**. Odin will automatically detect the device and will show the ports above.  

6\. Now, extract the UK firmware that you downloaded from the Frija tool. It will have five md5 files. You will have to import these images on the Odin tool. So go back to Odin and **select these files according to their naming scheme**. Make sure to select CSC\_OMC for CSC and HOME\_CSC file for Userdata. After that, click on the “Start” button and it will begin flashing the images. After some time, your phone will boot into the latest ASII build.  

_**Note:** Odin might not respond for a while, but keep patience. Due to large files, the processing takes some time. _  

![Install the Latest ASII Build 2](https://beebom.com/wp-content/uploads/2019/10/Install-the-Latest-ASII-Build-2-1.jpg)

*     
    
    ### Install the OneUI 2.0 Beta Build
    
      
    
  

Having updated your device to the latest ASII firmware, now you can update to the OneUI 2.0 beta build. You can verify the build number again by pressing \*1234# in the dialer app. Now, we are going to use the firmware files pulled by Cyber John from [XDA Forum](https://forum.xda-developers.com/s10-plus/how-to/galaxy-s10-sm-g975f-official-oneui2-10-t3980879). Here are the steps to follow.  

1\. First of all, download the OneUI 2.0 beta build for your device from here: [Samsung S10+](http://fota-secure-dn.ospserver.net/firmware/DBT/SM-G975F/nspx/755147d238284db7845f2afaa79653f1.bin?px-time=5df34a35&px-hash=f6b91ee18bee7ee948cb37fb171fff5a&px-wid=15420191014-WCC96257468&px-wctime=2019-10-14%2008:22:10&px-unum=&px-nb=UGtezEZ854jbmFcvWGxLEA==&px-nac=g2/EC9sWD3aMZZDMG4GJNHcvnSPhkuRTLmw/WdcM2ew=), [Samsung S10](http://fota-secure-dn.ospserver.net/firmware/DBT/SM-G973F/nspx/c894cf646b224687b69cb6ff7e572f89.bin?px-time=5df34a48&px-hash=0c8039654b927e07d1f731bb03c4b156&px-wid=13120191014-WSA65882803&px-wctime=2019-10-14%2008:22:29.0&px-unum=+UWyUdDwPHqUO+MuP/T4VqeXqs6t0h6YBawt6y2zDR0=&px-nb=UGtezEZ854jbmFcvWGxLEA==&px-nac=HB+eCAUEf7BOqKi6lS1sHw6Bii4N4si8KQfspQzXkv4=), [Samsung S10e](http://fota-secure-dn.ospserver.net/firmware/DBT/SM-G970F/nspx/35558eed138c411fbbe6ea1b94cbd038.bin?px-time=5df34a5b&px-hash=5ac0d6fa0b9635c79adefa11c3b72e1a&px-wid=75820191014-WSA65885859&px-wctime=2019-10-14%2008:22:49.0&px-unum=2FW3ezZxYmUvolmac0CfCi0Aqg7sX/l4AmJs0dXEnEU=&px-nb=UGtezEZ854jbmFcvWGxLEA==&px-nac=g2/EC9sWD3aMZZDMG4GJNJ3cLiQbZHk1BQfoG43U+3c=). After that, rename the downloaded file to **update.zip**.  

2\. Next, [**set up ADB**](https://beebom.com/how-to-install-adb-windows-mac/) on your PC. If you don’t know how to do it, follow our guide from the link.  

2\.  Now, turn off your device completely and then press and hold power, Bixby, and volume up buttons. You will soon **enter the recovery mode**. Now, choose “update via ADB” option.  

3\. After that, **connect your device to the PC** and open the ADB command window. Now, type _adb devices_ to check if your device is recognized by the PC. If it shows a serial number, you are good to go.

  
  

  

![Install the OneUI 2.0 Beta Build](https://beebom.com/wp-content/uploads/2019/10/Install-the-OneUI-2.0-Beta-Build.jpg)

4\. Next, **type _adb sideload update.zip_ and hit enter**. It will start installing the OneUI 2.0 Beta on your smartphone. After a few minutes, your will phone restart automatically and will boot into Android 10 based OneUI 2.0 Beta. Now go ahead and enjoy the new gestures and animation.  

_**Note:** Make sure the update.zip file is in the same ADB folder._  

![Install the OneUI 2.0 Beta Build 2](https://beebom.com/wp-content/uploads/2019/10/Install-the-OneUI-2.0-Beta-Build-2.jpg)

**SEE ALSO: [When Is My Phone Getting the Android 10 Update?](https://beebom.com/when-is-my-phone-getting-android-10-update/)**  

Enjoy the New Enhancements on OneUI 2.0
---------------------------------------

  

So that is how you can install OneUI 2.0 update on your Galaxy S10 device right now. As I mentioned above, the beta is only available to Galaxy S10 series as of now, but Samsung has announced that the update is coming to Note 10 series as well. So when the beta arrives for other devices, you can update your device through the Members app seamlessly. Anyway, that is all from us. If you want to learn more about new OneUI 2.0 features then stay tuned with us.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/install-oneui-2-0-beta-based-android-10/)  
\[the\_ad id='1307'\]