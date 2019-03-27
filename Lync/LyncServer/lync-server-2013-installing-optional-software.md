---
title: 'Lync Server 2013: Installing optional software'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Installing optional software
ms:assetid: b95b3301-fa1e-4b96-9af4-05b43d39db8d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615032(v=OCS.15)
ms:contentKeyID: 51541509
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Installing optional software in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

The Microsoft Lync Server 2013, Planning Tool is designed to export to Microsoft Excel and Microsoft Visio. While these applications are not required for the operation of the Planning Tool, they do add significant value to the deployment and documentation of your design.

<div>

## Optional Software

<div>

## Microsoft Excel

Exporting your design to Microsoft Excel creates a report that displays seven tabs in the spreadsheet:

  - Summary – Displays information on site configuration, including user count, capacity settings, and server profile information.

  - Hardware Profile – Displays a report on the recommended hardware configurations for servers that are specified in the topology, including CPU, memory, disk, and network interface. The quantity and recommended specifications for the server components are also included. In addition, each server is defined by site to provide a complete representation of server requirements by site.

  - Ports Requirements – Displays a report of all ports that are enabled, and the association to Domain Name System load balancing (DNS LB) and hardware load balancers (HLB). You should use this report to plan your firewall and DNS LB and HLB configurations.

  - Summary Report – Displays the general summary of the settings that are required to set up your Edge Server network.

  - Certificates Report – Displays the subject name and subject alternate names that are required for the certificates needed to get the Edge Servers running.

  - Firewall Report – Displays the source and destination ports and IP addresses for both External and Internal interfaces.

  - DNS Report – Displays the fully qualified domain name (FQDN) and IP/VIP addresses required for each DNS entry that you create.

</div>

<div>

## Microsoft Visio

Exporting your design to Microsoft Visio creates a diagram for use in your documentation purposes of your configured topology and infrastructure. The imported diagram can be edited and rearranged to meet your documentation needs. The typical Visio diagram will include:

<div>


> [!NOTE]  
> If your design is large enough to require more than three Front End Servers, an additional page will be created for the Front End pool, Front End Servers, the computer running SQL Server, IP addresses, and FQDNs.



</div>

  - Global Topology – Diagram of configured Lync Server 2013 sites.

  - Site Name tab – Displays the site configuration topology with Edge Server, firewall, public switched telephone network (PSTN) with gateways, and the internal server deployment. Internal deployment consists of configured servers and pools, including the Front End pools, SQL Server-based servers, Active Directory Domain Services, Directors, Exchange Unified Messaging (UM) servers, Exchange Mailbox Servers, Office Web Apps Servers, Mediation Servers, and Persistent Chat Servers.

  - Edge Network Diagram – Diagram detailing the Edge Server configuration with associated IP addresses and FQDNs. DNS load balancing and hardware load balancers are also included. Additionally, Directors and the Front End Server or Front End pool are displayed, with associated DNS LB or HLB and the assigned IP address (the Planning Tool supports both IPv4 and IPv6 addresses) and FQDN.

</div>

</div>

<div>

## See Also


[Installing the Planning Tool in Lync Server 2013](lync-server-2013-installing-the-planning-tool.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

