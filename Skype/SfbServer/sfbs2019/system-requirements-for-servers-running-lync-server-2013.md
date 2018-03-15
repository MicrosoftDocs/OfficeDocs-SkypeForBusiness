---
title: "System requirements for servers running Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 781d487d-5958-416a-becb-904d9af3cc0a
description: "Standard Edition and Enterprise Edition servers share the same software requirements."
---

# System requirements for servers running Lync Server 2013
[]
> [!NOTE]
> For details about hardware requirements, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md). 
  
Standard Edition and Enterprise Edition servers share the same software requirements.
  
Servers running Lync Server 2013, Enterprise Edition are intended for large organizations as the main organizational deployment. Enterprise Edition server is designed to scale to approximately 80,000 homed users per pool. Servers running Lync Server 2013, Standard Edition are intended for smaller organizations and remote locations from the main organization deployment. One pair of Standard Edition servers can support up to 5,000 users.. For details on the differences between Standard Edition servers and Enterprise Edition servers, see [Deployment overview for Lync Server 2013](deployment-overview.md).
  
## Operating System Installation

> [!IMPORTANT]
> Lync Server 2013 is available only in a 64-bit edition, which requires 64-bit hardware and a 64-bit edition of the Windows Server operating system. A 32-bit edition of Lync Server 2013 is not available with this release. 
  
Standard Edition and Enterprise Edition server can use any of the following:
  
- Windows Server 2008 R2 SP1 or latest service pack
    
- Windows Server 2012
    
- Windows Server 2012 R2
    
Install the operating system software on the Standard Edition Server or Enterprise Edition Front End Server. Apply all updates in order to bring the operating system up to the latest update and required update level consistent with your organization's standards. For more details about the operating requirements, see [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md) in the Supportability documentation. 
  
> [!NOTE]
> For Lync Server 2013 to work on Windows Server 2012 R2, you may need to change the value of a registry key in Windows Server. This change may be necessary for certificates to work correctly, and for clients to register with Survivable Branch Appliances. For more information, see [https://support.microsoft.com/kb/2901554](https://support.microsoft.com/kb/2901554). 
  
### Additional Software for Lync Server 2013

In addition to the updates required for the operating system, Lync Server 2013 requires operating system roles, features, and software to operate. For details about the additional software that must be installed prior to publishing your topology and installing Lync Server 2013, see [Additional software requirements for Lync Server 2013](additional-software-requirements.md) in the Planning documentation. 
  
## Additional Software Necessary for All Server Roles

On all server roles, you must also make sure that Windows PowerShell command-line interface 3.0 and Microsoft .NET Framework 4.5 are installed. 
  
Additionally, Windows PowerShell command-line interface 3.0 and Microsoft .NET Framework 4.5 are required on any computer where you will run the Lync Server administrative tools.
  
### Windows PowerShell 3.0

Lync Server 2013 requires you to install Windows PowerShell 3.0 on each computer that will take part in your Lync Server topology. For details about installing Windows PowerShell 3.0, see [Installing Windows PowerShell 3.0 for Lync Server 2013](installing-windows-powershell-3-0.md).
  
> [!NOTE]
> On Windows Server 2008 R2 with SP1, Windows PowerShell command-line interface 3.0 cannot be installed before installing Microsoft .NET Framework 4.5. 
  
### Microsoft .NET Framework 4.5

When you install Microsoft .NET Framework 4.5 on servers that will run Lync Server 2013 on Windows Server 2012 or Windows Server 2012 R2, you must perform one additional step. After .NET Framework 4.5 is installed, use Server Manager to install HTTP Activation.
  
### To Install .NET 4.5 HTTP Activation on Windows Server 2012 or Windows Server 2012 R2

1. From the **Start** menu, click **Programs**, then click **Administrative Tools**, then click **Server Manager**. 
    
2. In Server Manager, under **Features Summary**, choose **Add Features**. 
    
3. Expand **.NET Framework 4.5**.
    
4. Select **WCF Activation** if it isn't already selected. Then select **HTTP Activation**.
    
5. Click **Next** and follow the prompts to finish the installation. 
    

