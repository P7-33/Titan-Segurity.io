---
title: '25 Outlook 2016 Command Line Switches You Have to Know'
date: 2020-01-21T01:37:00+01:00
draft: false
---

![outlook-2016-cmd](https://static.makeuseof.com/wp-content/uploads/2016/09/outlook-2016-cmd.jpg)

You can get more out of Microsoft Outlook by learning how to use command line switches.

**Unlock the free "100+ Essential Windows CMD Commands" cheat sheet now!**

This will sign you up to our newsletter

Enter your Email

Unlock

[Read our privacy policy](//www.makeuseof.com/legal/)

The command line interface can seem intimidating, especially if you aren’t particularly familiar with using it. However, it can offer major benefits if you’re willing to learn the basics.

Command line switches can be used in Outlook to perform all kinds of tasks. Whether you’re troubleshooting a problem or just trying to speed up your normal usage, these switches offer serious advantages.

Here are 25 command line switches for Outlook to get started with.

Introduction to Run Commands
----------------------------

The easiest way to input a command line switch is by using a Run command, which is essentially a single-line version of the [full command line interface](//www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line/).

In Windows 10, you can open a new Run command by typing Run into the search bar, or by using the shortcut **Windows key + R**.

You should see this window — simply input your desired switch into the **Open** field and press Enter to execute it.

Now let’s take a look at how to perform some tasks using this tool!

Sending Emails
--------------

Command line switches can be used to speed up the process of sending emails. To compose a new message, enter the following into the Run dialog:

```
outlook.exe /c ipm.note
```

This will generate a blank Outlook email. It’s also possible to add the name of the email’s recipient by adding an extra `**/m**` switch onto the end of the command:

```
outlook.exe /c ipm.note /m dvader@empire.org
```

The result is a new Outlook email with the recipient filled in:

You can even add an attachment by using the `**/a**` switch and specifying its disk location.

```
outlook.exe /m artoo@rebellion.net /a "C:\My Documents\deathstarplans.pdf"
```

Which results in the following email draft:

You may have noticed that `**ipm.note**` was left off the switch from the previous command. Unless Outlook receives specific instructions to attach the file to a different type of item, the program will assume that the user is trying to draft an email.

To attach content to a different item, [such as a task](//www.makeuseof.com/tag/use-outlook-simple-task-project-management/), all you need to do is add another switch to the command.

### Creating Other Items

By modifying the last element in the command used to send an email, you can create a variety of other Outlook items:

*   `**ipm.contact**` — Creates a new contact.
*   `**ipm.stickynote**` — Creates a new note.
*   `**ipm.task**` — Creates a new task.
*   `**ipm.appointment**` — Creates a new appointment.
*   `**ipm.activity**` — Creates a new journal entry.

Cleaning up Outlook
-------------------

Anyone who’s worked as a system administrator will tell you that certain employees can have a tendency to … adjust their computer station.

Whether they’ve been fiddling with settings that should go untouched or repetitive reminders that clog up the system, cleaning up this mess can be frustrating.

Fortunately, we can use switches to clean up some parts of Outlook without even touching the program. The following command will remove all names and email addresses from the Autocomplete register:

```
outlook.exe /cleanautocompletecache
```

There are plenty of other things that we can clean in Outlook by switching out `**/cleanautocompletecache**` for another switch:

*   `**/cleancategories**` — Deletes any custom category names and restores category names to their default labels.
*   `**/cleanclientrules**` — Deletes client-based rules.
*   `**/cleanserverrules**` — Deletes server-based rules.
*   `**/cleanrules**` — Deletes both client-based and server-based rules.
*   `**/cleanreminders**` — Clears and regenerates reminders.
*   `**/cleanviews**` — Deletes any custom views and restores the defaults.

Opening and Finding Files
-------------------------

Switches can be used to open individual files in Outlook without having to navigate through an email inbox. The following command will open either a message file using the MSG format or a saved search that uses the OSS format—just swap out **file-name**.

```
outlook.exe /f file-name
```

We can also swap out `**/f**` for `**/hol**` to open a HOL file, and `**/ical**` to open an ICS file.

Sometimes you might not have the file name of the content that you’re looking for. In this situation, you can use the `**/finder**` switch:

```
outlook.exe /finder
```

This will produce the **Advanced Find** window, which is a powerful search tool to find just about anything hidden away in Outlook.

Opening Outlook
---------------

Initializing Outlook from a Run command might shave a few seconds off the process, but that’s not the only reason you might want to use it. By taking advantage of switches, you can open Outlook and perform other useful tasks at the same time.

Enter the following into a Run dialog to open up Outlook with the Reading Pane disabled:

```
outlook.exe /nopreview
```

You can switch out `**/nopreview**` for `**/safe**` to disable both the Reading Pane and any active toolbar customizations.

Alternatively, you can initialize Outlook and open a specific folder by using the following command:

```
outlook.exe /select folder-name
```

Just replace **folder-name** with the title of a particular folder or reference like `**outlook:calendar**`.

One especially time-saving switch is `**/sniff.**` This switch opens Outlook, looks for new meeting requests in the inbox and adds anything it finds to the calendar.

You activate the switch like this:

```
outlook.exe /sniff
```

In the event that Outlook crashes, there’s a switch that can attempt to open the same profile and folders that were active before the crash:

```
outlook.exe /restore
```

Finally, if you want to initialize Outlook by using an Outlook window that’s already open (if one exists), you can use this command:

```
outlook.exe /recycle
```

Where is Cleanfreebusy?
-----------------------

You may notice that among these switches for Outlook 2016 the absence of a very powerful switch:

```
outlook.exe /cleanfreebusy
```

Unfortunately, this switch is not available in the 2016 edition of Outlook. Microsoft phased out this feature in the 2010 edition. There is not a direct replacement for this feature yet, perhaps in the future, there will be an alternative.

Further Steps Into the Command Line Interface
---------------------------------------------

Once you’ve used a few of these switches with Outlook, you’ll hopefully find that the command line isn’t as fearsome as it looks from a distance.

Learning the concept of inputting commands is the first step toward carrying out more complex tasks from the command line. Next, why not try using it to [take control of your network](//www.makeuseof.com/tag/reset-network-settings-windows/), [speed up your Windows system](//www.makeuseof.com/tag/7-common-tasks-windows-command-prompt-makes-quick-easy/), or [choose the perfect emoji](//www.makeuseof.com/tag/how-to-find-the-perfect-emoji-using-the-command-line/).

Read the full article: [25 Outlook 2016 Command Line Switches You Have to Know](https://www.makeuseof.com/tag/25-outlook-2016-command-line-switches-know/)

  
  
from MakeUseOf https://ift.tt/2TFYWVp  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)