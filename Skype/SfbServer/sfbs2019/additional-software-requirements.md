---
title: "Additional software requirements for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 87b318e3-03ae-41f7-af5e-29bb294f6af0
description: "In this articleAdditional Software Necessary for All Internal Server RolesWindows PowerShell 3.0Microsoft .NET Framework 4.5Windows Identity FoundationAdditional Software for All Front End Servers and Standard Edition ServersAdditional Software for Front End Servers and Standard Edition Servers Running on Windows Server 2012Additional Software for DirectorsAdditional Software for Persistent Chat Front End ServersAdditional Software for Edge ServersDo Not Install Layered Socket Providers on Media Servers"
---

# Additional software requirements for Lync Server 2013
[]
 **In this article**
  
[Additional Software Necessary for All Internal Server Roles](#sectionSection0)
  
[Windows PowerShell 3.0](#sectionSection1)
  
[Microsoft .NET Framework 4.5](#sectionSection2)
  
[Windows Identity Foundation](#sectionSection3)
  
[Additional Software for All Front End Servers and Standard Edition Servers](#sectionSection4)
  
[Additional Software for Front End Servers and Standard Edition Servers Running on Windows Server 2012](#sectionSection5)
  
[Additional Software for Directors](#sectionSection6)
  
[Additional Software for Persistent Chat Front End Servers](#sectionSection7)
  
[Additional Software for Edge Servers](#sectionSection8)
  
[Do Not Install Layered Socket Providers on Media Servers](#sectionSection9)
  
In addition to the hardware and operating system requirements for server platforms, Lync Server 2013 requires the installation of additional software on the servers that you deploy.
  
> [!NOTE]
> For details about the platform requirements for servers running Lync Server, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md) and [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md). For details about system requirements for client computers and devices, see [Planning for clients and devices in Lync Server 2013](planning-for-clients-and-devices-in-lync-server.md) in the Planning documentation. For details about software requirements for administrative tools, see [Administrative tools software requirements in Lync Server 2013](administrative-tools-software-requirements.md). 
  
## Additional Software Necessary for All Internal Server Roles
<a name="sectionSection0"> </a>

This section lists software necessary on all internal server roles, which are all Lync Server server roles except for Edge Server. The requirements for the Edge Servers and Edge pools are listed later in this topic under **Additional Software for Edge Servers**.
  
## Windows PowerShell 3.0
<a name="sectionSection1"> </a>

Each server running Lync Server 2013 must have the correct release of Windows PowerShell 3.0 installed. For details, see [Installing Windows PowerShell 3.0 for Lync Server 2013](installing-windows-powershell-3-0.md). 
  
## Microsoft .NET Framework 4.5
<a name="sectionSection2"> </a>

Lync Server requires Microsoft .NET Framework 4.5 on all internal server roles and on any computer where you will run the Lync Server administrative tools or Microsoft Lync Server 2013, Planning Tool. For Lync Server 2013, you must manually install the 64-bit edition of Microsoft .NET Framework 4.5 on the server prior to installing Lync Server 2013. To manually install it, download the Microsoft .NET 4.5 Framework from the Microsoft Download Center at [https://go.microsoft.com/fwlink/p/?LinkId=268529](https://go.microsoft.com/fwlink/p/?LinkId=268529)
  
### Installing Microsoft .NET Framework 4.5 on Servers Running Windows Server 2012

When you install Microsoft .NET Framework 4.5 on servers that will run Lync Server 2013 and Windows Server 2012, you must perform one additional step. After .NET Framework 4.5 is installed, use Server Manager to install HTTP Activation.
  
### To Install .NET 4.5 HTTP Activation on Windows Server 2012

1. From the **Start** menu, click **Programs**, then click **Administrative Tools**, then click **Server Manager**. 
    
2. In Server Manager, under **Features Summary**, choose **Add Features**. 
    
3. Expand **.NET Framework 4.5**.
    
4. Select **WCF Activation** if it isn't already selected. Then select **HTTP Activation**.
    
5. Click **Next** and follow the prompts to finish the installation. 
    
## Windows Identity Foundation
<a name="sectionSection3"> </a>

 **Windows Identity Foundation** in Lync Server 2013 requires the installation of Windows Identity Foundation in order to support server to server authentication scenarios. Windows Server 2008 R2 and Windows Server 2012 require different procedures to install the Windows Identify Foundation. Select your server operating system from the following list: 
  
- Windows Server 2008 R2 For Windows Server 2008 R2, you check to see if it has already been installed on your computer. To do this, go to **Add/Remove Programs**, **View Installed Updates**, and look under **Windows** for the entry **Windows Identity Foundation (KB974405)**. For details about installing Windows Identity Foundation, see [https://go.microsoft.com/fwlink/p/?linkId=204657](https://go.microsoft.com/fwlink/p/?linkId=204657).
    
- Windows Server 2012 For Windows Server 2012, you use **Server Manager** to install the Windows Identity Foundation. In the Server Manager **Add Roles and Features Wizard**, select **Features**. Select **Windows Identity Foundation 3.5** from the list. Click **Next**, then click **Install**.
    
## Additional Software for All Front End Servers and Standard Edition Servers
<a name="sectionSection4"> </a>

All Front End Servers and Standard Edition servers must also run Internet Information Services (IIS) with certain modules. Additionally, all Front End Servers and Standard Edition servers where conferencing, Call Park application, Announcement, or Response Groups are deployed must run Windows Media Format Runtime.
  
### Internet Information Services (IIS)

Front End Servers and Standard Edition servers must run Internet Information Services (IIS), with the following modules:
  
- Static Content
    
- Default Document
    
- HTTP Errors
    
- ASP.NET
    
- .NET Extensibility
    
- Internet Server API (ISAPI) Extensions
    
- ISAPI Filters
    
- HTTP Logging
    
- Logging Tools
    
- Tracing
    
- Windows Authentication
    
- Request Filtering
    
- Static Content Compression
    
- Dynamic Content Compression
    
- IIS Management Console 
    
- IIS Management Scripts and Tools
    
- Anonymous Authentication (this is installed by default when IIS is installed.)
    
- Client Certificate Mapping Authentication
    
### Windows Media Format Runtime and Windows Desktop Experience

 **Windows Desktop Experience** All Front End Servers and Standard Edition servers where conferencing will be deployed must have the Windows Media Format Runtime installed, which, except for Windows Server 2012 is installed as part of the Windows desktop experience. Windows Server 2012 requires Microsoft Media Foundation. The Windows Media Format Runtime is required to run the Windows Media Audio (.wma) files that the Call Park, Announcement, and Response Group applications play for announcements and music. 
  
We recommend that you install Windows desktop experience before you install Lync Server 2013. If Lync Server 2013 does not find this software on the server, it will prompt you to install it, and then you must restart the server to complete installation.
  
## Additional Software for Front End Servers and Standard Edition Servers Running on Windows Server 2012
<a name="sectionSection5"> </a>

Front End Servers require .NET 3.5, which is not installed by default on Windows Server 2012. To install it, put your Windows Server 2012 installation media in Drive D and type the following:
  
```
Add-WindowsFeature RSAT-ADDS, Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Compat, Desktop-Experience, Telnet-Client, BITS -Source D:\sources\sxs
```

For details about installing .NET 3.5 on servers running Windows Server 2012, see "Microsoft .NET Framework 3.5 Deployment Considerations" at [https://go.microsoft.com/fwlink/p/?linkid=275032](https://go.microsoft.com/fwlink/p/?linkid=275032). 
  
## Additional Software for Directors
<a name="sectionSection6"> </a>

Directors must run Internet Information Services (IIS), with the following modules:
  
- Static Content
    
- Default Document
    
- HTTP Errors
    
- ASP.NET
    
- .NET Extensibility
    
- Internet Server API (ISAPI) Extensions
    
- ISAPI Filters
    
- HTTP Logging
    
- Logging Tools
    
- Tracing
    
- Windows Authentication
    
- Request Filtering
    
- Static Content Compression
    
- IIS Management Console 
    
- IIS Management Scripts and Tools
    
- Anonymous Authentication (This is installed by default when IIS is installed.)
    
- Client Certificate Mapping Authentication
    
## Additional Software for Persistent Chat Front End Servers
<a name="sectionSection7"> </a>

Persistent Chat Front End Servers must run Message Queuing (also known as MSMQ), which is a component of Windows Server.
  
For information on enabling MSMQ, [click here.](https://technet.microsoft.com/en-us/library/cc771474.aspx)
  
## Additional Software for Edge Servers
<a name="sectionSection8"> </a>

Edge Servers require the following software:
  
- Each server running Lync Server 2013 must have the correct release of Windows PowerShell 3.0 installed. For details, see [Installing Windows PowerShell 3.0 for Lync Server 2013](installing-windows-powershell-3-0.md).
    
- Lync Server requires Microsoft .NET Framework 4.5. For Lync Server 2013 installed on Windows Server 2008 R2, you must manually install the 64-bit edition of Microsoft .NET Framework 4.5 on the server prior to installing Lync Server 2013. To manually install it, download the Microsoft .NET 4.5 Framework from the Microsoft Download Center at [https://go.microsoft.com/fwlink/p/?LinkId=268529](https://go.microsoft.com/fwlink/p/?LinkId=268529)
    
- **Windows Identity Foundation** in Lync Server 2013 requires the installation of Windows Identity Foundation in order to support server to server authentication scenarios. Windows Server 2008 R2 and Windows Server 2012 require different procedures to install the Windows Identify Foundation. Select your server operating system from the following list: 
    
  - Windows Server 2008 R2 For Windows Server 2008 R2, you check to see if it has already been installed on your computer. To do this, go to **Add/Remove Programs**, **View Installed Updates**, and look under **Windows** for the entry **Windows Identity Foundation (KB974405)**. For details about installing Windows Identity Foundation, see [https://go.microsoft.com/fwlink/p/?linkId=204657](https://go.microsoft.com/fwlink/p/?linkId=204657).
    
  - Windows Server 2012 For Windows Server 2012, you use **Server Manager** to install the Windows Identity Foundation. In the Server Manager **Add Roles and Features Wizard**, select **Features**. Select **Windows Identity Foundation 3.5** from the list. Click **Next**, then click **Install**.
    
## Do Not Install Layered Socket Providers on Media Servers
<a name="sectionSection9"> </a>

Do not install any Microsoft Internet Security and Acceleration (ISA) Server client software, or any other Winsock Layered Service Providers (LSP) software, on any Front End Servers or stand-alone Mediation Servers. Installing this software could cause poor media traffic performance.
  
## See also
<a name="sectionSection9"> </a>

#### 

[Administrative tools software requirements in Lync Server 2013](administrative-tools-software-requirements.md)

