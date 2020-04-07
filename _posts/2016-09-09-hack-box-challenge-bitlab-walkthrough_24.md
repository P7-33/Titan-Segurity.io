---
title: 'Hack the Box Challenge: Bitlab Walkthrough'
date: 2020-01-25T08:01:00+01:00
draft: false
---

In this article, we are going to crack the Gitlab Boot to Root Challenge and present a detailed walkthrough. The machine depicted in this Walkthrough is hosted on HackTheBox Website. Credit for making this machine goes to [Frey](https://www.hackthebox.eu/home/users/profile/33283) & [thek](https://www.hackthebox.eu/home/users/profile/4615). As the Machine is live, we don’t need to download it on our systems but we can take a look at the lab by clicking **[here](https://www.hackthebox.eu/home/machines/profile/207)**.

### **Penetration Testing Methodology**

*   **Network Scanning**
    *   Nmap Scan
*   **Enumeration**
    *   Directory Bruteforce using dirb
    *   Browsing the HTTP Service in Browser
    *   Decoding the JavaScript to extract credentials
*   **Exploitation**
    *   Enumerating the Repositories
    *   Finding the Database Query Script
    *   Manipulating the script to get the credentials
    *   Connecting to Machine using SSH
*   **Post Exploitation**
    *   Reading the User Flag
    *   Downloading the suspicious executable file
*   **Privilege Escalation**
    *   Reverse Engineer the executable using the Debugger
    *   Enumerating for the root credentials
    *   Connecting to Target Machine using SSH with root credentials
*   **Reading Root Flag**

### **Walkthrough**

### **Network Scanning**

From the Official HackTheBox Website,

**Static IP Address: 10.10.10.114**

Since we have the IP Address, the next step is to scan the target machine by using the Nmap tool. This is to find the open ports and services on the target machine and will help us to proceed further.

```
nmap -A -p- 10.10.10.114
```

![](https://i2.wp.com/1.bp.blogspot.com/-738z5Tgzv3o/XivdbNTgLHI/AAAAAAAAiVY/22UEfxJDGAIKvT6mPjyPJtfnORkV65v2gCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Here we performed an Aggressive scan coupled with the ping scan. After the scan, we saw that the port 22 and 80 are open. We have the SSH Service (22) as well as an HTTP Service (80) on the server.

This gave us a lay of the land. Now let’s get to enumeration.

### **Enumeration**

We start the Enumeration with a Directory Brute Force. We will be using the dirb tool for this attack.

![](https://i1.wp.com/1.bp.blogspot.com/-eu_Lp7IVvz0/XivdddFP47I/AAAAAAAAiV4/eVzF-lw5aLo1RbWu5tbd4ugHlXAyrnKuwCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

We see that the dirb helped us get some of the links that could be our potential entry points. We also see that we have the robots.txt file. It had a bunch of links in it. But since we have an HTTP Service, we decided to open the IP Address in the browser.

![](https://i1.wp.com/1.bp.blogspot.com/-BAqLhKcxyTQ/XivdhFavzSI/AAAAAAAAiWg/W3XJn0Dr-pIzBCIMg9mNqTB1OYWbewCxACLcBGAsYHQ/s1600/3png.png?w=687&ssl=1)

We find that the machine is running Gitlab on it. But as shown in the image given, there are some credentials that are required to get in. Back to the robots.txt, we see that we have the a /help/ link inside it. This was unusual so we decide to give it a look.

```
http://10.10.10.114/help/
```

Here we found a page named bookmarks.html. Let’s check it out.

![](https://i2.wp.com/1.bp.blogspot.com/-V-N5IQn1KxE/XivdhhCjDpI/AAAAAAAAiWk/Au-qyUTFTTYxfoVy5-2bS7mcb0ThqRz7wCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

There are a couple of links in this bookmarks.html page. But one that drew our attention was the Git Lab login. Clicking on the link was useless. So, it occurred to us that like it a link on an HTML page, there must be a reference link behind it. We used the Inspect Element Tool of the Firefox Browser to look at that Reference link.  There is some JavaScript code involved. But we were pretty sure that the credentials are hiding inside it somewhere.     

![](https://i1.wp.com/1.bp.blogspot.com/-MhBhWRDl_w4/XivdiIfZczI/AAAAAAAAiWo/K3Gi8cYSLuUMCWVeEmYwev8z7jp6TZ8zACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

We copied the code and looked for something that could decode these values for us.  We found this awesome [Deobfuscator for JavaScript](https://lelinhtinh.github.io/de4js/) online. We pasted the script inside it and it gave us the decoded values. In those decoded values we have the Login Credentials. 

![](https://i0.wp.com/1.bp.blogspot.com/-JAi11Xdcnwc/XivdiE2yiiI/AAAAAAAAiWs/jDT-ua_YiVY5-KSedxf40o4EB7_RvSQlQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

### **Exploitation**

We went back to the login page that we found earlier. We enter the credentials that we just found and logged in the GitLab.

**Username:** clave

**Password****:** 11des0081x

![](https://i2.wp.com/1.bp.blogspot.com/-U9Je4M9NlCU/XivdiqFgqwI/AAAAAAAAiWw/roT2E8v7AiY4opdcrWrsyGh5ZS1YWtSBgCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

After the successful login, we enumerated the Projects and found 2 repositories: **Profile and Deployer**. We need to enumerate those repositories as well. Let’s Start with the Profile repo. 

![](https://i0.wp.com/1.bp.blogspot.com/-ius6aFh4zIE/XivdjI4kJ9I/AAAAAAAAiW0/QTyTYWcfOAkekeAwl9cbgUL1mr8FSewiQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

We went inside the Profile Repo and then we saw that we have a Snippets Tab in the panel. So, we clicked on that to enumerate some snippets.

![](https://i1.wp.com/1.bp.blogspot.com/-LCSZYNfDTM0/XivdjMZsazI/AAAAAAAAiW4/p2kGEQk5tj0jbH-_BTmrf00DkCOGVPsQwCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Here we have an interesting code snippet that contains a Postgresql file. We examined the file to see that it contains a code that could be useful. So, we took the note of that code.

![](https://i1.wp.com/1.bp.blogspot.com/-g04ig8u2ypo/XivdaoDJ2CI/AAAAAAAAiVU/XBTA5M9_9XAS_cI-oBlUzLmEuShEIwjYgCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

We went back to the Profile Repository. It was kind-off empty so we went on to do some research on how to exploit the GitLab Repository. We tinkered with it and figured out a way. To do this, first, we need to create a new file in the repo as shown in the image given.

![](https://i1.wp.com/1.bp.blogspot.com/-SMQTpUdVv9M/Xivdaoi48RI/AAAAAAAAiVQ/mXNpnHeuMhk58PHZkr8Pp7ELZrcNxsBkQCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

We name the file as “**db.php**” and paste the PostgreSQL code that we found earlier in the Code Snippet Section and because we want to fetch the credentials form the database, we added the lines at the end to do so.

```
$db\_connection = pg\_connect(“host=localhost dbname=profiles user=profiles password=profiles”);  
$result = pg\_query($db\_connection, “SELECT \* FROM profiles”);  
$data = pg\_fetch\_all($result);  
print\_r($data)  
\>
```

![](https://i0.wp.com/1.bp.blogspot.com/-GEXtwnRHYRU/XivdbdVFOUI/AAAAAAAAiVc/bPkeS1sgFjIMZhmEwZnNp7J5LebDzXOLQCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

After making the appropriate edits, we move all the way down to the “Commit changes” button and click on it to reflect the changes in the file.

![](https://i0.wp.com/1.bp.blogspot.com/-fpyMD9Fk20c/Xivdb30eV7I/AAAAAAAAiVg/Pc4M4ULv0KQT9QyHjGc50Dl5AVsoIRh0ACLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

After we have successfully saved the PHP file with the code, we need to merge the file that we just created in the current working repository. For this, we need to create a Merge Request. It can be done using the “**Create merge request**” button on the Repository. This will result in the opening of a page, we filled in the necessary details. After that, we drag to the bottom of the page where we find a “**Submit merge request”** button as shown in the image. 

![](https://i0.wp.com/1.bp.blogspot.com/-CLKvI1ZsdHU/XivdcMir6UI/AAAAAAAAiVk/7Jc9yUtGhrEwvkJkwOYsKMvEDaiFUn96gCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

After submitting the merge request, we need to merge the commit in the root branch. For that, we have a “**Merge**” button right below the request that we just submitted.

![](https://i2.wp.com/1.bp.blogspot.com/-USvht7AwqSc/XivdcX1mysI/AAAAAAAAiVo/qZ2QIiMxYCIkHs6ZIfst3dbLmUeJ9oMYgCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

After clicking on that Merge button, we will now modify our URL to get to the PHP file that we just created. As shown in the image given below. Here we wrote the IP Address of the machine, followed by the name of the repository i.e., profile and lastly the name of the file that we created. Here we can see that we have the password of the user clave which was stored in the database. Cool!

```
http://10.10.10.114/profile/db.php
```

![](https://i0.wp.com/1.bp.blogspot.com/-R35uu5mCgk8/Xivdcqa3x_I/AAAAAAAAiVs/pouGq51E85kFeMhHpsfZTeGaqOS7sH3qwCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

### **Post Exploitation**

Now that we had the credentials of the user clave. So, it’s time to connect to the Target Machine via the SSH service. Establishing a connection was a breeze. After connecting, we do some enumeration using the **id** command. We listed all the directories and found the user.txt. This is the user flag. Congratulations! The battle is half won.

```
ssh clave@10.10.10.114  
c3NoLXN0cjBuZy1wQHNz==  
id  
pwd  
ls  
cat user.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-fIAS10E7WHU/XivddRvmhfI/AAAAAAAAiVw/1wBmUxsq9_IidsS3l3Brr8_Yo4p8_geCACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

When we were enumerating for the user flag, we saw an executable file named RemoteConnection.exe Let’s download the file to our system to have a better look at the executable. We used the SCP for transferring the RemoteConnection.exe to our system.

```
scp clave@10.10.10.114:/home/clave/RemoteConnection.exe /  
c3NoLXN0cjBuZy1wQHNz==
```

![](https://i0.wp.com/1.bp.blogspot.com/-F3P6yku_DMA/XivddS3DmkI/AAAAAAAAiV0/siPIH8-BYB0mzKex0kUSQkb2IB_iKo4cgCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

Now, that we have the executable we tired to run the file in out Windows Machine but as shown in the image we have the classic Access Denied!! Error.

![](https://i1.wp.com/1.bp.blogspot.com/-c-AgYwbpnVQ/XivdeK6iygI/AAAAAAAAiV8/KxNRy57g5moTXH6bgTVkul9Wpa_IhNx_QCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

### **Privilege Escalation**

Now we decided to Reverse Engineer the exe to get some information or to bypass the Access Denied!! In actuality we just wanted to know as this exe makes a connection to the server then it must have a set of credentials hidden in it. We are going to use an x32dbg Debugger for our Reverse Engineering operations.

![](https://i2.wp.com/1.bp.blogspot.com/-BWKLvVPzGvw/Xivde6-M4YI/AAAAAAAAiWA/EugZOXmYAJ0UwT3nPkZcRnKswfpNDDgqgCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

After opening the Debugger as shown in the image we locate the RemoteConnection.exe file in our Windows Explorer.

![](https://i0.wp.com/1.bp.blogspot.com/-PnCA8mctt4E/XivdfMJd88I/AAAAAAAAiWE/6dET_2oVAoA-F4EMfS5HN_lR0FFWHlE8gCLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

We open the executable inside the debugger and take a look around various text fields. In the search for some way to get through the Access Denied!! We click on the Run Button(Highlighted) to capture the response.

![](https://i0.wp.com/1.bp.blogspot.com/-soSbOfRxvcQ/XivdfLC88iI/AAAAAAAAiWI/1tpexhQATCs-1qLAS9wcLNMbHftiMZpZwCLcBGAsYHQ/s1600/25.png?w=687&ssl=1)

Here we take the instance and scan the Text Fields using the button (Highlighted) as shown in the image given below.

![](https://i1.wp.com/1.bp.blogspot.com/-bCnuLM3PqYs/Xivdfvg6hYI/AAAAAAAAiWM/GGnq-7w5Uyo2KrzAXPl4LnHJIzbtIrWBQCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

We see that we have the attempt for connecting to a server using the PuTTY Tools but then we got our Access Denied. This means that when it launches the PuTTY, it must have entered some set of credentials that are hiding from us. We need to find them.

![](https://i1.wp.com/1.bp.blogspot.com/-SwFhUO11BLE/Xivdf3PBfbI/AAAAAAAAiWQ/CGHe3tJQv44a9oWTEm20sP2RYkvyLIVXQCLcBGAsYHQ/s1600/27.png?w=687&ssl=1)

We check the different breakpoints to see if we can get way in. But it was not looking too good.

![](https://i0.wp.com/1.bp.blogspot.com/-O2vooGikdls/XivdgNZli5I/AAAAAAAAiWU/oI6QvdIYgmMbRVCuTOvUyGtJxL-vWWb-gCLcBGAsYHQ/s1600/28.png?w=687&ssl=1)

So, what we did was set up multiple Breakpoints and tried to analyze the instances. And we see that we have some SSH commands. So, we selected an instance to take a better look at the instance as we see that we have the SSH Password displayed in cleartext. This is probably not a secure way to handle credentials. 

![](https://i2.wp.com/1.bp.blogspot.com/-tlWi_MPBhQ0/Xivdg-RTj5I/AAAAAAAAiWY/i40-749Qwi4oEc7UkIChD8tAVwq9UUtawCLcBGAsYHQ/s1600/29.png?w=687&ssl=1)

Now that we have the root credentials, all that’s left to do is just SSH our way in and grab that root flag that is waiting for us. We logged in using the credentials that we found and then we quickly located the root flag!

```
ssh 10.10.10.114  
id  
ls  
cat root.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-zPMNegkfDSk/Xivdg1H3HBI/AAAAAAAAiWc/kC2e49sL7IwgdzLjOgwhxsyiA1KXkUTYgCLcBGAsYHQ/s1600/30.png?w=687&ssl=1)

This concludes this awesome Capture the Flag challenge. We learned lots of new things and we were provided with a scenario that could very much possible in a Real Life.

**Author**: Kavish Tyagi is a Cybersecurity enthusiast and Researcher in the field of WebApp Penetration testing. Contact [**here**](https://www.linkedin.com/in/kavish-tyagi-844239125/)

The post [Hack the Box Challenge: Bitlab Walkthrough](https://www.hackingarticles.in/hack-the-box-challenge-bitlab-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2t0YG8M