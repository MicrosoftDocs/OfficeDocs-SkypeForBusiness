---
title: 'Lync Server 2013: Monitoring network performance'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Monitoring network performance
ms:assetid: bc3a01da-91eb-4c0c-9598-35e5e46b00f6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720923(v=OCS.15)
ms:contentKeyID: 63969647
ms.date: 04/27/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Monitoring network performance in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-04-27_

Lync Server 2013 is a real-time communications technology that relies heavily on the network to enable communication between users—either through instant messaging (IM), voice calls, or video communication. It is therefore important to monitor the network performance continuously to help guarantee that a user’s chosen communication modality provides the best possible experience.

Network performance can be measured at two levels:

  - **Overall network performance**   This level of performance measurement will allow an organization to create a "big-picture" view of their network and is usually implemented through third-party network monitoring systems. These systems will receive performance and capacity data from remote network devices such as routers and switched throughout the network to allow administrators to determine the health of any given network component at any time of day.

  - **Individual server performance**   This level of performance measurement is limited to a specific server and will help administrators with gauging the network performance of a specific server to either help with troubleshooting a specific performance issue or to gauge the respective server’s performance over a given period as part of a capacity planning process.

You can monitor the network by using the tools described in the following sections.

<div>

## Tools for Overall Network Performance Monitoring

<div>

## System Center Operations Manager 2012

System Center Operations Manager provides end-to-end service management that is easy to customize and extend for improved service levels across an IT environment. This enables Operations and IT Management teams to identify, and resolve issues affecting the health of distributed IT services. End-to-end service management is not restricted to Microsoft-based environments. Support for Web Services for Management (WS-Management), Simple Network Management Protocol (SNMP), and partner solutions allow for systems that do not run Microsoft operating systems and hardware to be included in service monitoring within System Center Operations Manager 2012.

</div>

<div>

## System Center Operations Manager 2012 and Third-Party Network Management Solutions

**EMC Smarts**   EMC Solutions for Operations Manager help you quickly resolve issues affecting service levels throughout. By using EMC Solutions for Operations Manager, you can manage and monitor your whole IT service chain with one integrated, automated solution. You'll easily identify the root causes of performance and availability issues, and resolve them faster which reduces effects and costs. Key benefits include the following:

  - Advanced, easy-to-use management   Focus on delivering strategic business value instead of manually sorting and filtering confusing alerts.

  - **Faster resolution**   Solve IT issues and respond to business needs faster, reducing effect and cost.

  - **Streamlined operations**   Avoid IT complexity by combining multiple management tools, applications, and terminals.

More information can be found here:

[Microsoft System Center Operations Manager](http://go.microsoft.com/fwlink/p/?linkid=243651)

[Solutions for Microsoft System Center Operations Manager](http://www.emc.com/collateral/software/data-sheet/h6135-server-manager-ds.pdf)

</div>

<div>

## Third-Party Solutions

**HP Network Management Center (previously known as HP OpenView)**   [HP Network Management Center](http://www8.hp.com/us/en/software-solutions/network-management/index.html?%26zn=bto%26cp=1-11-15-119_4000_100__) provides integrated fault and performance management to improve network availability and performance. Network Management Center is part of the HP automated network management solution that unifies fault, performance, configuration, and change management.

**Cisco Network Management and Automation products**   For the Enterprise, Cisco has several management products available including CiscoWorks LAN Management Solution and Cisco Network Analysis Module, to help improve operational efficiency and reduce network downtime. For additional data on these products, refer to the Cisco website at [http://www.cisco.com/en/US/products/sw/netmgtsw/index.html](http://www.cisco.com/en/us/products/sw/netmgtsw/index.html).

Simple Network Management Protocol (SNMP)   Simple Network Management Protocol (SNMP) is a network management standard that defines a strategy for managing TCP/IP networks. SNMP enables you to capture configuration and status information about the network, and send the information to a designated computer for event monitoring. This standards based network management protocol uses a distributed architecture that includes the following:

  - Multiple managed nodes, each with an SNMP entity called an agent which provides remote access to management instrumentation.

  - At least one SNMP entity known as a manager which runs management applications to monitor and control managed elements. Managed elements are devices such as hosts, routers, and so on. They are monitored and controlled by accessing their management information.

  - A management protocol, SNMP, is used to communicate management information between the management stations and agents. Management information refers to a collection of managed objects that live in a virtual information store called a Management Information Base (MIB).

<div>


> [!NOTE]  
> Examples of third-party network monitoring solutions are provided above. This list is not definitive and Microsoft does not favor any specific vendor solution. Consult with a network service provider and or your respective technology provider to determine the best network monitoring solution for your organization.



</div>

</div>

</div>

<div>

## Tools for Monitoring Individual Server Network Performance

<div>

## System Center Operations Manager 2012

System Center Operations Manager 2012 would allow administrators to view network performance of individual servers through the Windows Server 2012 Management Pack: The Windows Server operating system management pack includes a "Performance" management pack that would allow administrators to monitor Network Adapter performance and adapter health.

</div>

<div>

## Windows Network Monitor

Collects, displays, analyzes resource usage on a server, and measures network traffic. Network Monitor exclusively monitors network activity. By capturing and analyzing network data, and using this data with performance logs, you can determine the network usage, identify network issues, and forecast future network needs.

For more information about Network Monitor 3.4, and to learn how to install and configure Network Monitor and capture and analyze data, review this session: Network Monitor 3.3 Overview. Also, review the [Network Monitor blog](http://blogs.technet.com/b/netmon/).

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

