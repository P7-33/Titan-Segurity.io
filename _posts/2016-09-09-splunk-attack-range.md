---
title: 'Splunk Attack Range'
date: 2019-12-20T11:47:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-9BGytRDmNUY/XfA3X9Qr_fI/AAAAAAAAREI/31Vq6PqurMQiMGPj7OKZaBZjivGSgqqWwCNcBGAsYHQ/s1600/attack_range_1_range.jpeg)](https://1.bp.blogspot.com/-9BGytRDmNUY/XfA3X9Qr_fI/AAAAAAAAREI/31Vq6PqurMQiMGPj7OKZaBZjivGSgqqWwCNcBGAsYHQ/s1600/attack_range_1_range.jpeg)

**Splunk Attack Range - A Tool That Allows You To Create Vulnerable Instrumented Local Or Cloud Environments To Simulate Attacks Against And Collect The Data Into Splunk**

  

  
The Attack Range solves two main challenges in development of detections. First, it allows the user to quickly build a small lab infrastructure as close as possible to your production environment. This lab infrastructure contains a [Windows](https://www.kitploit.com/search/label/Windows "Windows") Domain Controller, Windows Workstation and Linux server, which comes pre-configured with multiple security tools and logging configuration. The infrastructure comes with a [Splunk](https://www.kitploit.com/search/label/Splunk "Splunk") server collecting multiple log sources from the different servers.  
Second, this framework allows the user to perform attack simulation using different engines. Therefore, the user can repeatedly replicate and generate data as close to "ground truth" as possible, in a format that allows the creation of detections, investigations, knowledge objects, and playbooks in Splunk.  
  
  
**Architecture**  
Attack Range can be used in two different ways:

*   local using vagrant and virtualbox
*   in the cloud using terraform and AWS

In order to make Attack Range work on almost every laptop, the local version using Vagrant and [Virtualbox](https://www.kitploit.com/search/label/Virtualbox "Virtualbox") consists of a subset of the full-blown cloud infrastructure in AWS using Terraform. The local version consists of a Splunk single instance and a Windows 10 workstation pre-configured with best practice logging configuration according to Splunk. The cloud infrastructure in AWS using [Terraform](https://www.kitploit.com/search/label/Terraform "Terraform") consists of a Windows 10 workstation, a Windows 2016 server and a Splunk server. More information can be found in the wiki  

[![](https://1.bp.blogspot.com/-9T8SYVL70Ww/XfA3eg-rfoI/AAAAAAAAREM/GKHzN5r6Xy8bADvUlV9kg9aQjIuYfqm-QCNcBGAsYHQ/s640/attack_range_2_architecture.png)](https://1.bp.blogspot.com/-9T8SYVL70Ww/XfA3eg-rfoI/AAAAAAAAREM/GKHzN5r6Xy8bADvUlV9kg9aQjIuYfqm-QCNcBGAsYHQ/s1600/attack_range_2_architecture.png)

  
**Configuration**

*   [vagrant and virtualbox](https://github.com/splunk/attack_range/wiki/Configure-Attack-Range-for-Vagrant "vagrant and virtualbox")
*   [terraform and AWS](https://github.com/splunk/attack_range/wiki/Configure-Attack-Range-for-Terraform "terraform and AWS")

  
**Running**  
Attack Range supports different actions:

*   Build Attack Range
*   Perform Attack Simulation
*   Destroy Attack Range
*   Stop Attack Range
*   Resume Attack Range

  
**Build Attack Range**

*   Build Attack Range using **Terraform**

```
python attack_range.py -m terraform -a build
```

*   Build Attack Range using **Vagrant**

```
python attack_range.py -m vagrant -a build
```

  
**Perform Attack Simulation**

*   Perform Attack [Simulation](https://www.kitploit.com/search/label/Simulation "Simulation") using **Terraform**

```
python attack_range.py -m terraform -a simulate -st T1117,T1003 -t attack-range_windows_2016_dc
```

*   Perform Attack Simulation using **Vagrant**

```
python attack_range.py -m vagrant -a simulate -st T1117,T1003 -t win10
```

  
**Destroy Attack Range**

*   Destroy Attack Range using **Terraform**

```
python attack_range.py -m terraform -a destroy
```

*   Destroy Attack Range using **Vagrant**

```
python attack_range.py -m vagrant -a destroy
```

  
**Stop Attack Range**

*   Stop Attack Range using **Terraform**

```
python attack_range.py -m terraform -a stop
```

*   Stop Attack Range using **Vagrant**

```
python attack_range.py -m vagrant -a stop
```

  
**Resume Attack Range**

*   Resume Attack Range using **Terraform**

```
python attack_range.py -m terraform -a resume
```

*   Resume Attack Range using **Vagrant**

```
python attack_range.py -m vagrant -a resume
```

  
**Support**  
Please use the [GitHub issue tracker](https://github.com/splunk/attack_range/issues "GitHub issue tracker") to submit bugs or request features.  
If you have questions or need support, you can:

*   Post a question to [Splunk Answers](http://answers.splunk.com/ "Splunk Answers")
*   Join the [#security-research](https://splunk-usergroups.slack.com/messages/C1RH09ERM/ "#security-research") room in the [Splunk Slack channel](https://splunk-usergroups.slack.com/ "Splunk Slack channel")
*   If you are a Splunk Enterprise customer with a valid support entitlement contract and have a Splunk-related question, you can also open a support case on the [https://www.splunk.com/](https://www.splunk.com/ "https://www.splunk.com/") support portal

  
**Author**

*   [Jose Hernandez](https://twitter.com/d1vious "Jose Hernandez")

  
**Contributors**

*   [Rod Soto](https://twitter.com/rodsoto "Rod Soto")
*   [Bhavin Patel](https://twitter.com/hackpsy "Bhavin Patel")
*   [Patrick Bareiß](https://twitter.com/bareiss_patrick "Patrick Bareiß")
*   Russ Nolen
*   Phil Royer

  
**Acknowledgements**

*   [DetectionLab](https://github.com/clong/DetectionLab "DetectionLab")
*   Atomic Red team
*   Sysmon configuration

  

**[Download Attack\_Range](http://locinealy.com/4XTu "Download Attack_Range")**

**Regards**

**Kang Asu**