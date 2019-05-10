---
title: "Add Archiving Server SQL Server Store"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/8/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddArchivingServerSqlStorePage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 26e0a748-e31d-4c66-b225-b37e0a45408f
description: "Archiving Server requires a supported 64-bit edition of the SQL Server database software to store the archive data. You can either select a previously defined SQL Server database to be used for archiving or define a new SQL Server database by specifying a fully qualified domain name (FQDN) of the server on which the SQL Server database will reside, and the instance of SQL Server that you want to use for the new SQL Server database (which can be the default instance or a named instance that you specify)."
---

# Add Archiving Server SQL Server Store

Archiving Server requires a supported 64-bit edition of the SQL Server database software to store the archive data. You can either select a previously defined SQL Server database to be used for archiving or define a new SQL Server database by specifying a fully qualified domain name (FQDN) of the server on which the SQL Server database will reside, and the instance of SQL Server that you want to use for the new SQL Server database (which can be the default instance or a named instance that you specify).

> [!NOTE]
> If the account that is used to publish the topology has the appropriate user rights and permissions, you can create the archiving database (LcsLog) when you publish your topology. You can also create the database later, as part of the installation procedure, or otherwise.

> [!NOTE]
> To install and deploy the databases on the SQL Server-based server for archiving, you must be a member of the SQL Server sysadmins group for the SQL Server-based server where you are installing the database files. If you are not a member of the SQL Server sysadmins group, you must request to be added to the group until the database files are deployed. If you cannot be made a member of the sysadmins group, you should provide your SQL Server database administrator with the script to configure and deploy the databases. For details about the user rights and permissions that you need to accomplish the procedures, see [Deployment Permissions for SQL Server](https://technet.microsoft.com/library/56ea0c02-bcf5-4d45-aa13-570531c29074.aspx) in the Deployment documentation.


