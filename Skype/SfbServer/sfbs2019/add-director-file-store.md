---
title: "Add Director File Store"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.AddDirectorFileStorePage
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a15b69e0-d3d1-4648-af25-1c0f25e5da8e
description: "You must specify a file share to be used as the file store for Directors. You can use an existing file share for the file store, or you can specify a new file share by specifying the fully qualified domain name (FQDN) of the file server on which the file share is to be located and a folder name for the new file share."
---

# Add Director File Store
[]
You must specify a file share to be used as the file store for Directors. You can use an existing file share for the file store, or you can specify a new file share by specifying the fully qualified domain name (FQDN) of the file server on which the file share is to be located and a folder name for the new file share.
  
> [!IMPORTANT]
> When you add Directors to a topology, topology publication requires appropriate access to set up the file store and configure discretionary access control lists (DACLs) on the file share to be used for the file store. This requires that, when you run Topology Builder and publish the new topology, you are logged on with an account that has full control permissions (read/write/modify) for the file share. 
  
For details about storage support for Lync Server 2013 file shares, see [File storage support in Lync Server 2013](file-storage-support.md) in the Supportability documentation and [SQL Server data and log file placement for Lync Server 2013](sql-server-data-and-log-file-placement.md) in the Deployment documentation. For details about collocation of the file share, see [Supported server collocation in Lync Server 2013](supported-server-collocation.md) in the Supportability documentation. For details about designing the topology for Directors, see [Define optional Director topologies in your topology for Lync Server 2013](define-optional-director-topologies-in-your-topology.md) in the Deployment documentation. 
  

