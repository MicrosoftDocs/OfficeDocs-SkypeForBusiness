---
title: "Administrative tools software requirements in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2fb172c3-7b84-4e49-981c-2a17e7a00a29
description: "In this articleMicrosoft .NET Framework 4.5Windows PowerShell 3.0Windows Installer Version 4.5Microsoft Silverlight 5 browser plug-in"
---

# Administrative tools software requirements in Lync Server 2013
[]
 **In this article**
  
[Microsoft .NET Framework 4.5](#sectionSection0)
  
[Windows PowerShell 3.0](#sectionSection1)
  
[Windows Installer Version 4.5](#sectionSection2)
  
[Microsoft Silverlight 5 browser plug-in](#sectionSection3)
  
This topic describes the software required to install and use Lync Server 2013 administrative tools in addition to the operating system requirements.
  
## Microsoft .NET Framework 4.5
<a name="sectionSection0"> </a>

The 64-bit edition of Microsoft .NET Framework 4.5 is required for Lync Server 2013. 
  
## Windows PowerShell 3.0
<a name="sectionSection1"> </a>

Windows PowerShell 3.0 is required for running any component of Microsoft Lync Server 2013. For more information, see [Installing Windows PowerShell 3.0 for Lync Server 2013](installing-windows-powershell-3-0.md).
  
## Windows Installer Version 4.5
<a name="sectionSection2"> </a>

Lync Server 2013 uses Windows Installer technology to install, uninstall, and maintain various server roles. Windows Installer version 4.5 is available as a redistributable component for the Windows Server operating system. Windows Installer 4.5 ships with Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 meaning that you do not need to download the utility for any computer that is running Lync Server 2013. (Lync Server 2013 can only be installed on computers running Windows Server 2012 R2, Windows Server 2012 or Windows Server 2008 R2.)
  
However, if you want to install Lync Server Management Shell or Lync Server Topology Builder on an administrator workstation you might need to download Windows Installer 4.5. That utility ships with Windows 7 and Windows 2008 R2 but not with any previous versions of the Windows operating system. You can download Windows Installer 4.5 from the Microsoft Download Center at [https://go.microsoft.com/fwlink/p/?linkid=197395](https://go.microsoft.com/fwlink/p/?linkid=197395).
  
## Microsoft Silverlight 5 browser plug-in
<a name="sectionSection3"> </a>

Lync Server 2013 Control Panel is a web-based tool and requires that you install the latest version of Microsoft Silverlight 5 browser plug-in. When you start Lync Server 2013 Control Panel, if this software is not installed or if an earlier version is installed, Lync Server 2013 Control Panel prompts you to install the required version.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md)
#### 

[Administrative tools infrastructure requirements in Lync Server 2013](administrative-tools-infrastructure-requirements.md)
  
[Administrator rights and permissions required for setup and administration of Lync Server 2013](administrator-rights-and-permissions-required-for-setup-and-administration.md)

