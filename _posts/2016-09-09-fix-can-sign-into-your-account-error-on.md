---
title: 'Fix ''We Can''t Sign Into Your Account'' Error on Windows 10'
date: 2019-12-16T06:50:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Of [many issues related to Windows 10](https://beebom.com/common-problems-windows-10-solutions/), I have personally been at the receiving end of this error: We Can’t Sign Into Your Account. It’s a frustrating issue that locks you out of your account, folders and valuable files. And the sad part is that it has been occurring for years, yet Microsoft has not been able to patch this widely reported issue. Thankfully, there are a few ways you can get your account back without losing any files. So in this article, I am going to show you how to fix ‘We Can’t Sign Into Your Account’ Error on [Windows 10](https://beebom.com/windows-10-updates/). The process is quite simple and I have explained the steps in detail so that you can easily resolve this issue by yourself. With all that said, let’s now jump to the guide.  

Fix ‘We Can’t Sign Into Your Account’ Error on Windows 10
---------------------------------------------------------

  

Here, we have mentioned three different methods that will help you fix the sign-in problem on Windows 10. But before that, **let me clarify, all your files, folders and drives are completely safe** and there is nothing to be worried about. Windows suffers from this issue when the user profile goes corrupt due to issues pertaining to Registry modification and damaged system files. Now having cleared that doubt, let’s begin with the first method that is the Registry hack.  

### 1\. Have You Been Signed in With a Temporary Profile? Try the Registry Hack

  

Since you are unable to log into your account, Windows has signed you into a temporary profile. **Using this profile, you can make a couple of changes** to restore the original profile.  

_**Note:** Even if you are not signed into a temporary profile, you can still access Registry through the Safe Mode. I have explained the steps to [boot into Safe mode](https://beebom.com/boot-windows-10-safe-mode/) in the next section (Step #1 to #3) so go through that and then go ahead with the below instructions._  

1\. Press “Windows” and “R” keys at once to **open the Run window**. Here, enter `regedit` into the text field and hit enter.  

![How to Fix 'We Can't Sign Into Your Account' Error on Windows 10 17](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-17.jpg)

2\. Next, **copy the below path and paste it into the address bar** of Registry Editor. After that, hit enter and you will be taken to the ProfileList folder. Under this folder, you will find entries with “S-1-5” initials. All these “S-1-5” folders are assigned for each user account profile on your PC.  

```
ComputerHKEY\_LOCAL\_MACHINESOFTWAREMicrosoftWindows NTCurrentVersionProfileList
```  

![How to Fix 'We Can't Sign Into Your Account' Error on Windows 10 17](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-16.jpg)

3\. Now, we have to find the original user profile that has been corrupted. Go through each “S-1-5” folder and **look for the corrupted username in ProfileImagePath**.

  
  

  

![1](https://beebom.com/wp-content/uploads/2019/12/1-5.jpg)

4\. Once you find the correct “S-1-5” folder, **double-click on the “State” item** and change the value data to `0`.  

![](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-12.jpg)

5\. Under the same folder, look for “RefCount” and change its value data to `0`. **If “RefCount” is not available** then right-click on the main window and click on New -> DWORD (32 bit) and manually change the name to `RefCount`. After that, enter `0` in the value data.  

![How to Fix 'We Can't Sign Into Your Account' Error on Windows 10 17](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-15.jpg)

6\. Now, **close the Registry and restart your computer**. This time, ‘We Can’t Sign Into Your Account’ error should be gone. Just log in to your account normally and you will be able to access all your files.  

### 2\. Recover Your Account Through Safe Mode on Windows 10

  

1\. If you are signed into the temporary profile, open the Power option from the Start menu. Now **press and hold the “Shift” button and click on “Restart”**. Release the “Shift” key only when you see “Please Wait” on your screen.  

_**Note:** If you are not signed into a temporary profile, then click on the Power menu in the login screen (located at the bottom-right corner) and proceed with the same instruction mentioned above._  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-11.jpg)

  
  

  

2\. Your Windows 10 PC will boot into the Advanced Options screen. Here, click on Troubleshoot and then open Advanced Options. Once you are there, **click on “Startup Settings”** then proceed with “Restart”.  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-10.jpg)

3\. On the Startup window, **press 4 key on your keyboard** to finally enter the Safe Mode in Windows 10.  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-9.jpg)

4\. In Safe Mode, **enter your password on the login screen as usual** and see if you are able to sign in to your account. If so, restart the computer and log in to your account in the normal mode. This time you should pass through the login screen.  

5\. In case, it didn’t work, boot back to Safe mode by following step #1 to #3 and **temporarily disable [all the antivirus](https://beebom.com/best-antivirus-for-windows/) installed on your system.** Just search for Windows Security and open it. Open “Virus and threat protection settings” and disable all the toggle including “Tamper” protection. If you are using a third-party antivirus, open it and disable all kinds of threat protection.  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-8.jpg)

6\. Next, open the Run window by pressing Windows and R keys at once. **Type `services.msc`in the text field** and hit enter.  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-7.jpg)

  
  

  

7\. On the Services window, **look for “Windows Defender Advanced Threat Protection” and** “Microsoft Defender Antivirus”. Right-click on each of them and open “Properties”. Now, change the Startup type to “Disabled”. Having done all of that, now restart your computer normally and check if you are able to sign in to your account on Windows 10.  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-6.jpg)

8\. If the above steps did not work then reboot into Safe mode again and **uninstall unknown applications**. You can do so by pressing “Windows” and “X” keys at once and then open “Apps and Features”.  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-5.jpg)

