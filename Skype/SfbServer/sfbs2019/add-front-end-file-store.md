---
title: "Add Front End File Store"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.AddFrontEndFileStorePage
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4d18a648-a0e1-4401-a1e6-7a2755ba8c66
description: "You must specify a file share to be used as the file store for the Standard Edition server or Enterprise Edition Front End pool. You can use an existing file share for the file store, or you can specify a new file share by specifying the fully qualified domain name (FQDN) of the file server on which the file share is to be located and a folder name for the new file share."
---

# Add Front End File Store
[]
You must specify a file share to be used as the file store for the Standard Edition server or Enterprise Edition Front End pool. You can use an existing file share for the file store, or you can specify a new file share by specifying the fully qualified domain name (FQDN) of the file server on which the file share is to be located and a folder name for the new file share.
  
> [!IMPORTANT]
> The file share for Lync Server 2013 cannot be located on the Enterprise Edition Front End Server, but can be located on a Standard Edition server. > You can define the file share in Topology Builder before you create the file share, but you must create the file share in the defined location you define before you publish the topology. > When you add an Enterprise Front End pool or Standard Edition server to your topology, Topology Builder must be able to set up the file store and configure discretionary access control lists (DACLs) on the file share to be used for the file store. This requires that, when you run Topology Builder to publish the new topology, you are logged on with an account that has full control permissions (read/write/modify) for the file share. 
  
For details about storage support for Lync Server 2013 file shares, see [File storage support in Lync Server 2013](file-storage-support.md) in the Supportability documentation and [SQL Server data and log file placement for Lync Server 2013](sql-server-data-and-log-file-placement.md) in the Deployment documentation. For details about collocation of the file share, see [Supported server collocation in Lync Server 2013](supported-server-collocation.md) in the Supportability documentation. For details about designing the topology for an Enterprise Edition Front End pool, see [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](define-and-configure-a-front-end-pool-or-standard-edition-server.md) in the Deployment documentation. 
  

