---
title: 'Colored rows and heatmap columns - sysinternas'
date: 2019-11-05T14:34:00+01:00
draft: false
---

#### Process list

[](https://www.blogger.com/u/1/null)Each row in the process list represents a running process on the local computer. Actually, that’s not technically accurate. As my friend and _Windows Internals_[](https://www.blogger.com/u/1/null) co-author David Solomon likes to point out, processes do not run—only _threads_[](https://www.blogger.com/u/1/null) can run. Threads—not processes—are the entities that Windows schedules for execution and that consume CPU time. A _process_[](https://www.blogger.com/u/1/null) is simply the container for a set of resources, including one or more threads. It’s also not accurate to refer to “active processes” or to “processes with running threads,” because many processes spend most of their lifetimes with none of their threads running or scheduled for execution. So each row in the process list really represents a process object on the system that has its own virtual address space and one or more threads that conceivably could execute code at some point. And as we’ll discuss later, the first few rows in the default (tree) view are exceptions. Going forward, I’ll refer to them as _running processes_.

##### Colored rows and heatmap columns

[](https://www.blogger.com/u/1/null)One of the first things that stands out in the process list is its use of color. Row colors distinguish different types or states of processes, and colored _heatmaps_[](https://www.blogger.com/u/1/null) within certain columns call attention to processes consuming resources.

[](https://www.blogger.com/u/1/null)[](https://www.blogger.com/u/1/null)A heatmap graphically highlights larger values in a table with shading or with different colors. The CPU Usage, Private Bytes, Working Set, and GPU Usage[2](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fn2a)[](https://www.blogger.com/u/1/null) columns each show a pale shade of a distinct background color. For example, the CPU column is a very light green. When a process consumes a significant percentage of the resource’s availability, Procexp highlights that number with a correspondingly darker background shade. In [Figure 3-2](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fig02)[](https://www.blogger.com/u/1/null), you can see how the darker shades in the CPU and memory columns call your attention to the two processes consuming those resources. Similarly, the column headers’ shading corresponds to the systemwide consumption of that resource. For example, the Working Set column header’s background color becomes darker when total working set usage increases, even if no single process is consuming a significant percentage of working set. You can disable the heatmap feature by unselecting View | Show Column Heatmaps.

[2](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fn2)[](https://www.blogger.com/u/1/null) The GPU Usage column is not displayed by default.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85MzBmZWhpcy90cGdnYXNyaS9jMmdwMGou)

[](https://www.blogger.com/u/1/null)**[](https://www.blogger.com/u/1/null)FIGURE 3-2**[](https://www.blogger.com/u/1/null) Two processes consuming resources and demonstrating Procexp’s heatmap feature.

[](https://www.blogger.com/u/1/null)Although you can configure which process types and states are highlighted and in what row color, these are the defaults:

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Light blue**[](https://www.blogger.com/u/1/null) Indicates processes (“own processes”) that are running in the same user account as Procexp. Note that although they’re running in the same user account, they might be in different Local Security Authority (LSA) logon sessions, integrity levels, or terminal sessions, and therefore are not all necessarily running in the same security context. Also note that if you started Procexp as a different user, other applications on the desktop will not be highlighted as “own processes.”

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Pink**[](https://www.blogger.com/u/1/null) Designates services. These are processes containing one or more Windows services.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Dark gray**[](https://www.blogger.com/u/1/null) Indicates suspended processes. These are processes in which all threads are suspended and cannot be scheduled for execution. Note that on Windows 8 and newer, the Process Lifetime Manager (PLM) regularly suspends “modern” or Universal Windows Platform (UWP) processes when they do not have focus. Also, processes that have crashed might appear as suspended while Windows Error Reporting handles the crash. (Don’t confuse this gray with the lighter gray color that, with default Windows color schemes, indicates the selected row when the Procexp window does not have focus.)

[](https://www.blogger.com/u/1/null)![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Violet**[](https://www.blogger.com/u/1/null) Denotes “packed images.” Procexp uses simple heuristics to identify program files that might contain executable code in compressed form, encrypted form, or both. Malware often uses this technique to evade anti-malware and then unpack itself in memory and execute. Note that sometimes the heuristics result in false positives—for example, with debug builds of Microsoft Visual C++ applications.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Brown**[](https://www.blogger.com/u/1/null) Indicates jobs. These are processes that have been associated with a job. A _job_[](https://www.blogger.com/u/1/null) is a Windows construct that allows one or more processes to be managed as a unit. Jobs can have constraints applied to them, such as memory and execution time limits. A process can be associated with at most one job. Jobs are not highlighted by default.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Yellow**[](https://www.blogger.com/u/1/null) Indicates .NET processes. These are processes that use the Microsoft .NET Framework. This indicator is not enabled by default.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Cyan**[](https://www.blogger.com/u/1/null) Indicates “Immersive” processes on Windows 8 or newer[3](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fn3a)[](https://www.blogger.com/u/1/null). These processes are “modern” or UWP processes, or in some other way they can interact with the “modern” app environment. Explorer.exe is usually thought of as a regular Win32 desktop process, but it renders the modern Start menu and is typically reported as an “Immersive” process.

[3](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fn3) According to the IsImmersiveProcess API.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Bright pink**[](https://www.blogger.com/u/1/null) Indicates protected processes. Protected processes are not highlighted by default.

[](https://www.blogger.com/u/1/null)If a process belongs to more than one of these color categories, the precedence order is Suspended, Immersive, Protected, Packed, .NET, Jobs, Services, Own Process. For example, if a process hosts a service and uses the .NET Framework, Procexp applies the highlight color associated with .NET processes because that has higher precedence than Services. Procexp requires administrative rights to recognize a packed image, a .NET process, or association with a job if the process is running at a higher integrity level or in a different user account from Procexp.

[](https://www.blogger.com/u/1/null)In addition to highlighting process types, Procexp highlights new processes and processes that have just exited. By default, when Procexp identifies a new process, it highlights its row in the process list with a green background for one second. When a process exits, Procexp keeps it in the list for one second, highlighted in red. Note that even though the process appears in the list, if it is highlighted in red, the process has already exited and no longer exists. You can configure how long the “difference highlight” lasts by choosing Difference Highlight Duration from the Options menu and entering a number from 0 to 9 in the dialog box. (See [Figure 3-3](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fig03)[](https://www.blogger.com/u/1/null).) Note that the actual duration also depends on the Procexp refresh interval. The difference highlighting changes only when the display is refreshed.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85MzBmZWhpcy90cGdnYXNyaS9jM2dwMGou)

[](https://www.blogger.com/u/1/null)**FIGURE 3-3** Difference Highlighting Duration dialog box.

[](https://www.blogger.com/u/1/null)[](https://www.blogger.com/u/1/null)To change whether a process type or difference is highlighted and in what color, choose Configure Colors from the Options menu. As indicated by [Figure 3-4](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fig04)[](https://www.blogger.com/u/1/null), you can enable or disable the highlighting of changes or process types by selecting or clearing the corresponding boxes. New Objects and Deleted Objects also refer to items appearing in the DLL view and Handle view. Relocated DLLs, which is not selected by default, applies only to DLL view. Click the Change button to display a color-picker dialog box to change the highlighting color for the corresponding highlight type. By clicking the Change button next to the

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85MzBmZWhpcy90cGdnYXNyaS9jNGdwMGou)

[](https://www.blogger.com/u/1/null)**FIGURE 3-4** Configure Colors dialog box.

[](https://www.blogger.com/u/1/null)Graph Background option, you can change the background color for all of Procexp’s graphical representations described throughout this chapter. The Defaults button restores Procexp’s default colors but leaves the check box selections as they are.

##### Updating the display

[](https://www.blogger.com/u/1/null)By default, Procexp updates dynamic attributes in the display once per second. Dynamic attributes are those that are likely to change regularly, such as CPU time. You can pause the updating by pressing the space bar; pressing space again resumes the automatic refresh. (Procexp’s status bar indicates when updating is paused.) You can trigger a one-time update of all the displayed data (dynamic _and_[](https://www.blogger.com/u/1/null) static attributes) by pressing F5 or clicking the Refresh icon in the toolbar. Finally, you can change the automatic refresh duration through the Update Speed submenu of the View menu. The available intervals range from 0.5 seconds to 10 seconds.

* * *

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85aXRwZWhpcy90cGphcy5yL2NnZ3A-) Tip

[](https://www.blogger.com/u/1/null)Manually updating the display combined with difference highlighting is a great way to see all new and deleted objects across a time span of your choosing. Pause the update, perform actions on the system, and then press F5 in Procexp.

* * *

##### [](https://www.blogger.com/u/1/null)Default columns

[](https://www.blogger.com/u/1/null)Each column in the process list represents some static or dynamic attribute of the process. Dynamic attributes are updated at each automatic refresh interval. The default configuration of Procexp shows these columns:

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Process**[](https://www.blogger.com/u/1/null) This column shows the name of the executable, along with its icon if Procexp can identify the full path to the executable. The first three rows represent “pseudo-processes,” which I will describe in the “[What you can expect to see](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03lev3sec6)” section shortly.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **CPU**[](https://www.blogger.com/u/1/null) This column shows the percentage of CPU time, rounded to two decimal places, consumed by the process in the last refresh interval. (It’s fully described in the “[Process Performance tab](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec4_html#ch03lev3sec9)[](https://www.blogger.com/u/1/null)” section later in this chapter. Also see the “[Measuring CPU consumption](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev1sec1_html#ch03lev2sec1)” section earlier in this chapter for more information.)

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Private Bytes**[](https://www.blogger.com/u/1/null) This is the number of bytes allocated and committed by the process for its own use and that are not shareable with other processes. Per-process private bytes include heap and stack memory. Memory leaks are often exhibited by a continual rise in this value.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Working Set**[](https://www.blogger.com/u/1/null) This column displays the amount of physical memory assigned to the process by the memory manager.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **PID** The process ID.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Description and Company Name**[](https://www.blogger.com/u/1/null) Information in these columns is extracted from the version information resource of the executable image file. These columns are populated only if Procexp is able to identify the path to the file and can read from it. If Procexp is not running with administrative rights, it will not be able to read that information from nonservice processes running in a different security context.

[](https://www.blogger.com/u/1/null)You can choose to display many more attributes, which will be described in the “[Customizing column selections](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec4_html#ch03lev2sec4)[](https://www.blogger.com/u/1/null)” section later in this chapter.

[](https://www.blogger.com/u/1/null)You can resize columns by dragging the border lines in the column headers. You can autosize a column to its current content by double-clicking the border line to the right of the column title. And you can reorder columns—except for the Process column, which is always the leftmost—by dragging the column headers. The Process column is also always kept in the view; if the other columns are wider than can fit in the window, they can be scrolled horizontally.

[](https://www.blogger.com/u/1/null)Clicking on a column header sorts the table by the data in that column in ascending order. Clicking the same column header again toggles between ascending and descending order. For example, clicking on the CPU column to get a descending sort shows the processes consuming the most CPU at the top of the list. The list automatically reorders at each refresh interval as different processes consume more or less CPU. Again here, there’s an exception for the Process column.

[](https://www.blogger.com/u/1/null)One hidden trick in Procexp is that in both the main window and in the lower pane, pressing Ctrl+C copies the content of the selected row to the clipboard as tab-separated text.

##### [](https://www.blogger.com/u/1/null)Process tree

[](https://www.blogger.com/u/1/null)As mentioned, the Process column is always the first one displayed. It has three sorting modes: ascending, descending, and Process Tree.

[](https://www.blogger.com/u/1/null)By default, Procexp displays processes in a tree view, which shows the processes’ parent/child relationships. Whenever a process creates another process, Windows puts the process ID (PID) of the creating process (the _parent_[](https://www.blogger.com/u/1/null)) into the internal data structure of the new process (the _child_[](https://www.blogger.com/u/1/null)). Procexp uses this information to build its tree view. Unlike in UNIX, the process parent/child relationship is not used by Windows, so when a process exits, processes it created are not updated to identify another ancestor. In the Procexp tree view, processes that have no existing parent are left-aligned in the column.

[](https://www.blogger.com/u/1/null)You can collapse or expand portions of the tree by clicking the plus (+) and minus (–) icons to the left of parent processes in the tree, or you can do it by selecting those nodes and pressing the left and right arrow keys. Nodes that you collapse remain collapsed if you switch to an ascending or descending sort on the Process column or any other column.

[](https://www.blogger.com/u/1/null)Clicking the Process column header cycles through an ascending sort by process name, a descending sort, and the tree view. You can also switch to the tree view at any time by pressing Ctrl+T or by clicking the Show Process Tree toolbar icon.

##### Tooltips

[](https://www.blogger.com/u/1/null)Hovering the mouse pointer over a column entry in which the text does not fit within the column’s width displays a tooltip with the full text content of that entry. And yet again, the Process column is a special case.

[](https://www.blogger.com/u/1/null)By default, hovering the pointer over any process name displays its command line and the full path to its executable image, if Procexp can obtain that information. As mentioned earlier, obtaining that information can require administrative rights in some cases. The command line and image path are not shown in the tooltip if the corresponding columns are enabled for display. Likewise, if the Description or Company Name column is not enabled, the tooltip displays that information.

[](https://www.blogger.com/u/1/null)The tooltip shows additional information when possible. For example, when you hover the pointer over a service process, the tooltip lists the display and internal names of all the services hosted within that process. Hovering it over a WMI Provider Host (WmiPrvSe.exe) process shows the WMI providers, namespaces, and DLLs in that instance. The tooltips for different operating systems’ task host processes—such as taskeng.exe, taskhost.exe, taskhostw.exe, or taskhostex.exe—displays the tasks running within it. And hovering the pointer over a “modern” app on Windows 8 or newer shows its full package name.

[](https://www.blogger.com/u/1/null)If the process has a user-defined comment associated with it and the Comment column is not selected for display, the comment also appears in the tooltip. (A user-defined comment can be entered in the Image tab of the process’ Properties dialog box. See the “[Process details](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev1sec4_html#ch03lev1sec4)[](https://www.blogger.com/u/1/null)” section later in the chapter for more information.)

##### [](https://www.blogger.com/u/1/null)What you can expect to see

[](https://www.blogger.com/u/1/null)There are some patterns you can always expect to see in Procexp on a normal Windows system. Some processes and parent/child relationships will always appear, as well as some pseudo-processes that Procexp uses to distinguish categories of kernel-mode activity.

###### System processes

[](https://www.blogger.com/u/1/null)The first three rows in the Process Tree view are System Idle Process, System, and Interrupts. System Idle Process and Interrupts are not real operating system processes, and the System process does not run user-mode code.

[](https://www.blogger.com/u/1/null)The System Idle Process (called just “Idle” by some utilities) has one “thread” per CPU and is used to account for CPU idle time when Windows is not running any program code. Because it isn’t a real process, it doesn’t have a PID—there’s no PID 0 in Windows. However, because Task Manager shows an artificial System Idle Process and displays 0 in its PID column, Procexp follows suit and assigns it PID 0.

[](https://www.blogger.com/u/1/null)The System process hosts only kernel-mode system threads, which only ever run (as you might expect) in kernel mode. These threads typically execute operating system code from Ntoskrnl.exe and device driver code.

[](https://www.blogger.com/u/1/null)The Interrupts pseudo-process represents kernel-mode time spent servicing interrupts and deferred procedure calls (DPCs). Procexp represents Interrupts as a child process of System because its time is spent entirely in kernel mode. Windows does not charge the time represented by this pseudo-process to the System process nor to any other process. Older versions of Task Manager incorrectly included interrupt and DPC time in its numbers for the System Idle Process. A system with heavy interrupt activity would therefore have appeared to be idle according to Task Manager. If you have a high interrupt or DPC load, you might want to investigate the reason by using Xperf to trace interrupts and DPCs or Kernrate to monitor kernel-mode CPU usage. For more information about interrupts and DPCs, see _[](https://www.blogger.com/u/1/null)Windows Internals_.

###### Startup and Logon Processes

[](https://www.blogger.com/u/1/null)From the time Windows starts until the first user logs on, there’s a well-defined sequence of processes. By the time you log on and are able to see the process tree in Procexp, some of these processes have exited, so the user shell (typically Explorer.exe) appears on the left edge of the window with no parent process. For much more information on the startup and logon sequences, see _Windows Internals_.

As shown in [Figure 3-5](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fig05)[](https://www.blogger.com/u/1/null), the System process starts an instance of Smss.exe (the Session Manager), which remains running until system shutdown. That Smss.exe launches two new instances of Smss.exe, one in session 0 and one in session 1, which create processes in their respective sessions. Both of these instances end up exiting before a user logs on, so the initial Smss.exe always appears not to have child processes. The instance of Smss.exe in session 0 starts an instance of Csrss.exe (the “client-server runtime” Windows subsystem) in session 0 and Wininit.exe. Wininit.exe starts Services.exe (the Service Control Manager process) and Lsass.exe (the Local Security Authority subsystem). In session 1, Smss.exe starts a new instance of Csrss.exe and Winlogon.exe. Winlogon starts LogonUI.exe to prompt the interactive user for credentials, and then it starts Userinit.exe (which starts Explorer) after the user has authenticated. Both LogonUI and Userinit typically exit before the shell initializes and the [](https://www.blogger.com/u/1/null)[](https://www.blogger.com/u/1/null)user can start Procexp. Most services are descendants of Services.exe; Services.exe does not host any services itself.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85MzBmZWhpcy90cGdnYXNyaS9jNWdwMGou)

[](https://www.blogger.com/u/1/null)**FIGURE 3-5** Process tree in Windows 10.

[](https://www.blogger.com/u/1/null)To view the complete startup process tree for yourself, refer to the “[Boot logging](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch05lev1sec6_html#ch05lev2sec17)” section in [Chapter 5](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch05_html#ch05), “[Process Monitor](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch05_html#ch05).”

###### User Processes

[](https://www.blogger.com/u/1/null)There are some typical patterns you might wonder about in the Procexp display. For example, you might see “own processes” that are children of service processes rather than descendants of Explorer. The most common examples are out-of-process DCOM components. An application invokes a component that COM determines needs to be hosted in a separate process. Even though the new process might run as the interactive user, the new process is launched by the process hosting the DcomLaunch service rather than directly by the client process. Similarly, on Windows Vista and Windows 7, the Desktop Window Manager (Dwm.exe) is launched as the desktop user by the Desktop Window Manager Session Manager service (UxSms). On Windows 8 and newer, Dwm.exe runs as a system-managed Window Manager account and is started by Winlogon.exe.

[](https://www.blogger.com/u/1/null)[](https://www.blogger.com/u/1/null)Another frequent pattern is the use of job objects. Some DCOM components, particularly Windows Management Instrumentation (WMI) hosting processes, run with restrictions on the amount of memory they can allocate, the number of child processes they can start (if any), or the maximum amount of CPU time they can charge. Anything launched through the Secondary Logon service (for example, with RunAs) is added to a job so that the process and any children it launches can be tracked as a unit and terminated if they’re still running when the user logs off. Finally, the Program Compatibility Assistant (PCA) tracks legacy applications on some versions of Windows so that it can offer a compatibility fix to the user if the PCA detects a potential compatibility problem for which it might have a solution after the last process in the job has exited. Jobs are not highlighted by default; see the “[Colored rows and heatmap columns](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03lev3sec1)” section earlier in this chapter for more information.

[](https://www.blogger.com/u/1/null)Virtualization-based security in Windows 10 and Windows Server 2016 enables features such as Credential Guard and Device Guard, and it creates user-mode processes that are outside of the direct control of Windows. Procexp can display the existence of the Secure System and LsaIso.exe[4](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fn4a)[](https://www.blogger.com/u/1/null) processes, but little else about them.

[4](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fn4)[](https://www.blogger.com/u/1/null) That’s an upper-case “i” and not a lower-case “L” – it’s short for “LSA Isolated.” It’s not “LS Also.”

##### Process actions

[](https://www.blogger.com/u/1/null)You can perform a number of actions on a process by right-clicking it or by selecting it and choosing any of the following options from the Process menu:

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Window submenu**[](https://www.blogger.com/u/1/null) If the process owns a visible window on the desktop, you can use the window submenu to bring it to the foreground or restore, minimize, maximize, or close it. The window submenu is disabled if the process owns no visible windows.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Set Affinity**[](https://www.blogger.com/u/1/null) On multi-CPU systems, you can set processor affinity for a process so that its threads will run only on the CPU or CPUs you specify. (See [Figure 3-6](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev2sec3_html#ch03fig06)[](https://www.blogger.com/u/1/null).) This can be useful if you have a runaway CPU-hogging process that must be allowed to keep running but throttled back so that you can troubleshoot it. You can use Set Affinity to restrict the process to a single core temporarily and free up other CPUs so that the system is still usable. (If a particular process should always be restricted to a single CPU and you can’t modify its source code, use the SingleProcAffinity application compatibility shim or, as a last resort, modify the file’s PE header to specify affinity.)

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85MzBmZWhpcy90cGdnYXNyaS9jNmdwMGou)

[](https://www.blogger.com/u/1/null)**FIGURE 3-6**[](https://www.blogger.com/u/1/null) Dialog box for setting processor affinity on an eight-processor system.

[](https://www.blogger.com/u/1/null)![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Set Priority**[](https://www.blogger.com/u/1/null) View or set the base scheduling priority for the process.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Kill Process**[](https://www.blogger.com/u/1/null) You can forcibly terminate a process by choosing Kill Process or by clicking the Kill Process button in the toolbar. By default, Procexp prompts you for confirmation before terminating the process. You can disable that prompt by clearing Confirm Kill in the Options menu.

* * *

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85YXJ3ZWhpcy90cC5hc3JuL2NwZ2pn) Warning

[](https://www.blogger.com/u/1/null)Forcibly terminating a process does not give the process an opportunity to shut down cleanly and can cause data loss or system instability. In addition, Procexp does not provide extra warnings if you try to terminate a system-critical process such as Csrss.exe. Terminating a system-critical process results in an immediate Windows blue screen crash.

* * *

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Kill Process Tree**[](https://www.blogger.com/u/1/null) When Procexp is in the process-tree sorting mode, this menu item is available and allows you to forcibly terminate a process and all its descendants. If the Confirm Kill option is enabled, you will be prompted for confirmation first.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Restart**[](https://www.blogger.com/u/1/null) When you select this item, Procexp terminates the highlighted process (after optional confirmation) and starts the same image using the same command-line arguments. Note that the new instance might fail to work correctly if the original process depended on other operating characteristics, such as the security context, environment variables, or inherited object handles.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Suspend**[](https://www.blogger.com/u/1/null) If you want a process to become temporarily inactive so that a system resource—such as a network, CPU, or disk—becomes available for other processes, you can suspend the process’ threads. To resume a suspended process, choose the Resume item from the process context menu. Note that this feature can’t resume a “modern” app package that was suspended by the Process Lifetime Manager; the process will remain suspended.

* * *

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85aXRwZWhpcy90cGphcy5yL2NnZ3A-) Tip

[](https://www.blogger.com/u/1/null)Suspend can be useful when dealing with “buddy system” malware, in which two or more processes watch for each other’s termination, with the nonterminated one restarting its buddy if it dies. To defeat such malware, suspend the processes first and then terminate them. See [Chapter 20](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch20_html#ch20), “[Malware](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch20_html#ch20)[](https://www.blogger.com/u/1/null),” for additional information and for several real-world troubleshooting cases that succeeded with this technique.

* * *

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Launch Depends**[](https://www.blogger.com/u/1/null) If the Dependency Walker (Depends.exe) utility is found, Procexp launches it with the path to the executable image of the selected process as a command-line argument. Depends.exe shows DLL dependencies. It used to ship with various Microsoft products, and it’s now distributed through _[www.DependencyWalker.com](http://www.dependencywalker.com/)_.

[](https://www.blogger.com/u/1/null)![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Debug**[](https://www.blogger.com/u/1/null) This menu item is available only if a debugger is registered in HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug. Choosing Debug launches the registered debugger with _–p_[](https://www.blogger.com/u/1/null) followed by the selected process’ PID as the command-line arguments. Note that closing the debugger without detaching first terminates the debugee as well. If the debugger registration is changed while Procexp is running, Procexp needs to be restarted to pick up the change.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Create Dump submenu**[](https://www.blogger.com/u/1/null) You use the options on this submenu to capture a minidump or a full memory dump of the selected process to a file location of your choosing. Procexp captures a 32-bit or 64-bit dump, depending on the process’ bitness. Capturing a dump does not terminate the process.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Check VirusTotal**[](https://www.blogger.com/u/1/null) This item submits the SHA1 hash of the process’ image file to the [VirusTotal.com](http://virustotal.com/)[](https://www.blogger.com/u/1/null) web service and reports the result in the VirusTotal column. See the “[VirusTotal analysis](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev1sec7_html#ch03lev1sec7)[](https://www.blogger.com/u/1/null)” section later in this chapter for more information.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Properties**[](https://www.blogger.com/u/1/null) This menu item displays the Properties dialog box for the selected process, which displays a wealth of information about the process. It’s described in detail in the “[Process details](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch03lev1sec4_html#ch03lev1sec4)[](https://www.blogger.com/u/1/null)” section later in this chapter.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85cXN1ZWhpcy90cGphcy5yL2NnZ3A-) **Search Online**[](https://www.blogger.com/u/1/null) Procexp will launch a search for the selected executable name using your default browser and search engine. This option can be useful when researching malware or identifying the source of an unrecognized process.