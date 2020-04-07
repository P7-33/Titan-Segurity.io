---
title: 'Run the following set of steps one by one to install and configure Docker on Windows 10:'
date: 2020-01-06T03:13:00+01:00
draft: false
---

Run the following set of steps one by one to install and configure Docker on Windows 10:

```
       **Invoke-WebRequest "https://master.dockerproject.org/windows/  
       amd64/docker-1.13.0-dev.zip" -OutFile "$env:TEMP\\docker-1.13.0  
       -dev.zip"  
       -UseBasicParsing**       **Expand-Archive -Path "$env:TEMP\\docker-1.13.0-dev.zip"  
       -DestinationPath $env:ProgramFiles**       **$env:path += ";c:\\program files\\docker"**       **\[Environment\]::SetEnvironmentVariable("Path", $env:Path + ";  
       C:\\Program Files\\Docker", \[EnvironmentVariableTarget\]::Machine)**       **dockerd --register-service**  

```

7.  Start the **Docker Service** by running the following command:

```
       **Start-Service docker**  

```

8.  In order to develop Windows Server Containers, we need any Windows base OS image, such as windowsservercore or nanoserver. Since Windows 10 supports Nano Servers only, run the following command to download the nanoservercore base OS image (we have a dedicated chapter for learning development using Nano Server images). The following command might take some time depending on your bandwidth; it downloads and extracts the nanoserver base OS image, which is 970 MB in size, approximately:

```
       **docker pull microsoft/nanoserver**  

```

At the time of writing, Windows 10 can only run Nano Server images. Even though the windowsservercore image gets downloaded successfully, running containers using this image will fail due to incompatibility with the OS.

9.  Ensure that the images are successfully downloaded by running the following command:

```
 **docker images**  

```

The preceding command gives the following output:

![](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=cmE4N204ZHRzaXBjMWcvcy84MjNzOTlhNTc4ZTcvczB0Z2VlZWFpL3NfbXN0c3AwbmEuMl8yLzBn)

[](https://www.blogger.com/u/2/null)Now you are ready to start container development on Windows 10, you can directly skip to the _Windows Server Containers development_ section to start creating Windows Containers.