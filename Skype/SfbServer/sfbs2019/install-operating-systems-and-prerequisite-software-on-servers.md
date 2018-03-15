---
title: "Install operating systems and prerequisite software on servers for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 055991e0-5aeb-43fc-a7ba-d4b02316d73b
description: "In this articleInstall Windows Operating Systems on ServersInstall Windows Update on ServersInstall Other Prerequisite Software on Servers"
---

# Install operating systems and prerequisite software on servers for Lync Server 2013
[]
 **In this article**
  
[Install Windows Operating Systems on Servers](#sectionSection0)
  
[Install Windows Update on Servers](#sectionSection1)
  
[Install Other Prerequisite Software on Servers](#sectionSection2)
  
After you have set up the hardware and system infrastructure, you need to install the appropriate Windows operating systems and updates, in addition to all other prerequisite software on each server that you are deploying. This includes each Lync Server 2013 server role and any additional infrastructure servers or servers running SQL Server that are required for your deployment.
  
> [!NOTE]
> This section describes installation of operating systems and prerequisite software for internal servers. If you are deploying Edge Servers to support external user access, you also need to install operating systems and prerequisite software for those servers, including Edge Servers and reverse proxy servers. For details about preparing servers to support external user access, see [Preparing for installation of servers in the perimeter network for Lync Server 2013](preparing-for-installation-of-servers-in-the-perimeter-network.md) in the Deployment documentation. 
  
## Install Windows Operating Systems on Servers
<a name="sectionSection0"> </a>

On each server that you are deploying, install the appropriate Windows operating system as follows:
  
- **Servers running Lync Server 2013** For details about the operating system requirements for servers running Lync Server 2013, see [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md) in the Supportability documentation. 
    
- **Database servers** For details about operating system requirements for database servers, including the back-end database, Archiving database, and Monitoring database, see the SQL Server documentation. For SQL Server 2012, see the SQL Server 2012 Books Online at [https://go.microsoft.com/fwlink/p/?linkId=218015](https://go.microsoft.com/fwlink/p/?linkId=218015).
    
> [!NOTE]
> If you are installing Lync Server 2013 on Windows Server 2008 R2 with SP1, you must first install the update described in the Microsoft Knowledge Based article 2646886, "FIX: Heap corruption occurs when a module calls the InsertEntityBody method in IIS 7.5", at [http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=2646886](http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=2646886). > You must also modify the registry as described in the KB article, [Event IDs 32402, 61045 are logged in Lync Server 2013 Front End servers that are installed in Windows Server 2012 R2](https://go.microsoft.com/fwlink/p/?LinkId=506893). 
  
## Install Windows Update on Servers
<a name="sectionSection1"> </a>

Install the following updates from Windows Update on each server:
  
- **Windows Update for servers running Lync Server 2013** For details about the updates from Windows Update that are required for servers running Lync Server 2013, see [Additional software requirements for Lync Server 2013](additional-software-requirements.md) in the Planning documentation. 
    
- **Database servers** For details about the updates from Windows Update that are required for database servers, including the back-end database, Archiving database, and Monitoring database, see the SQL Server 2012 documentation. For SQL Server 2012, see the SQL Server 2012 Books Online at [https://go.microsoft.com/fwlink/p/?linkId=218015](https://go.microsoft.com/fwlink/p/?linkId=218015).
    
## Install Other Prerequisite Software on Servers
<a name="sectionSection2"> </a>

Lync Server 2013 requires the installation of the following additional software on servers:
  
- **Prerequisite software for servers running Lync Server 2013** The additional software prerequisites for servers running Lync Server 2013 depend on the server role being deployed. For details about the specific software requirements for each server, see [Additional software requirements for Lync Server 2013](additional-software-requirements.md) in the Planning documentation. 
    
- **Windows Identity Foundation** Lync Server 2013 requires the installation of Windows Identity Foundation in order to support server-to-server authentication scenarios. To verify that it has already been installed on your computer, go to Control Panel, click **Programs and Features**, **View installed updates**, and look under **Microsoft Windows**. For details about installing Windows Identity Foundation, see [https://go.microsoft.com/fwlink/p/?linkId=204657](https://go.microsoft.com/fwlink/p/?linkId=204657).
    
- **Microsoft .NET Framework 4.5** The 64-bit edition of Microsoft .NET Framework 4.5 is required for Lync Server 2013. 
    
- **Prerequisite software for database servers** For details about the Windows Update required for database servers, including the back-end database, Archiving database, and Monitoring database, see the SQL Server 2012 documentation at [https://go.microsoft.com/fwlink/p/?linkId=218015](https://go.microsoft.com/fwlink/p/?linkId=218015).
    
    > [!NOTE]
    > Lync Server 2013 automatically installs Microsoft SQL Server 2012 Express on each Standard Edition server and each server running Lync Server 2013 on which the local configuration store is located. 
  
- **Windows Media Format Runtime** All Front End Servers and Standard Edition servers where conferencing will be deployed must have the Windows Media Format Runtime installed. The Windows Media Format Runtime is required to run the Windows Media Audio (.wma) files that the Call Park, Announcement, and Response Group applications play for announcements and music. 
    
    > [!NOTE]
    > For Windows Server 2012 and Windows Server 2012 R2 the Windows Media Format Runtime installs with Microsoft Media Foundation. 
  
    > [!NOTE]
    > For Windows Server 2008 and Windows Server 2008 R2 the Windows Media Format Runtime installs as part of the Windows Desktop Experience. It is recommended that you install Windows Desktop Experience before you install Lync Server 2013. If Lync Server 2013 does not find this software on the server, it will prompt you to install it, and then you must restart the server to complete installation. 
  

