---
title: 'How to Automate Tasks on Windows 10 to Save Time'
date: 2019-11-16T14:19:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

In a world of smart technology, we are missing out on a bunch of things if we are not doing automation right. Android has the [Tasker app for automation](https://beebom.com/how-automate-android-using-tasker/) that is now getting a new Rules feature; iOS already has a powerful Shortcuts app to automate a multitude of tasks and more. But those are smartphones, what about PCs? Well, Windows 10 has a similar tool called Task Scheduler which allows you to perform a host of tasks based on time, events, and various other conditions. So in this article, we bring you a detailed guide on how to automate tasks on Windows 10. Along with that, we have also shared a basic tutorial on PowerShell in the next section. Now having said that, let’s begin the article without further delay.  

Automation on Windows 10
------------------------

  

Before moving forward, let me summarily explain some broad points of this article. To automate tasks on [Windows 10](https://beebom.com/windows-10-updates/), **there are essentially two methods**. The first one is a native tool called Task Scheduler which is quite easy and straightforward. And the next method is automation through [PowerShell](https://beebom.com/how-change-powershell-color-scheme-windows-10/) which is a bit complex, but also feature-rich. Now having gone through the outline of the article, let’s jump right in.  

1\. Automate Tasks on Windows 10 Using Task Scheduler
-----------------------------------------------------

  

The best way to learn something is by solving problems. So, here we will **implement a basic task.** For example, let’s say every time we turn on our computer, it opens a [browser](https://beebom.com/best-windows-10-browsers/) and then heads to some [cool websites](https://beebom.com/cool-interesting-websites/). So all we have to do is automate this routine task so that we can save time and boatloads of clicks. Let’s begin.  

1\. Press the Windows key once and **type “Task Scheduler”**. Open the first result and pin it on your taskbar because you are going to need it all the time.  

![automate tasks on windows 10](https://beebom.com/wp-content/uploads/2019/11/1-1.jpg)

2\. The UI may look a bit daunting in the beginning, but just follow my instructions and you will be off to the races. Now, **click on “Create Task”** on the right panel.  

![2](https://beebom.com/wp-content/uploads/2019/11/2-2.jpg)

3\. After that, provide a name to your task and **check the box for “Run with highest privileges”**. It will not prompt UAC or ask for any administrator permission before running the task.  

![3](https://beebom.com/wp-content/uploads/2019/11/3-1.jpg)

  
  

  

4\. Now **switch to the “Triggers” tab** above and click on the “New” button.  

![automate tasks on windows 10](https://beebom.com/wp-content/uploads/2019/11/4-1.jpg)

5\. Here, **choose “At log on” option** from the drop-down menu and click on the “OK” button. You can also delay the task by a few seconds, but let’s just leave it for now. As a side note, I always delay my internet-related tasks by 30 seconds so that the computer can connect to WiFi and be ready in time.  

![5](https://beebom.com/wp-content/uploads/2019/11/5.jpg)

6\. Now, switch to the “Actions” tab and click on the “New” button. Here, **choose “Start a program”** from the drop-down menu as we will be opening [Google Chrome](https://beebom.com/chrome-updates/).  

![6](https://beebom.com/wp-content/uploads/2019/11/6.jpg)

7\. Next, click on the “Browse” button and **select Chrome from desktop** or any location.  

![automate tasks on windows 10](https://beebom.com/wp-content/uploads/2019/11/7.jpg)

8\. After that, enter your **website’s URL in the “Add Argument” box**. For example, you can type _beebom.com_ and click the “Ok” button. In case, you want to **open multiple websites** at once then just put a blank space in between and enter another website.

  
  

  
```
 beebom.com theverge.com
```  

![automate tasks on windows 10](https://beebom.com/wp-content/uploads/2019/11/8.jpg)

*   You can also add your [Spotify](https://beebom.com/spotify-tips-tricks/) playlist or just about anything you want. Just make sure to put a space in between the websites. Chrome will open these websites automatically the moment you log in to your computer. Do note that, **you can just write the domain name or provide the whole _https_ link**. Anything works!
  

```
 beebom.com theverge.com https://open.spotify.com/playlist/37i9dQZF1DX2Ja6eBQeGaS
```  

9\. Having done that, switch to the “Conditions” tab and **uncheck both the options under the “Power” section**. It will allow the PC to run the task irrespective of battery or charging status.  

![9](https://beebom.com/wp-content/uploads/2019/11/9.jpg)

10\. Finally, move to the “Settings” tab. Here, we don’t have to touch anything, but **make sure “Allow task to be run on demand” is checked**. Also, go through other options so that you can understand the scope of what you can do with Task Scheduler. Now, click on the “Ok” button.  

![10](https://beebom.com/wp-content/uploads/2019/11/10.jpg)

11\. You have successfully created a task to open your [favorite websites](https://beebom.com/cool-new-shortcuts-websites/) after turning on your computer. You can **find your task in the “Task Scheduler Library” on the left pane**l. If the task is not showing, hit the “Refresh” button on the action panel located on the right side.  

![17](https://beebom.com/wp-content/uploads/2019/11/17.jpg)

12\. Further, you can **test the task manually if it’s running properly by pressing the “Run” button** on the right panel. If it’s working fine then restart your computer and you will have your series of tasks automated in no time. Enjoy!  

![automate tasks on windows 10](https://beebom.com/wp-content/uploads/2019/11/18.jpg)

  
  

  

So this task was for opening websites in Chrome, but there can be several use-cases based on your daily routine. For example, you can choose to connect to a particular WiFi point automatically, create a task to empty recycle bin after a certain amount of days, you can also start [Office apps](https://beebom.com/microsoft-office-2019/) or just about anything you want. Granted, there are a lot of other things to learn, but **for most of the tasks, you will be following similar steps mentioned above**. The only changes will have to be made in the “Action” and “Triggers” tab, but apart from that everything remains similar. Also, I would advise you to tinker with different settings to understand Task Scheduling properly.  

2\. Automate Tasks on Windows 10 Using PowerShell
-------------------------------------------------

  

In the above section, we learned how to automate tasks using Task Scheduler. But there is a native **scripting tool on Windows 10 called PowerShell** which is quite advanced and versatile. You can go about doing anything with a few commands. I know many users dread seeing the blue screen of PowerShell, but believe me, it’s quite easy once you get the whiff. Let me just say, it’s not [hardcore programming](https://beebom.com/best-python-learning-courses-online/) so do not worry.  

Apart from that, there are some key differences between PowerShell and Task Scheduler. PowerShell is not an automation tool but a scripting tool. It still **requires Task Scheduler to automate its script**. Whereas Task Scheduler is a complete tool in itself where you can create scripts and also automate those tasks.  

Apart from that, in terms of performance, **Task Scheduler is quite fast** because it executes everything from the app. However, its scope is relatively limited as you can’t delve deep into other programs and features. So, if you have a small task at hand then Task Scheduler is great. However, **PowerShell is very dynamic and can interact with many programs** at once, but it’s relatively slow at executing those commands. So basically, on one hand, you get faster execution but have limited scope and on the other hand, you get versatile support, but slower execution. Nevertheless, here we will go through the same example as above to check how both fare against each other.  

*     
    
    ### Get Started with PowerShell Syntax
    
      
    
  

Let me begin with an example. What you are seeing below is a PowerShell command to open multiple websites in Chrome. Here, **_Start-Process _is a command to start a program** and _chrome.exe_ is the executable name of the program. After that, websites are provided with a blank space under double-quotes. Very similar to Task Scheduler, right? Easy peasy.  

```
Start-Process "chrome.exe" "beebom.com theverge.com"
```  

![11](https://beebom.com/wp-content/uploads/2019/11/11-e1573901366842.jpg)

You can also **add your Spotify playlist, favorite [subreddits](https://beebom.com/best-subreddits-subscribe-reddit/)** or anything you wish.  

```
Start-Process "chrome.exe" "beebom.com theverge.com https://www.reddit.com/r/Android   
https://open.spotify.com/playlist/37i9dQZF1DX2Ja6eBQeGaS"
```  

Now that you have understood the syntax and what different arguments of PowerShell command mean, let’s begin with the steps.  

*     
    
    ### Steps to Create PowerShell Script
    
      
    
  

1\. **Open a Notepad file** and paste the below command.

  
  

  
```
Start-Process "chrome.exe" "beebom.com theverge.com https://www.reddit.com/r/Android   
https://open.spotify.com/playlist/37i9dQZF1DX2Ja6eBQeGaS"
```  

![19](https://beebom.com/wp-content/uploads/2019/11/19.jpg)

2\. You can **change the website as per your preference**. And if you want to provide a different browser, right-click on the browser icon and open “Properties”. In the target box, copy the last _XXXX.exe_ part and paste it in the Notepad file. This way, you can find executable names for other programs as well.  

_**Note:** In case it’s not working, you can paste the whole address from the target box. Here’s an example of the Microsoft Edge browser. You can do this for any program._  

```
Start-Process "C:Program Files (x86)MicrosoftEdge BetaApplicationmsedge.exe"   
"beebom.com theverge.com"
```  

![14](https://beebom.com/wp-content/uploads/2019/11/14.jpg)

3\. Now, go to “File” on Notepad and click on “Save As”. Here, give a name to your script and then **add _.ps1 _extension at the end**. PS1 is the extension of PowerShell scripts. Also, make sure to keep the file name as one word.  

![20](https://beebom.com/wp-content/uploads/2019/11/20.jpg)

4\. Having done that, open Task Scheduler and **create a new task by following steps 1-5** mentioned in the above section. Once you are in the “Action” tab, choose “Start a program” from the drop-down menu and type _powershell.exe _in the Program/Script box.  

![15](https://beebom.com/wp-content/uploads/2019/11/15.jpg)

5\. Now, **right-click on the PS1 file** and open “Properties”. Here, you will find the file path in the location section. Copy it and add _filename.ps1_ at the end. Here is how it should look. We will need this address in the next step.

  
  

  
```
C:UsersBeebomDesktopbrowser.ps1
```  

![automate tasks on windows 10](https://beebom.com/wp-content/uploads/2019/11/21.jpg)

6\. **Replace the below address** with your address from the above step and paste it in the “Argument” box. After that, click the “Ok” button.  

```
\-windowstyle Hidden -file C:UsersBeebomDesktopbrowser.ps1
```  

![16](https://beebom.com/wp-content/uploads/2019/11/16.jpg)

7\. Finally, you are done defining the Action part using PowerShell script. Now, **follow the same steps from 9 to 12** from the Task Scheduler section. You can go ahead and test the script using the “Run” button. As I explained above, the PowerShell window might prompt a small popup window because it’s a tad slow in executing the script.  

So that’s how you can create a simple script on PowerShell and automate it using Task Scheduler. What I showed above is just the tip of the iceberg. You can do a lot more and the possibilities are endless. For example, **you can add commands to run a separate program, delete old files from certain folders**, [disable Windows 10 update](https://beebom.com/how-to-stop-windows-10-updates/) and other OS level services, enable maintenance services, and more using the same PS1 file. You no longer have to go back to Task Scheduler to tweak anything, just make changes in the PS1 file using Notepad and it will run all the changes. Awesome, right? In the coming days, we will share some cool PowerShell scripts to automate tasks on Windows 10 so stay tuned with us.  

Ace PowerShell Scripting and Automate Routine Tasks on Windows 10
-----------------------------------------------------------------

  

So that was our in-depth guide on how to get started with automation on Windows 10. There are many hidden tools that we can take advantage of and Task Scheduler is one of them. And if you happen to know a few tricks of PowerShell then you can create multi-program scripts that will save you a lot of precious time. Anyway, that is all from us. If you liked this guide and could learn something new then do let us know in the comment section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-automate-tasks-windows-10-save-time/)  
\[the\_ad id='1307'\]