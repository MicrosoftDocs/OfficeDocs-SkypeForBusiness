---
title: "Publish Topology Select CMS Page"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.PublishTopologySelectCmsPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: df447066-2840-431b-bc4e-acf8aa692d71
ROBOTS: NOINDEX, NOFOLLOW
description: "You publish the topology that you have configured using Topology Builder. You are asked to select from a list which Front End Server or Front End pool will assume the role of holding the Central Management store. Only one Front End Server or Front End pool can hold this role at any given time."
---

# Publish Topology Select CMS Page
 
You publish the topology that you have configured using Topology Builder. You are asked to select from a list which Front End Server or Front End pool will assume the role of holding the Central Management store. Only one Front End Server or Front End pool can hold this role at any given time. 
  
### About the Central Management Server
The Central Management Server is a single master/multiple replica system, where the read/write copy of the database is held by the Front End Server that contains the Central Management Server. Each computer in the topology, including the Front End Server that contains the Central Management Server, has a read-only copy of the Central Management store data in the SQL Server database (named RTCLOCAL by default) installed on the computer during setup and deployment. The local database receives replica updates by way of the Lync Server Replica Replicator Agent that runs as a service on all computers. The name of the actual database on the Central Management Server and the local replica is XDS, which is made up of the xds.mdf and xds.ldf files. The master database location is referenced by a service control point (SCP) in Active Directory Domain Services. All tools that use the Central Management Server to manage and configure Lync Server use the SCP to locate the Central Management store.
  
## See also

[Move-CsManagementServer](https://docs.microsoft.com/powershell/module/skype/move-csmanagementserver?view=skype-ps)