9\. Next, sort the applications by date and uninstall the recent applications. After that, go through the app list and **uninstall the programs that you have no idea about**. After that, restart the PC normally and check whether ‘We Can’t Sign Into Your Account’ Error is still there or gone.  

![2. Recover Your Account Through Safe Mode on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-4.jpg)

### 3\. Create a New User Account

  

If none of the above methods worked then you can **create a new account and move all your files from old account to the new profile**. This way, all your files, folders, and drives will be accessible. Here is how you can do it.  

1\. From the temporary profile that you are logged into, open Windows Settings from the Start menu and **navigate to Accounts -> Family and other users**. Here, click on “Add someone else to this PC” under the “Other users” section.  

![Resolve 'We Can't Sign Into Your Account' Error on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-3.jpg)

  
  

  

2\. After that, **click on “I don’t have this person’s sign-in information”** and then proceed with “Add a user without a Microsoft account”. Now, enter the username and password (optional) and click on “Next”. For example, I have specified “Arjun Sha” as my new username where I will move all my old files.  

![Resolve 'We Can't Sign Into Your Account' Error on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-2.jpg)

3\. Having done that, click on the newly created user account under the “Other users” section. Now, **click on “Change account type” and change it to “Administrator”**. Finally, click on “OK” and restart your PC.  

![Resolve 'We Can't Sign Into Your Account' Error on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-13.jpg)

4\. Now, log in to the new account and go through the initial setup. After that, open `C:Users` and open the old user account. Here, you will find all your documents, downloads and desktop files. **Copy all the folders -> Go back -> Open your new profile folder and paste everything**. That’s it.  

![Resolve 'We Can't Sign Into Your Account' Error on Windows 10](https://beebom.com/wp-content/uploads/2019/12/How-to-Fix-We-Cant-Sign-Into-Your-Account-Error-on-Windows-10-1.jpg)

5\. Now all your files and drives are accessible just like before but in a new user account. You can choose to remove the old profile from Account Settings (Step #1) as well. Also, **if you were using Microsoft account earlier** then you can sign back to your online account by navigating to Windows Settings -> Accounts -> Your Info. Here, click on “Sign in with a Microsoft Account” and you are done.  

Resolve ‘We Can’t Sign Into Your Account’ Error on Windows 10
-------------------------------------------------------------

  

So that was our 3-point guide on how to fix ‘We Can’t Sign Into Your Account’ Error on Windows 10. While two of the methods are aimed at fixing the problem, the third and last one is basically a workaround to get your files back. If you don’t want to [reset your Windows machine](https://beebom.com/reset-windows-10/) or [install Windows 10 from scratch](https://beebom.com/get-windows-10-key-free-cheap/) then creating a new user account is a better way to go. Anyway, that is all from us. If you are still facing some problems then comment down below and let us know. We will try to help you out.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-fix-we-cant-sign-your-account-error-windows-10/)  
\[the\_ad id='1307'\]