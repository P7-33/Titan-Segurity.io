---
title: 'What is Windows Core OS (WCOS) - Explained'
date: 2020-02-07T13:30:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Windows has a roughly 77% market share in the desktop market and yet there are reports that [Microsoft is developing a new operating system](https://beebom.com/windows-core-os-spotted-official-documents/) and you wonder why. After Windows 10S, now there are rumors about Windows Core OS. So what is Windows Core OS (WCOS) and how it’s different from [Windows 10 or 10S](https://beebom.com/windows-10-s-vs-windows-10/)? Is it something that will replace Windows 10 in the future? We have answered all these are crucial questions along with all the nitty-gritty in detail below. Know that WCOS is going to change the foundation of Windows as we know it. So without further delay, let’s go ahead and learn about Windows Core OS in all aspects.  

What is Windows Core OS (WCOS)?
-------------------------------

  

Before I throw technical terms from left, right, and center, let me explain what is Windows Core OS in simple terms. **Windows Core OS is a universal base from where different flavors of Windows can be created**. WCOS is a shareable and modular base which means Microsoft can take it and add additional features on top of it for devices having different form factors. To draw a loose comparison, think about how the Android ecosystem works. Google develops the AOSP (the base) which is somewhat like the Windows Core OS and several manufacturers fork it to make their version of OS. Similarly, Windows Core OS will be the universal base for Windows laptops, desktops, [foldable phones](https://beebom.com/best-foldable-phones/), HoloLens, Xbox, Surface Hub, and every future product released by Microsoft.  

![What is Windows Core OS (WCOS)](https://beebom.com/wp-content/uploads/2020/02/What-is-Windows-Core-OS-WCOS.jpeg)

To conclude, Windows Core OS is not an operating system in the traditional sense (like Windows 10 or 7), but a modular base which will power a host of future Windows operating systems. In fact, **we already know about such an operating system that comes with WCOS at its base**: [Windows 10X](https://beebom.com/windows-10x-everything-you-need-know/). Last year, Microsoft unveiled a dual-screen device that acts both like a tablet and a laptop. So when you are building operating systems for devices having such a unique form factor, you need a portable base and that is where Windows Core OS comes into play. Another example is Surface Hub OS which will run on the upcoming Surface Hub 2X– an interactive whiteboard for teamwork. And this one too is powered by Windows Core OS at its base.  

So these are the different flavors of Windows Core OS running on a range of distinct devices. Now that we have got the basic idea, let’s now jump to some technicality, shall we?  

Windows Core OS Features
------------------------

  

#### 1\. CShell (Composable Shell)

  

CShell is a top-of-the-line feature of Windows Core OS. I know the term is not self-explanatory so let me explain. In the above section, I talked about how WCOS is modular and can be easily forked for devices having distinct hardware design. CShell is that feature that makes it possible. In simple term, **CShell is a modular user-interface which can be slapped on devices depending on their form factor**. It’s a user-interface deeply tied to WCOS, but also modular at the same time.  

![1. CShell (Composable Shell)](https://beebom.com/wp-content/uploads/2020/02/1.-CShell-Composable-Shell.jpeg)

Surface Neo Tablet Mode (Running WCOS-powered Windows 10X)

For example, if you are running a device like [Surface Neo](https://beebom.com/microsoft-dual-screen-surface-neo-announced/) which has both laptop and tablet form factor. Depending upon how you are using it, the device can switch to Tablet CShell or Laptop CShell in no time. What it means is that **you will get a proper Tablet user-interface while you are in the Tablet mode with all the gestures, touchscreen, snapping and other features**. And the moment you move to the laptop mode, you get a proper laptop interface where you have support for keyboard, taskbar, classic file explorer and more.  

While you can perform similar laptop-tablet switching on Windows 10 right away, the experience is jarring. In [Windows 10](https://beebom.com/windows-10-updates/) tablet mode, the interface is slightly changed for more friendly touchscreen navigation, but other than that, you don’t have many tablet-related features. Simply put, **Windows 10 does not have a dedicated tablet interface that is deeply hardwired to the underlying OS** so it does not behave like a true tablet OS. But with CShell feature on WCOS, you get a modular yet deeply tied and fully-featured interface for multiple form-factors.  

![1. CShell (Composable Shell) 2 What is Windows Core OS](https://beebom.com/wp-content/uploads/2020/02/1.-CShell-Composable-Shell-2.jpeg)

Windows 10 Tablet Mode

To give you another example, if you are using a Windows Core OS-powered laptop and if you open the [Xbox Game Bar](https://beebom.com/how-to-use-windows-10-built-in-screen-recorder/), you will instantly switch to the Xbox OS interface due to a separate CShell for gaming mode. This will make your experience much more cohesive and streamlined as if you are using an Xbox Console. **The whole idea of CShell is to make the experience consistent across all Microsoft devices** by making the user-interface portable.

  
  

  

### 2\. Shareable Component

  

After CShell, Shareable Component is another foundational feature of Windows Core OS. The problem with Windows 10 is that every layer from legacy apps to modern subsystems are intertwined with each other and that makes it harder to update and separate them. Recently, [Google separated the Hardware Abstraction Layer (HAL) on Android](https://beebom.com/what-is-project-treble/) to bring modularity and improve the Android update system. With WCOS, Microsoft is also taking a similar route. In fact, **Microsoft is removing almost all the components to make WCOS just a barebone base**. All the app layers, Libraries, and Composers are available in the form of additional components. In fact, the interface that is CShell is also available as a Component to make WCOS completely light and modular.  

![2. Shareable Component What is Windows Core OS](https://beebom.com/wp-content/uploads/2020/02/2.-Shareable-Component.jpg)

Source: Windows Central

What it means for Microsoft is that, for instance, if they want to create an operating system for foldable phones, they can take the WCOS base and add components as required. No need to re-write and modify a huge chunk of code to make a compatible Windows operating system for different devices. This will enormously save crucial time and resources for Microsoft. Further, they can choose to add Win32 app support (as a component) on WCOS-powered laptops or leave the support on WCOS-powered tablets. **Basically, share components where it makes sense.** This will bring modularity in the Windows ecosystem and as a result, will make your WCOS-powered laptop light, [battery efficient](https://beebom.com/how-get-battery-report-windows-10/), and overall faster to use just like [Chrome OS](https://beebom.com/best-chrome-os-tips-tricks/).  

### 3\. Faster Updates

  

Faster Update is a feature that many Windows users hope to see one day and it’s finally coming with Windows Core OS. It’s an inherent WCOS feature so any OS built using its base will support faster update by default. This feature is straight out of Chrome OS, and I am happy that Microsoft is bringing it to WCOS. Unlike Windows 10 where you have to wait for 5-30 minutes to install an update, on WCOS, it will be just a matter of a reboot. **It will use a separate partition to install updates while you are using your device** and will switch the active boot slot after a reboot. No need to wait for installation. Apart from that, Windows Core OS will use the Full Flash Update (FFU) image format to install Windows updates as opposed to ISO which will significantly reduce installation time. So finally, your [Windows 10 update woes](https://beebom.com/stop-windows-10-updates/) will go away with Windows Core OS.  

![3. Faster Updates](https://beebom.com/wp-content/uploads/2020/02/3.-Faster-Updates.jpeg)

### 4\. App Support

  

Now we come to the most crucial part, App Support. Does Windows Core OS support Win32 Apps like Microsoft Office and the new Microsoft Edge? The answer is plain no; WCOS does not have native support for legacy apps which have been a cornerstone of Windows operating systems since its existence. However, Microsoft can add **an additional component for Win32 app support which will work in a container** and will be completely sandboxed– just like [Linux on Chrome OS](https://beebom.com/how-use-linux-chromebook/). All it means for end-users is that you will be able to use your favorite Win32 apps, but the performance might take a hit since it’s not running natively. But Microsoft has stated that the performance will be quite good and usable in a container.  

![4. App Support](https://beebom.com/wp-content/uploads/2020/02/4.-App-Support.jpeg)

Windows 10 Architecture with Legacy App Support (Win32)

Apart from that, WCOS will have inherent support for UWP and Web apps. As the world is increasingly moving towards web and cloud computing, this is a good move by Microsoft. It can be argued that leaving Win32 app support is a step in the wrong direction since Microsoft has painstakingly built its app ecosystem for decades. However, we also have to acknowledge the fact that **supporting such a complex app layer has bogged down Windows 10 considerably**. In fact, legacy apps have become a bane for Microsoft at this point. Furthermore, most of the users already use a web browser to achieve a lot of tasks so there is a good case for dropping Win32 app support.  

Why Microsoft Created Windows Core OS?
--------------------------------------

  

If you are wondering why Microsoft needs such a universal base, the answer lies in Microsoft’s failure to make Windows 10 an all-encompassing platform. For instance, Microsoft tried to build its smartphone in line with Windows 10’s aesthetic and features, but it failed miserably. The reason is that **the base for the desktop and mobile version of Windows 10 is completely different** hence the features were implemented differently.  

![windows mobile action center](https://beebom.com/wp-content/uploads/2020/02/shutterstock_1380441881.jpg)

As a result, the Windows 10 experience on mobile was starkly inconsistent against the desktop version. To give you a practical example, **the Action Center on Windows Mobile feels shaky and disjointed (almost fake)** in comparison to how Action Center behaves on the desktop version. So to plug this hole, Microsoft needs a common yet modular base so the experience remains coherent across all the WCOS-powered devices.

  
  

  

![Why Microsoft Created Windows Core OS?](https://beebom.com/wp-content/uploads/2020/02/Why-Microsoft-Created-Windows-Core-OS-2.jpeg)

Apart from that, one of the major reasons why Microsoft created Windows Core OS is portability. In a world where technology and consumer behavior is rapidly changing every 4-5 years, **Microsoft needed something that is easily shareable, portable, and interchangeable**. In this regard, Windows 10 fell flat as we saw with its stripped-down version, Windows 10S. Windows 10 is a highly complex and fragmented operating system having support for multiple layers like legacy apps, UWP, [Linux Subsystems](https://beebom.com/how-enable-linux-bash-shell-windows-10-wsl-2/) and more. So it’s clear that Microsoft was in a crying need for a light and universal base like WCOS that can be easily forked to create operating systems for various product categories.  

What Will Happen to Windows 10?
-------------------------------

  

Well, Windows 10 is not going anywhere. In fact, experts suggest that Windows 10 will always be available for power and enterprise users who want native Win32 app support, gaming libraries, subsystems, networking tools, legacy control panel– all into one OS. What we will see though is that **Microsoft will increasingly push a lite version of Windows with containerized Win32 app support** in the mainstream market. It will slowly make Windows 10 an optional OS meant for hardcore users, professionals, and geeks. And something like a Windows Lite will take center-stage which is light, fast to boot, have modern CShell interface, updates in a flash, performs much better, and is power-efficient.  

![What Will Happen to Windows 10 What is Windows Core OS](https://beebom.com/wp-content/uploads/2020/02/What-Will-Happen-to-Windows-10.jpg)

Windows Lite, Source: The Verge

When Will Windows Cores OS Release?
-----------------------------------

  

We will see the first instance of Windows Core OS in action **with the arrival of Surface Neo during Christmas, 2020**. It runs Windows 10X which is powered by the WCOS at its base. Apart from that, Surface Hub OS is another WCOS-powered operating system that will launch with Surface Hub 2X, but the launch has been [delayed as of now](https://www.theverge.com/2020/2/3/21119915/microsoft-surface-hub-2x-cancel-major-software-update-features-release-date). There is also Xbox OS and Windows Holographic in the pipeline but the details are scarce at this moment.  

Having said that, the important question remains, when will we get our hands-on with Windows Core OS in a mainstream product like a Windows laptop? Frankly, we don’t know as the project is still a work in progress. However, many have suggested that **we might get a peek at Windows Lite in October 2020** at Microsoft’s hardware event. But we can safely say that in the coming two years, we will have Windows Core OS-powered computers in the market.  

Are you Ready for Windows Core OS?
----------------------------------

  

So that was our detailed look into Windows Core OS and how it’s different from Windows 10. As I discussed above, Microsoft needed a common underlying base that could fit in all its products and WCOS seems to make that possible. What I love about Windows Core OS is that Microsoft has been bold enough to ditch its legacy apps. Apart from that, Microsoft has re-invented a modern OS from scratch instead of forking Windows 10 over and over again so that is quite commendable. Anyway, I am really excited to get my hands on a WCOS-powered operating system. But what about you? Tell us your opinion in the comment section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/windows-core-os-wcos-explained/)  
\[the\_ad id='1307'\]