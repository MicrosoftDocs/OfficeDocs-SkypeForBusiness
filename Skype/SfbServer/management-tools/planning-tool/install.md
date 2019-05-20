---
title: "Install the Planning Tool in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 4/5/2016
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: b95b3301-fa1e-4b96-9af4-05b43d39db8d
description: "Before you begin designing and planning your Skype for Business Server 2015 infrastructure by using the Skype for Business Server 2015 Planning Tool, you must first install the Planning Tool. The Planning Tool does not need to be deployed to a workstation or server that is part of the domain or infrastructure where you plan to install Skype for Business Server 2015. The Readme file that accompanies the Planning Tool details important information about installing and using the tool. Some of the information in the Readme file is duplicated here for clarity."
---

# Install the Planning Tool in Skype for Business Server 2015

Before you begin designing and planning your Skype for Business Server 2015 infrastructure by using the Skype for Business Server 2015 Planning Tool, you must first install the Planning Tool. The Planning Tool does not need to be deployed to a workstation or server that is part of the domain or infrastructure where you plan to install Skype for Business Server 2015. The Readme file that accompanies the Planning Tool details important information about installing and using the tool. Some of the information in the Readme file is duplicated here for clarity.

> [!IMPORTANT]
> The Planning Tool requires installation by a user with administrator rights and permissions on the computer on which the tool is to be installed.

The supported operating systems for installation and operation of the Planning Tool are:

- Windows 10

- Windows 8

- Windows 8.1

- Windows Server 2012

- Windows Server 2012 R2

- Windows 7, 32-bit edition

- Windows 7, 64-bit edition using Windows on Win32 (WOW)

- Windows Server 2008 R2, using WOW

Additionally, the Planning Tool requires Microsoft .NET Framework 4.5.

After the preinstallation requirements are met, you can then install the Planning Tool.



## To install the Planning Tool

1. Log on to the local computer as a member of the Administrators group.

2. Using Windows Explorer or a command window, locate the directory where you downloaded the Planning Tool installation files.

3. Locate the SkypeForBusinessPlanningTool.msi. In Windows Explorer, double-click the file. In the command window, type the name of the file, and then press **Enter** to run the file.

4. On the Welcome page of the **Skype for Business Server 2015, Planning Tool Setup Wizard**, click **Next**.

5. Review the **End-User License Agreement**, select **I accept the terms in the License Agreement** if you choose to accept the terms of use in the license agreement, and then click **Next**.

6. Choose where to install the Planning Tool files. The default location is C:\Program Files (x86)\Skype for Business Server 2015\Planning Tool. If you want to change the installation location, click **Change**. On **Change destination folder**, browse or type the location to install the files, click **OK**, and then click **Next**.

7. The installer is now ready to install the Planning Tool. Click **Install** to begin the installation process.

8. The installation will start, and the progress will be displayed. After the installation is successfully completed, click **Finish**.

9. The Planning Tool is ready for use.

## Optional Software
<a name="Optional_Software"> </a>

The Skype for Business Server 2015 Planning Tool is designed to export to Microsoft Excel and Microsoft Visio. While these applications are not required for the operation of the Planning Tool, they do add significant value to the deployment and documentation of your design.

### Microsoft Excel

Exporting your design to Microsoft Excel creates a report that displays seven tabs in the spreadsheet:

- Summary - Displays information on site configuration, including user count, capacity settings, and server profile information.

- Hardware Profile - Displays a report on the recommended hardware configurations for servers that are specified in the topology, including CPU, memory, disk, and network interface. The quantity and recommended specifications for the server components are also included. In addition, each server is defined by site to provide a complete representation of server requirements by site.

- Ports Requirements - Displays a report of all ports that are enabled, and the association to Domain Name System load balancing (DNS LB) and hardware load balancers (HLB). You should use this report to plan your firewall and DNS LB and HLB configurations.

- Summary Report - Displays the general summary of the settings that are required to set up your Edge Server network.

- Certificates Report - Displays the subject name and subject alternate names that are required for the certificates needed to get the Edge Servers running.

- Firewall Report - Displays the source and destination ports and IP addresses for both External and Internal interfaces.

- DNS Report - Displays the fully qualified domain name (FQDN) and IP/VIP addresses required for each DNS entry that you create.

### Microsoft Visio

Exporting your design to Microsoft Visio creates a diagram for use in your documentation purposes of your configured topology and infrastructure. The imported diagram can be edited and rearranged to meet your documentation needs. The typical Visio diagram will include:

> [!NOTE]
> If your design is large enough to require more than three Front End Servers, an additional page will be created for the Front End pool, Front End Servers, the computer running SQL Server, IP addresses, and FQDNs.

- Global Topology - Diagram of configured Skype for Business Server 2015 sites.

- Site Name tab - Displays the site configuration topology with Edge Server, firewall, public switched telephone network (PSTN) with gateways, and the internal server deployment. Internal deployment consists of configured servers and pools, including the Front End pools, SQL Server-based servers, Active Directory Domain Services, Directors, Exchange Unified Messaging (UM) servers, Exchange Mailbox Servers, Office Web Apps Servers, Mediation Servers, and Persistent Chat Servers.

- Edge Network Diagram - Diagram detailing the Edge Server configuration with associated IP addresses and FQDNs. DNS load balancing and hardware load balancers are also included. Additionally, Directors and the Front End Server or Front End pool are displayed, with associated DNS LB or HLB and the assigned IP address (the Planning Tool supports both IPv4 and IPv6 addresses) and FQDN.

## See also
<a name="Optional_Software"> </a>

[Installing the Planning Tool](https://technet.microsoft.com/library/ebdc9e26-4b22-4b02-85b9-7462bcfe7c93.aspx)
