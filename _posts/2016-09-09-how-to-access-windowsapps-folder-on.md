---
title: 'How to Access the WindowsApps Folder on Windows 10'
date: 2020-02-15T07:18:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

For a long time, Windows has been storing app data and cache files in the Program Files folder. However, with Windows 10, Microsoft has moved the app data storage to a sandboxed folder called WindowsApps. The said folder is primarily created for storing data of [modern apps](https://beebom.com/best-windows-10-apps/) like UWP, Electron, and PWAs. Further, the folder is locked out from user’s access to provide high data integrity and [security against malware](https://beebom.com/best-malware-removal-tools-windows/). Having said that, the surprising part is that you can’t access the folder even if you have the administrator privilege. So in this article, we bring you a step by step guide on how to access the WindowsApps folder on Windows 10.  

Access WindowsApps Folder on Windows 10
---------------------------------------

  

As I said, even if you are an Administrator, you can’t access the WindowsApps folder. It’s because the folder is ‘owned’ by the system. Other than Admin privilege, **there are other permissions too on Windows 10 like ownership, read and execute**, assign attributes, and more. So you need to share the ownership of the folder to your user account and then you can have access to the WindowsApps folder on Windows 10.  

1\. First off, open `C:Program Files` and you will find the “WindowsApps” folder. Now, right-click on it and **open “Properties”**.  

![Access WindowsApps Folder on Windows 10](https://beebom.com/wp-content/uploads/2020/02/4-access-windowsapps-folder-on-windows-10.jpg)

2\. Next, **move to the “Security” tab** and then click on the “Advanced” button.  

![Access WindowsApps Folder on Windows 10](https://beebom.com/wp-content/uploads/2020/02/5-access-windowsapps-folder-on-windows-10.jpg)

3\. Here, **select “TrustedInstaller”** from the Permission entries and then click on the “Change” button.  

![Access WindowsApps Folder on Windows 10](https://beebom.com/wp-content/uploads/2020/02/6-access-windowsapps-folder-on-windows-10.jpg)

4\. Now, **enter your account username in the “object name” box**. Do not mistake your username with the account name or Microsoft account. To find the correct name, open the `C:Users` location and check the folder name of your account. That’s your actual username.

  
  

  

![Access WindowsApps Folder on Windows 10](https://beebom.com/wp-content/uploads/2020/02/7-access-windowsapps-folder-on-windows-10.jpg)

5\. Next, **click on the “Check Names” button** and it will validate your details by adding the computer location. Now, click on the “Ok” button. In case, it throws an error then it means you are entering the wrong username. Enter the correct one and try again.  

![Access WindowsApps Folder on Windows 10](https://beebom.com/wp-content/uploads/2020/02/1-access-windowsapps-folder-on-windows-10.jpg)

6\. Now, **enable the checkbox for “Replace owner on…”** and click on the “Apply” and “Ok” button subsequently. It will apply all the changes and will share the ownership with you.  

![](https://beebom.com/wp-content/uploads/2020/02/2-access-windowsapps-folder-on-windows-10.jpg)

7\. Now, close the File Explorer and **open the WindowsApps folder again** and this time, you will be able to access the WindowsApps folder without any issue.  

![](https://beebom.com/wp-content/uploads/2020/02/3-access-windowsapps-folder-on-windows-10.jpg)

Access WindowsApps Folder and Delete Unnecessary Files
------------------------------------------------------

  

So that was our short guide on how to access the WindowsApps folder on Windows 10. As we saw above, the steps are quite simple and straightforward. You can further go ahead and delete files that have taken space excessively. While this tutorial was just about the WindowsApps folder, you can apply the same steps while accessing other folders owned by the system. So that is all from us. If you want to learn similar [tricks about Windows 10](https://beebom.com/beginner-tips-for-windows-10/) then go through our linked article. And if you are still facing some issues, do let us know in the comment section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-access-windowsapps-folder-windows-10/)  
\[the\_ad id='1307'\]