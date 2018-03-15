---
title: "Deployment permissions for SQL Server in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 56ea0c02-bcf5-4d45-aa13-570531c29074
description: "Microsoft SQL Server 2012 has specific requirements when installing and deploying Lync Server 2013. Because Windows and SQL Server define their security differently, logging in as an administrator in the Active Directory domain does not implicitly grant permissions for SQL Server. You must also be a member of the sysadmin entity on the SQL Server-based server you are configuring."
---

# Deployment permissions for SQL Server in Lync Server 2013
[]
Microsoft SQL Server 2012 has specific requirements when installing and deploying Lync Server 2013. Because Windows and SQL Server define their security differently, logging in as an administrator in the Active Directory domain does not implicitly grant permissions for SQL Server. You must also be a member of the sysadmin entity on the SQL Server-based server you are configuring.
  
## Permissions Required for Database and Lync Server Installation

The following options detail three permissions and group membership associations for installation of Lync Server 2013 files and SQL Server databases. Choose the scenario that best meets the requirements of your organization.
  
**Permissions and Group Membership Associations**

|**SQL Server or Lync Server 2013 role**|**Role-Typical SQL Server permissions and group membership**|**Role-typical Lync Server 2013 permissions and group membership**|**Permissions outcome**|
|:-----|:-----|:-----|:-----|
|Lync Server 2013 administrator  <br/> |Must be granted membership of sysadmins SQL Server security group and member of the SQL Server local Administrators group  <br/> |Must be a member of the RTCUniversalServerAdmins group  <br/> |Lync Server 2013 administrator has the proper permissions to install both Lync Server 2013 and SQL Server databases.  <br/> |
|SQL Server administrator  <br/> |SQL Server sysadmin group member (or equivalent) and member of the SQL Server local Administrators group  <br/> |Must be a member of the RTCUniversalServerReadOnly group  <br/> |SQL Server administrator has the proper permissions to install both Lync Server 2013 and SQL Server databases.  <br/> |
|Both administrators sharing installation duties  <br/> |SQL Server administrator is member of sysadmins group (or equivalent) and member of the SQL Server local Administrators group  <br/> |Lync Server 2013 administrator is member of RTCUniversalServerAdmins  <br/> |The Lync Server 2013 administrator can install Lync Server 2013, but cannot install the databases. The SQL Server administrator uses the Lync Server Management Shell and Windows PowerShell cmdlets provided by the Lync Server 2013 administrator to install the databases. The Lync Server 2013 Management Shell used by the SQL Server administrator is installed on the Front End Server. This eliminates the need to install the Lync Server 2013 administrative tools on the SQL Server-based server.  <br/> |
   

