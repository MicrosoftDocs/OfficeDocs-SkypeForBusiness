---
title: "Understanding firewall requirements for SQL Server with Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 31d7df2c-589f-465e-be74-cf6767db190d
description: "In this articleRequirements for a Firewall Exception When Using the Default Instance Requirements for a Firewall Exception for the SQL Server Browser ServiceRequirements for Static Listening Ports When Using Named InstancesSQL Server Documentation"
---

# Understanding firewall requirements for SQL Server with Lync Server 2013
[]
 **In this article**
  
[Requirements for a Firewall Exception When Using the Default Instance ](#sectionSection0)
  
[Requirements for a Firewall Exception for the SQL Server Browser Service](#sectionSection1)
  
[Requirements for Static Listening Ports When Using Named Instances](#sectionSection2)
  
[SQL Server Documentation](#sectionSection3)
  
For a Standard Edition deployment, firewall exceptions are created automatically during Lync Server 2013 Setup. However, for Enterprise Edition deployments, you must configure the firewall exceptions manually on the SQL Server Back End Server. The TCP/IP protocol allows for a given port to be used once for a given IP address. This means that for the SQL Server-based server you can assign the default database instance the default TCP port 1433. For any other instances you will need to use the SQL Server Configuration Manager to assign unique and unused ports. This topic covers:
  
- Requirements for a firewall exception when using the default instance
    
- Requirements for a firewall exception for the SQL Server Browser service
    
- Requirements for static listening ports when using named instances
    
## Requirements for a Firewall Exception When Using the Default Instance
<a name="sectionSection0"> </a>

If you are using the SQL Server default instance for any database when deploying Lync Server 2013, the following firewall rule requirements are used to help ensure communication from the Front End pool to the SQL Server default instance.
  
|**Protocol**|**Port**|**Direction**|
|:-----|:-----|:-----|
|TCP  <br/> |1433  <br/> |Inbound to SQL Server  <br/> |
   
## Requirements for a Firewall Exception for the SQL Server Browser Service
<a name="sectionSection1"> </a>

The SQL Server Browser service will locate database instances and communicate the port that the instance (named or default) is configured to use.
  
|**Protocol**|**Port**|**Direction**|
|:-----|:-----|:-----|
|UDP  <br/> |1434  <br/> |Inbound  <br/> |
   
## Requirements for Static Listening Ports When Using Named Instances
<a name="sectionSection2"> </a>

When using named instances in the SQL Server configuration for databases supporting Lync Server 2013, you configure static ports by using SQL Server Configuration Manager. After the static ports have been assigned to each named instance, you create exceptions for each static port in the firewall.
  
|**Protocol**|**Port**|**Direction**|
|:-----|:-----|:-----|
|TCP  <br/> |Statically defined  <br/> |Inbound  <br/> |
   
## SQL Server Documentation
<a name="sectionSection3"> </a>

Microsoft SQL Server 2012 documentation provides detailed guidance on how to configure firewall access for databases. For details about Microsoft SQL Server 2012, see "Configuring the Windows Firewall to Allow SQL Server Access" at [https://go.microsoft.com/fwlink/p/?linkId=218031](https://go.microsoft.com/fwlink/p/?linkId=218031).
  

