---
title: 'Installing Docker'
date: 2019-11-05T03:56:00+01:00
draft: false
---

  
Docker is needed to work with Windows containers. The Docker installer for Windows is now available in an online package repository. It can be found and installed using the Docker provider of the package management (a.k.a. OneGet) PowerShell module. The provider needs to be installed before we start using it.  
  
The following PowerShell cmdlets can be used to install the provider.  
  
Open a remote PowerShell session on Nano Server. This assumes that you have already completed the steps described earlier:  
$Session | Enter-PSSession  
Run the following command within the remote PowerShell session to install the Docker provider PowerShell module to the Nano machine:  
Install-Module -Name DockerMsftProvider -Repository PSGallery -Force  
Run the following command within the remote PowerShell session to install the latest version of Docker using the OneGet to Nano machine:  
Install-Package -Name docker -ProviderName DockerMsftProvider  
When the installation is completed, reboot the Nano Server machine.  
Restart-Computer -Force