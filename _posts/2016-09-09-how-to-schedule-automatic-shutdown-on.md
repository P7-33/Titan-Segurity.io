---
title: 'How to Schedule Automatic Shutdown on Windows 10'
date: 2019-12-13T06:34:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Believe it or not, many users have been asking for an automatic shutdown option in [Windows 10](https://beebom.com/windows-10-updates/), but sadly the feature has not been added yet. Many a time, Windows users simply forget to shut down their PC or you can say we are lazy enough to not do it. This may cause some problems like battery drain or heating. So, in this article, we are going to share a simple way that allows you to schedule automatic shutdown on Windows 10. You can schedule the shutdown based on your preferred time, event, and much more. So without further delay, let’s go ahead and learn about the steps in detail.  

Schedule Automatic Shutdown on Windows 10
-----------------------------------------

  

Since Windows does not have a native setting for scheduling automatic shutdown, **we are going to use the built-in Task Scheduler application** to achieve this task. As such, we have already covered the [basics of Task Scheduler](https://beebom.com/how-automate-tasks-windows-10-save-time/) in a separate tutorial, so go through that if you are not acquainted with this application. In this article, I will explain the steps from scratch so don’t worry if you are completely new to task scheduling. Now, without any delay, let’s begin.  

Automate Shutdown on Windows 10 with Task Scheduler
---------------------------------------------------

  

1\. Press the Windows key once and **type “Task Scheduler”** in the search box. Now, click on the first result.  

![Automate Shutdown on Windows 10 with Task Scheduler](https://beebom.com/wp-content/uploads/2019/12/How-to-Schedule-Automatic-Shutdown-on-Windows-10-1-1.jpg)

2\. Next, **click on “Create Basic Task”** located in the right pane.  

![Automate Shutdown on Windows 10 with Task Scheduler](https://beebom.com/wp-content/uploads/2019/12/How-to-Schedule-Automatic-Shutdown-on-Windows-10-3.jpg)

3\. After that, **give a name to your task** and click on “Next”. For example, I have entered “Automatic Shutdown”.  

![How to Schedule Automatic Shutdown on Windows 10 9](https://beebom.com/wp-content/uploads/2019/12/How-to-Schedule-Automatic-Shutdown-on-Windows-10-9-1.jpg)

4\. On the next window, **choose “Daily”** if you want the shutdown to happen once every day. You are free to choose other options as well based on your preference.

  
  

  

![1](https://beebom.com/wp-content/uploads/2019/12/1-3.jpg)

5\. After that, enter the time and date from when the task will be active. As you can see, I have scheduled the automatic shutdown at 11 every night starting from today. Keep in mind, the time field** only supports the 24-hour format** so enter your data in that specific format only.  

![How to Schedule Automatic Shutdown on Windows 10 ](https://beebom.com/wp-content/uploads/2019/12/2-4.jpg)

6\. On the Action tab, **choose “Start a program”** and click on “Next”.  

![start a program task scheduler](https://beebom.com/wp-content/uploads/2019/12/How-to-Schedule-Automatic-Shutdown-on-Windows-10-6.jpg)

7\. Now, **paste `shutdown.exe` in the Program/Script field** and `/s /f /t 60` in the Add arguments field. Basically, /s means shutdown, /f means force-close apps and /t means timeout which is capped at 60 seconds. It means the computer will shut down every night at 11 after a timeout of 60 seconds. You can change the timeout time be changing the number of seconds.  

![automatic shutdown](https://beebom.com/wp-content/uploads/2019/12/How-to-Schedule-Automatic-Shutdown-on-Windows-10-5.jpg)

8\. Now, you are almost done. Check all the details of your task and click on the “Finish” button.  

![3](https://beebom.com/wp-content/uploads/2019/12/3-1.jpg)

  
  

  

9\. If you want to **test if the automatic shutdown task is working as intended**, click on “Task Scheduler Library” and right-click on “Automatic Shutdown”. Now, click on “Run”. If you have configured everything properly, your PC will shut down in 60 seconds.  

![test automatic shutdown](https://beebom.com/wp-content/uploads/2019/12/How-to-Schedule-Automatic-Shutdown-on-Windows-10-2.jpg)

Shutdown Windows 10 on Scheduled Time
-------------------------------------

  

So that was our short guide on how to schedule automatic shutdown on Windows 10. As you can see, we have not used any third-party application, instead relied on a native application to achieve this task. There are many more things you can do with Task Scheduler and I hope you go through the detailed tutorial. If you liked this article, check out our article on [Windows 10 tricks](https://beebom.com/beginner-tips-for-windows-10/), where you can learn many such nifty tricks. Anyway, that is all from us. If you found the article interesting, do let us know in the comment section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-schedule-automatic-shutdown-windows-10/)  
\[the\_ad id='1307'\]