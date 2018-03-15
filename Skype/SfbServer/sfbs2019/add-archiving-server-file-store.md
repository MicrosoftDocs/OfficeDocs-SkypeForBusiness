---
title: "Add Archiving Server File Store"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.AddArchivingServerFileStorePage
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e95f938e-4dd2-48b8-95a3-05b4c63d4810
description: "To enable the archiving of both instant messaging (IM) and web conferencing (meeting) content, you must specify a file share to be used as the file store for copies of all web conferencing content. You can use an existing file share for the archiving file store, or you can specify a new file share by specifying the fully qualified domain name (FQDN) of the file server on which the file share is to be located and a folder name for the new file share."
---

# Add Archiving Server File Store
[]
To enable the archiving of both instant messaging (IM) and web conferencing (meeting) content, you must specify a file share to be used as the file store for copies of all web conferencing content. You can use an existing file share for the archiving file store, or you can specify a new file share by specifying the fully qualified domain name (FQDN) of the file server on which the file share is to be located and a folder name for the new file share.
  
> [!IMPORTANT]
> You can define the file share in Topology Builder before you create the file share, but you must create the file share in the defined location before you publish the topology. > When you add an Archiving Server to your topology, Topology Builder must be able to set up the Archiving file store and configure discretionary access control lists (DACLs) on the file share to be used for the file store. This requires that, when you run Topology Builder to publish the new topology, you are logged on with an account that has full control permissions (read/write/modify) for the file share. 
  
For details about storage support for Lync Server 2013 file shares, see [File storage support in Lync Server 2013](file-storage-support.md) in the Supportability documentation and [SQL Server data and log file placement for Lync Server 2013](sql-server-data-and-log-file-placement.md) in the Deployment documentation. For details about collocation of the file share, see [Supported server collocation in Lync Server 2013](supported-server-collocation.md) in the Supportability documentation. 
  

