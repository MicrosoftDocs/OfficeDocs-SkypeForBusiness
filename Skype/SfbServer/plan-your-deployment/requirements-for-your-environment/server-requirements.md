---
title: "Server requirements for Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/15/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 8d47b242-b93d-4c2e-a658-23b78bca30b1
description: "Summary: Prepare your Skype for Business Server 2015 servers with this topic. Hardware, OS, databases, software, all the system requirements and recommendations are here to help ensure a successful install and deployment of your server farm."
---

# Server requirements for Skype for Business Server 2015
 
**Summary:** Prepare your Skype for Business Server 2015 servers with this topic. Hardware, OS, databases, software, all the system requirements and recommendations are here to help ensure a successful install and deployment of your server farm.

If you're looking for environmental requirements, such as Active Directory, DNS or certificates, you can check out the [Environmental requirements for Skype for Business Server 2015](environmental-requirements.md) doc.
  
As you might expect, there are some preparations to make before you begin deploying Skype for Business Server 2015. This article will walk you through planning for the following:
  
- [Hardware for Skype for Business Server 2015](server-requirements.md#Hardware)
  
- [Operating systems for Skype for Business Server 2015](server-requirements.md#OS)
  
- [Back end databases that will work with Skype for Business Server 2015](server-requirements.md#DBs)
  
- [Software that should be installed before a Skype for Business Server 2015 deployment](server-requirements.md#Software)
  
## Hardware for Skype for Business Server 2015
<a name="Hardware"> </a>

Now that you have your topology down (and if you don't, you can check out the [Topology Basics for Skype for Business Server 2015](../../plan-your-deployment/topology-basics/topology-basics.md) topic), it's time to think about servers. Skype for Business Server 2015 servers will require 64-bit hardware. Our recommendations for hardware are below. These aren't requirements, but they reflect the requirements necessary for optimal performance. We have capacity planning documentation that will help you determine if you need more than this, depending on your circumstances.
  
Recommended hardware for Front End Servers, Back End Servers, Standard Edition servers, and Persistent Chat Servers:
  
|**Hardware component**|**Recommended**|
|:-----|:-----|
|CPU  <br/> |64-bit dual processor, hex-core, 2.26 gigahertz (GHz) or higher.  <br/> Intel Itanium processors are not supported for Skype for Business Server 2015 roles.  <br/> |
|Memory  <br/> |32 gigabytes (GB).  <br/> |
|Disk  <br/> |EITHER:  <br/> • 8 or more 10000 RPM hard disk drives with at least 72 GB free disk space (two of the disks using RAID 1 and 6 using RAID 10).  <br/> OR  <br/> • Solid state drives (SSDs) able to provide the same free space and similar performance to 8 10000 RPM mechanical disk drives.  <br/> |
|Network  <br/> |1 dual-port network adapter, 1 Gbps or higher (2 network adapters can be used, but they need to be teamed with a single MAC address and a single IP address).  <br/> Dual or multi-homed configurations are **not** supported for Front End Servers, Back End Servers, Standard Edition servers, and Persistent Chat Servers. <br/> As long as they are not exposed to the operating system and are being used to monitor and manage server hardware, you can have out of band management systems, such as DRAC or ILO. This scenario doesn't constitute a multi-homed server, and it is supported.  <br/> |
   
Recommended hardware for Edge Servers, standalone Mediation Servers, Video Interop Servers, and Directors:
  
|**Hardware component**|**Recommended**|
|:-----|:-----|
|CPU  <br/> |64-bit dual processor, quad-core, 2.26 gigahertz (GHz) or higher.  <br/> Intel Itanium processors are not supported for Skype for Business Server 2015 roles.  <br/> |
|Memory  <br/> |16 gigabytes.  <br/> |
|Disk  <br/> |EITHER:  <br/> • 4 or more 10000 RPM hard disk drives with at least 72 GB free disk space (the disks should be in a 2x RAID 1 configuration).  <br/> OR  <br/> • Solid state drives (SSDs) able to provide the same free space and similar performance to 4 10000 RPM mechanical disk drives.  <br/> |
|Network  <br/> |1 dual-port network adapter, 1 Gbps or higher (2 network adapters can be used, but they need to be teamed with a single MAC address and a single IP address).  <br/> Dual or multi-homed configurations are **not** supported for Video Interop Servers and Directors. <br/> Edge servers will require two network interfaces that are dual-port network adapters, 1 Gbps or higher (or two paired network adapters, for a total of four, each pair being teamed with a single MAC address and a single IP address, for a total of two pairs).  <br/> On standalone Mediation Servers the installation of additional network interface cards (NICs) to allow the configuration of a specific PSTN IP address is supported.  <br/> |
   
## Operating systems for Skype for Business Server 2015
<a name="OS"> </a>

Once you have the hardware in place, you'll need to install operating systems (OS). These are the OS that will allow you to install and successfully use Skype for Business Server 2015.
  
|||
|:-----|:-----|
|Windows Server 2019 (You need Skype for Business Cumulative Update 9 or later). <br/> |Windows Server 2016 (You need Skype for Business Cumulative Update 5 or later. For more information check [KB4015888](https://support.microsoft.com/en-gb/help/4015888/how-to-install-skype-for-business-server-2015-on-windows-server-2016))  <br/> ||
|Windows Server 2012 R2 Datacenter OS with all required updates installed.  <br/> |Windows Server 2012 R2 Standard OS with all required updates installed.  <br/> |
|Windows Server 2012 Datacenter OS with all required updates installed.  <br/> |Windows Server 2012 Standard OS with all required updates installed.  <br/> |
   
If it's not on this list, it won't work properly, please don't try it for new installs of Skype for Business Server 2015.
  
> [!NOTE]
> You may have noticed Windows Server 2008 R2 isn't on this list. That's because we recommend Windows Server 2012 R2 for all new servers to be used for SFB. You should only be using Windows Server 2008 R2 when you have existing servers with Lync Server 2013 already installed, and you're intending to do an in-place upgrade of them. Windows Server 2008 R2 reached the end of the mainstream support lifecycle on 1/13/2015. 
  
In addition to the latest service pack, you'll want to ensure the following updates are installed where relevant to you:
  
- For Windows Server 2012, KB article 2858668 should be installed before an upgrade. [Get it here](https://support.microsoft.com/en-us/kb/2858668/).
    
- If you have Windows Server 2012 R2, please install KB article 2982006 before upgrading. [It's found here](https://support.microsoft.com/en-us/kb/2982006/).
    
- If you're upgrading on a Windows Server 2008 R2 box (see the Note above), then you'll want to install KB article 2533623 first. [It's at this link](https://support.microsoft.com/en-us/kb/2533623/).
    
## Back end databases that will work with Skype for Business Server 2015
<a name="DBs"> </a>

> [!NOTE]
> SQL back end must be local to the SFB front ends (not across a low speed link). It is not supported to share SQL back ends between two or more pools.

When installing Skype for Business Server 2015 Standard Edition, you'll have SQL Server 2014 Express (64-bit edition) is automatically installed as well.
  
Skype for Business Server 2015 Enterprise Edition is a little more complicated, but the supported list is below (everything is 64-bit edition, you'll notice, please don't use 32-bit editions):
  
||||||
|:-----|:-----|:-----|:-----|:-----|
|Microsoft SQL Server 2019 Enterprise (64-bit edition), and we recommend running with the latest service pack. <br/> |Microsoft SQL Server 2017 Enterprise (64-bit edition), and we recommend running with the latest service pack. <br/> |Microsoft SQL Server 2016 Enterprise (64-bit edition) with Service Pack 1 or later, and you must run with Skype for Business Cumulative Update 7 or later ([download Skype for Business Cumulative Update](https://support.microsoft.com/en-us/help/3061064)).  <br/> |Microsoft SQL Server 2014 Enterprise (64-bit edition), and you must run with Cumulative Update 6 or later ([download Cumulative Update 6](https://support.microsoft.com/en-us/kb/3031047/)).  <br/> |Microsoft SQL Server 2012 Enterprise (64-bit edition), and we recommend running with the latest service pack.  <br/> |
|Microsoft SQL Server 2019 Standard (64-bit edition), and we recommend running with the latest service pack. <br/> |Microsoft SQL Server 2017 Standard (64-bit edition), and we recommend running with the latest service pack. <br/> |Microsoft SQL Server 2016 Standard (64-bit edition) with Service Pack 1 or later, and you must run with Skype for Business Cumulative Update 7 or later ([download Skype for Business Cumulative Update](https://support.microsoft.com/en-us/help/3061064)).  <br/> |Microsoft SQL Server 2014 Standard (64-bit edition), and you must run with Cumulative Update 6 or later ([download Cumulative Update 6](https://support.microsoft.com/en-us/kb/3031047/)).  <br/> |Microsoft SQL Server 2012 Standard (64-bit edition), and we recommend running with the latest service pack.  <br/> |
   
If you don't see the SQL Server edition you want to use listed here, you can't use it.
  
> [!NOTE]
> You're also going to need to install SQL Server Reporting Services for the Monitoring Server role.

### Microsoft Exchange storage
Meeting content files, such as PowerPoint presentations, are archived as attachments. If you want to store Skype for Business archive data with Exchange compliance data, you must use Exchange for your Exchange deployment and ensure that the maximum storage size supports storage of the meeting content files. You must deploy Exchange prior to deploying and enabling archiving using the Microsoft Exchange integration option. 
    
    If you choose to use Exchange storage, you do not need to deploy separate SQL Server databases for archiving, unless you have Skype for Business users who are not homed on your Exchange servers. If you deploy archiving using the Microsoft Exchange integration option, Skype for Business archive data is stored with Exchange compliance data only for the users who are homed on your Exchange servers. 
  
## Hardware and software requirements for archiving in Skype for Business Server 2015
  
Archiving is not a defined server role, you do not need to install a separate server for archiving. Unified Data Collection Agents are installed and activated automatically on every Enterprise Edition Front End pool and every Standard Edition Server. You will need to enable and publish your archiving topology by using Topology Builder.
    
Archiving uses the Skype for Business Server file storage for temporary storage of meeting content files, so you do not set up a separate file store for archiving.
    
Microsoft Message Queuing is not required.
    
You will need to set up the infrastructure for archiving storage. This includes choosing either Exchange or Archiving storage using SQL Server.   Skype for Business Server Archiving infrastructure requirements are the same as for deployment of Skype for Business Server. For details, see [Requirements for your Skype for Business environment](../../plan-your-deployment/requirements-for-your-environment/requirements-for-your-environment.md). 
  
> [!NOTE]
> To support users who are not homed on Exchange servers, or if you do not want to use the Microsoft Exchange integration option, you must deploy archiving storage using a 64-bit SQL Server database. 
    
You must set up the SQL Server platforms prior to deploying and enabling archiving. If the account to be used to publish the topology has the appropriate administrator rights and permissions, you can create the Archiving database (LcsLog) when you publish your topology. You can also create the database later, included as part of the installation procedure. For details about SQL Server, see the [SQL Server documentation](https://go.microsoft.com/fwlink/p/?linkID=129045).
    
The load increase for archiving can be significant. Therefore, you should ensure that disk space is adequate for Front End Servers on which archiving is enabled.

### SQL Mirroring, SQL Clustering, and SQL Always On

You are able to use SQL Mirroring or SQL Clustering with Skype for Business Server 2015, it's supported. SQL Mirroring's set up through the Skype for Business Server Topology Builder. If you're intent on setting up SQL Clustering, that's done in SQL Server.
  
Make sure you have an active/passive configuration for SQL Clustering, as that's what's supported. Don't share the passive node with any other SQL instance.
  
You can have the following for failover clustering:
  
Two-node:
  
- Microsoft SQL Server 2019 Standard (64-bit edition), and we recommend running with the latest service pack.

- Microsoft SQL Server 2017 Standard (64-bit edition), and we recommend running with the latest service pack.

- Microsoft SQL Server 2016 Standard (64-bit edition) with Service Pack 1 or later. We recommend running with the latest service pack.

- Microsoft SQL Server 2014 Standard (64-bit edition), and we recommend running with the latest service pack.
    
-  Microsoft SQL Server 2012 Standard (64-bit edition), and we recommend running with the latest service pack.

Sixteen-node:

- Microsoft SQL Server 2019 Enterprise (64-bit edition), and we recommend running with the latest service pack.

- Microsoft SQL Server 2017 Enterprise (64-bit edition), and we recommend running with the latest service pack.

- Microsoft SQL Server 2016 Enterprise (64-bit edition) with Service Pack 1 or later. We recommend running with the latest service pack.
  
- Microsoft SQL Server 2014 Enterprise (64-bit edition), and we recommend running with the latest service pack.
    
- Microsoft SQL Server 2012 Enterprise (64-bit edition), and we recommend running with the latest service pack.

> [!IMPORTANT]
> For upgrading, we do want you to ensure that on your Front End Servers you have at least SQL Server 2012 SP1 installed prior to upgrade. [Here's a link](https://www.microsoft.com/en-us/download/details.aspx?id=35575) to SP1 if you want to download it right away.
  
If you need to read up more on SQL Mirroring, we have a Back End Server high availability in Skype for Business Server 2015 topic. Configure SQL Server clustering for Skype for Business Server 2015 has the steps for getting clustering ready. There are also further links on failover clustering for SQL, for [2014](https://technet.microsoft.com/en-us/library/hh231721.aspx), [2012](https://technet.microsoft.com/en-us/library/hh231721%28v=sql.110%29.aspx), and [2008](https://technet.microsoft.com/en-us/library/ms189134%28v=sql.105%29.aspx).
  
> [!NOTE]
> New to the 2015 release is support of SQL Always On. It is supported, and you can read more about it in the [Back End Server high availability in Skype for Business Server 2015](../../plan-your-deployment/high-availability-and-disaster-recovery/back-end-server.md) topic.

> [!NOTE]
> SQL Mirroring is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The  AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances (FCI), and SQL failover clustering methods are preferred with Skype for Business Server 2019.  

## Software that should be installed before a Skype for Business Server 2015 deployment
<a name="Software"> </a>

There are some things you're going to need to install or configure for any server running Skype for Business Server 2015, and they're listed below. After that are additional requirements for specific server roles.
  
 **All Servers:**
  
|**Software/Role**|**Details**|
|:-----|:-----|
|Windows PowerShell 3.0  <br/> |All Skype for Business Server servers need Windows PowerShell 3.0 installed.  <br/> • If you're doing the installation on Windows Server 2012 or Windows Server 2012 R2, you're set, because it's already there.  <br/> • If you're doing an upgrade on Windows Server 2008 R2, you can download the [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) to get it. <br/> **Tip:** Once you have the correct PowerShell on there, confirm that it's BuildVersion 6.2.9200.0 or later by going to the PowerShell prompt and typing `$PSVersionTable`. This should bring up the information you need.  <br/> |
|Microsoft .NET Framework  <br/> |WCF services is a **Feature** that's installed as a Windows feature, under **Server Manager**, no downloads needed. <br/> • You need to make sure, when you install this feature, or if it's already installed and you're checking on it, that the **HTTP Activation** option is also checked and installed, like so: <br/> ![Screenshot showing HTTP Activation option under the .NET Framework 4.5 Features.](../../media/a4064fa0-fa49-4474-bd98-b9a79ff68f8b.png)Don't worry if you get an additional pop-up saying some other things need to be installed for HTTP Activation to be installed. That's normal, click OK and go ahead. If you don't get this pop-up, then assume those things are already installed, and go ahead.  <br/> Microsoft .NET Framework is usually installed when Windows Server 2012 R2 or Windows Server 2016 are installed. Skype for Business Server works with the following Microsoft .NET Framework versions:  <br/> • .NET 3.5  <br/> • .NET 4.5  <br/> • .NET 4.6.x  <br/> • .NET 4.7.1 and higher (for Skype for Business Server CU 5 or later releases)  <br/>  .NET Framework 3.5 will likely be installed by default on your Windows Server 2008 R2 machine (definitely check to be sure before you upgrade), but it actually won't be on your Windows Server 2012/Windows Server 2012 R2 servers (for new installations). To add it in, you'll need access to your installation drive or media (the place your Windows Server was installed from, or where the install files are now). Then go ahead and install it as a feature from Server Manager, and point to the installation media (specifically the **\sources\sxs** folder) when asked for it, and continue on to install it. <br/> |
|Media Foundation  <br/> |For Windows Server 2016, Windows Server 2012 and Windows Server 2012 R2 the Windows Media Format Runtime installs with Microsoft Media Foundation.  <br/> All Front End Servers and Standard Edition servers used for conferencing require Windows Media Format Runtime to run the Windows Media Audio (.wma) files that the Call Park, Announcement, and Response Group applications play for announcements and music.  <br/> |
|Windows Identity Foundation  <br/> |We need Windows Identity Foundation 3.5 to support server-to-server authentication scenarios for Skype for Business Server 2015.  <br/> • For Windows Server 2012 and Windows Server 2012 R2, there's no need to download anything. Open **Server Manager**, and go to the **Add Roles and Features Wizard**. **Windows Identity Foundation 3.5** is listed under the **Features** section. If it's checked, you're good. Otherwise select it and click Next to reach the **Install** button. <br/> |
|Remote Server Administration Tools  <br/> |Role Administration Tools: AD DS and AD LDS tools  <br/> |
   
 **Front End Servers and Standard Edition server also need:**
  
|**Software/Role**|**Details**|
|:-----|:-----|
|Internet Information Services (IIS)  <br/> |IIS is needed on all Front End Servers, as well as all Standard Edition servers, with the following modules selected:  <br/> • Common HTTP Features: Default Document, HTTP Errors, Static Content  <br/> • Health and Diagnostics: HTTP Logging, Logging Tools, Tracing  <br/> • Performance: Static Content Compression, Dynamic Content Compression  <br/> • Security: Request Filtering, Client Certificate Mapping Authentication, Windows Authentication  <br/> • Application Development: .NET Extensibility 3.5, .NET Extensibility 4.5, ASP.NET 3.5, ASP.NET 4.5, ISAPI Extensions, ISAPI Filters  <br/> • Management Tools: IIS Management Console, IIS Management Scripts and Tools  <br/> We should also note Anonymous Access is also needed, but you get that when you install IIS, so you don't have a place to select that on the list.  <br/> |
|Windows Media Format Runtime  <br/> | For Windows Server 2016, Windows Server 2012, and Windows Server 2012 R2, you'll need to install the **Media Foundation** feature in **Server Manager**. Now, you actually can start your Skype for Business Server 2015 installation without this one, but you'll be prompted to install it, and then reboot the server, before the Skype for Business Server 2015 install continues. Better to do it ahead of time. <br/> |
|Silverlight  <br/> |You can install the latest version of Silverlight at [this link](https://www.microsoft.com/silverlight/).  <br/> |
   
> [!NOTE] 
> You may also need to enable Directory Browsing if you are using a load balancer. 
> Otherwise a blank page will load which the load balancer might consider a failure. 

To help you out, here's a sample PowerShell script you can run to automate this:

```
Add-WindowsFeature NET-Framework-Core, RSAT-ADDS, Windows-Identity-Foundation, Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Dir-Browsing, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Compat, Server-Media-Foundation, BITS, Desktop-Experience, Telnet-Client
```

> [!NOTE] 
> The command looks for source files in a specific order. 
> If you are online, the command accesses Windows Update. 
> However, if you are offline, you need to make sure the source files are available to the command. 
> For more information about using PowerShell to install roles and features, 
> see [Install or Uninstall Roles, Role Services, or Features](https://technet.microsoft.com/en-us/library/hh831809.aspx) 
> Don't forget to run Windows Update again after you install prerequisites, even if you use the PowerShell command.

 **Directors also need:**
  
IIS, with the following modules selected:
  
- Common HTTP Features
    
  - Default Document
    
  - HTTP Errors
    
  - Static Content
    
- Health and Diagnostics
    
  - HTTP Logging
    
  - Logging Tools
    
  - Tracing
    
- Performance
    
  - Static Content Compression
    
- Security
    
  - Request Filtering
    
  - Client Certificate Mapping Authentication
    
  - Windows Authentication
    
- Application Development
    
  - .NET Extensibility 3.5
    
  - .NET Extensibility 4.5
    
  - ASP.NET 3.5
    
  - ASP.NET 4.5
    
  - ISAPI Extension
    
  - ISAPI Filters
    
(If you're wondering, it's the same module set as the Front End Servers and Standard Edition servers, with the Dynamic Content Compression and Management Tools left out.)
  
And we have some PowerShell code below for this too:
  
```
Add-WindowsFeature RSAT-ADDS, Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Scripting-Tools, Web-Mgmt-Compat, Desktop-Experience, Telnet-Client
```

 **Persistent Chat Servers also need:**
  
Message Queuing, which is also called MSMQ. It's a Windows Server component, and you can install it under the Features section in Server Manager. If you want to read more about this, check out [Installing and Managing Message Queuing](https://technet.microsoft.com/en-us/library/cc771474.aspx).
  
 **Last thoughts:**
  
Please don't install any Microsoft Internet Security and Acceleration (ISA) Server client software, or any other Winsock Layered Service Providers (LSP) software (any third-party firewalls or anti-virus network inspection software would be included here) on any of your front end servers or standalone mediation servers. Poor media traffic performance has been seen when that software's installed.
  

