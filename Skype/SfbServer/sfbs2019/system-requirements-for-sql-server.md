---
title: "System requirements for SQL Server in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9c235085-cbfa-4e9e-9cec-3f5749039a6b
description: "Before you deploy Enterprise Edition server, install Microsoft SQL Server 2008 R2 or Microsoft SQL Server 2012 on a dedicated computer that meets the hardware requirements. For details about hardware requirements, see Server hardware platforms for Lync Server 2013 in the Supportability documentation. For details about software requirements, see Database software support in Lync Server 2013 in the Supportability documentation. For information about the permissions necessary for deployment, see Deployment permissions for SQL Server in Lync Server 2013."
---

# System requirements for SQL Server in Lync Server 2013
[]
Before you deploy Enterprise Edition server, install Microsoft SQL Server 2008 R2 or Microsoft SQL Server 2012 on a dedicated computer that meets the hardware requirements. For details about hardware requirements, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md) in the Supportability documentation. For details about software requirements, see [Database software support in Lync Server 2013](database-software-support.md) in the Supportability documentation. For information about the permissions necessary for deployment, see [Deployment permissions for SQL Server in Lync Server 2013](deployment-permissions-for-sql-server.md).
  
Before you create the Front End pool, you must also configure Windows Firewall to allow Lync Server 2013 access to SQL Server over specific ports by defining ports for the server using SQL Server Configuration Manager and opening ports in Windows Firewall with Advanced Security.
  

