---
title: 'The Robot Operating System (ROS) has moved out of academics'
date: 2020-01-09T04:47:00+01:00
draft: false
---

Commentary: The Robot Operating System (ROS) doesn't get a lot of press, but it increasingly powers the robots upon which industrial automation and other functions depend.

![Human with robot](https://tr1.cbsistatic.com/hub/i/r/2019/11/21/6a5a10a3-8789-4a91-9f3f-ba7b503e08dc/resize/770x/90e77a613aa38298240003c69ea1e2fd/your-robot-coworker-just-wants-to-help.jpg)

Image: Getty Images/iStockphoto

According to recent LinkedIn data, [artificial intelligence (AI) jobs are up 74% while data science jobs are up 37% since 2015](https://www.zdnet.com/article/data-science-dominates-linkedins-emerging-jobs-ranking/). Perhaps less visible, but emerging quickly in importance, are the robots increasingly powered by that data science. Small wonder, then, that the second-hottest job in LinkedIn's analysis is the robotics engineer, experiencing growth of 40% since 2015.

While the [open source projects](https://opensource.com/article/18/5/top-8-open-source-ai-technologies-machine-learning) behind the rise of data science are reasonably well known (e.g., [TensorFlow](https://www.techrepublic.com/article/tensorflow-googles-open-source-software-library-for-machine-learning-the-smart-persons-guide/) and [Keras](https://keras.io/), among others), most people aren't aware that robotics is also heavily influenced by open source and, in particular, by the [Robot Operating System](https://www.ros.org/) (ROS). Given the importance of ROS to the swelling open source robotics community, it's worth learning a bit more about it.

The Robot Operating System was born at Stanford
-----------------------------------------------

ROS has been around for over 10 years and has tens of thousands of developers building packages for it. In fact, according to ABI Research, [roughly 55% of the world's robots will include a ROS package by 2024](https://www.abiresearch.com/market-research/product/1029218-open-source-robotics-projects/).

It wasn't always thus.

Keenan Wyrobek and Eric Berger were student researchers at Stanford back in the mid 2000s, and both had a common goal: Stop reinventing the robot. As recorded by Ricardo Tellez in his [A History of ROS](https://www.theconstructsim.com/history-ros/), "Too much time \[was\] dedicated to re-implementing the software infrastructure required to build complex robotics algorithms…\[and\] too little time dedicated to actually building intelligent robotics programs." Nearing the end of the decade, Wyrobek and Berger partnered with Scott Hassan's robotics research lab [Willow Garage](https://en.wikipedia.org/wiki/Willow_Garage) to push their work forward under the auspices of its Personal Robotics Program.

**SEE: **[**Special report: A guide to data center automation**](https://www.zdnet.com/article/special-report-a-guide-to-data-center-automation-free-pdf/)** (ZDNet special feature) | [Download the free PDF version](https://www.techrepublic.com/resource-library/whitepapers/special-report-a-guide-to-data-center-automation-free-pdf/) (TechRepublic)**

It was here that ROS took shape. It was also here that ROS took on its open source nature. Licensed under the highly permissive three-clause [BSD license](http://opensource.org/licenses/BSD-3-Clause), community projects are licensed under a range of other open source licenses, making for a vibrant, eclectic community.

The Robot Operating System has moved out of academics
-----------------------------------------------------

In its original form, ROS was primarily driven by and geared to the academic and hobbyist communities, who built thousands of add-on packages to extend ROS. This extensibility has always been a core mandate for ROS and, as such, [Open Robotics](https://www.openrobotics.org/) (the foundation behind ROS) CEO [Brian Gerkey detailed](https://design.ros2.org/articles/why_ros2.html), "We put a lot of effort into defining levels of abstraction (usually through message interfaces) that would allow much of the software to be reused elsewhere."

While ROS was extensible, it lacked strong security and real-time communication, making it a poor fit for large industrial automation (IA) systems. Even so, because of ROS' community and potential, some IA companies invested significant resources to make it work for their mission-critical applications.

**SEE:** [**The 8 coolest robots spotted at CES 2020**](https://www.techrepublic.com/article/the-8-coolest-robots-spotted-at-ces-2020/) **(TechRepublic)**

By the late 2010s, increasingly industrial-grade demands were stretching "the platform...in unexpected ways," according to Gerkey. To push ROS forward into more commercial-grade applications, Open Robotics initiated ROS 2 to tackle an array of new use cases, as Gerkey detailed:

*   **Teams of multiple robots:** While it is possible to build multi-robot systems using ROS today, there is no standard approach, and they are all somewhat of a hack on top of the single-master structure of ROS.
    
*   **Small embedded platforms:** We want small computers, including "bare-metal" micro controllers, to be first-class participants in the ROS environment, instead of being segregated from ROS by a device driver.
    
*   **Real-time systems:** We want to support real-time control directly in ROS, including inter-process and inter-machine communication (assuming appropriate operating system and/or hardware support).
    
*   **Non-ideal networks:** We want ROS to behave as well as is possible when network connectivity degrades due to loss and/or delay, from poor-quality Wi-Fi to ground-to-space communication links.
    
*   **Production environments:** While it is vital that ROS continue to be the platform of choice in the research lab, we want to ensure that ROS-based lab prototypes can evolve into ROS-based products suitable for use in real-world applications.
    
*   **Prescribed patterns for building and structuring systems:** While we will maintain the underlying flexibility that is the hallmark of ROS, we want to provide clear patterns and supporting tools for features such as life cycle management and static configurations for deployment.
    

While there was interest in simply extending the original ROS (ROS 1), "given the intrusive nature of the changes that would be required to achieve the benefits that we are seeking, there is too much risk associated with changing the current ROS system that is relied upon by so many people." ROS 2 was born, and ROS 2 packages can communicate with ROS 1 packages through message bridges.

Today tens of thousands of developers work with ROS to build the future of robotics. [Contributors to ROS](https://www.ros.org/contributors/) come from a wide variety of companies, both well-known and obscure. But the code they're building, while not as widely known as Scikit or TensorFlow, will increasingly power the everyday robotics in our lives. As such, it's comforting to know that it's open source. 

_**Disclosure**: I work for AWS, but nothing written herein relates to my work there or is intended to promote AWS._

### Open Source Weekly Newsletter

You don't want to miss our tips, tutorials, and commentary on the Linux OS and open source applications. Delivered Tuesdays

Sign up today

Also see
--------

  
  
from Hacker News https://ift.tt/36D3iQO