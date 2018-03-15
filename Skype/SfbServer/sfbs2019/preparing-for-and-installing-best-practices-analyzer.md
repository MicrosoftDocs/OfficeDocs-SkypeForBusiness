---
title: "Preparing for and installing Best Practices Analyzer in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 550613dd-dc08-482e-9980-a3fe187cd162
description: "In this articleSystem Requirements for Best Practices Analyzer InstallationChoosing a Computer for InstallationInstalling Best Practices Analyzer"
---

# Preparing for and installing Best Practices Analyzer in Lync Server 2013
[]
 **In this article**
  
[System Requirements for Best Practices Analyzer Installation](#sectionSection0)
  
[Choosing a Computer for Installation](#sectionSection1)
  
[Installing Best Practices Analyzer](#sectionSection2)
  
You must be logged on as a member of the Administrators group to perform the tasks that are described in this topic.
  
## System Requirements for Best Practices Analyzer Installation
<a name="sectionSection0"> </a>

To run Lync Server 2013, Best Practices Analyzer to scan your environment, the computer must be running a 64-bit edition of one of the following operating systems: 
  
- Windows Server 2008 R2 with Service Pack 1 (SP1) Standard operating system
    
- Windows Server 2008 R2 with SP1 Enterprise operating system
    
- Windows Server 2008 R2 with SP1 Datacenter operating system
    
- Windows Server 2012 Datacenter operating system
    
- Windows Server 2012 Standard operating system
    
- Windows Server 2012 Enterprise operating system
    
- Windows Server 2012 R2 Datacenter operating system
    
- Windows Server 2012 R2 Standard operating system
    
- Windows Server 2012 R2 Enterprise operating system
    
- Windows 8 operating system
    
- Windows 7 operating system
    
The computer must also be running the following:
  
- Microsoft .NET Framework 4.5. For Lync Server 2013, you must manually install the 64-bit edition of Microsoft .NET Framework 4.5 on the server prior to installing Lync Server 2013. 
    
- Lync Server 2013, Core Components. 
    
- WMI Backward Compatibility Package. For details, see [Install WMI Backward Compatibility package [OCS 2007 R2 to W15]](install-wmi-backward-compatibility-package-ocs-2007-r2-to-w15.md) in the Migration documentation. 
    
- Windows PowerShell 3.0. For details, see [Installing Windows PowerShell 3.0 for Lync Server 2013](installing-windows-powershell-3-0.md) in the Deployment documentation. 
    
You can install Best Practices Analyzer on computers with a supported operating system that are not running Lync Server 2013, Core Components or WMI Backward Compatibility Package, but you can use Best Practices Analyzer on those computers only to view reports, not to run scans.
  
## Choosing a Computer for Installation
<a name="sectionSection1"> </a>

We recommend that you install Lync Server 2013, Best Practices Analyzer on a computer that is dedicated to Lync Server 2013 management. You can install the tool on a server running Lync Server 2013 or an administrative computer running Lync Server 2013 administrative tools. If you install the tool on a server that is running Lync Server, we recommend that you use the tool to scan only that server. 
  
## Installing Best Practices Analyzer
<a name="sectionSection2"> </a>

You can download the Best Practices Analyzer for Lync Server 2013 at [https://go.microsoft.com/fwlink/p/?linkId=266539](https://go.microsoft.com/fwlink/p/?linkId=266539).
  
To install Best Practices Analyzer, start the Microsoft Installer file RtcBPA.msi on the computer where you want to install the tool, and then follow the instructions on the screen. The default location for installing the program files is  _\<system drive\>_\Program Files\Lync Server 2013\BPA.
  

