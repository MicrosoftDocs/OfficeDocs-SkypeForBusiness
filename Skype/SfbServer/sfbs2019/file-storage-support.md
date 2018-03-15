---
title: "File storage support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ed66430d-3c19-4267-938c-956a51005073
description: "Lync Server 2013 uses the same file store for all file storage. File storage support includes the following:"
---

# File storage support in Lync Server 2013
[]
Lync Server 2013 uses the same file store for all file storage. File storage support includes the following: 
  
- A file share on either direct attached storage (DAS) or a storage area network (SAN), including Distributed File System (DFS), and on a redundant array of independent disks (RAID) for file stores. For details about storage requirements, see [Technical requirements for Front End Servers, instant messaging, and presence in Lync Server 2013](technical-requirements-for-front-end-servers-instant-messaging-and-presence.md) and [Hardware and software requirements for the Director in Lync Server 2013](hardware-and-software-requirements-for-the-director.md) in the Planning documentation. For details about DFS for Windows Server 2008 operating system, see the DFS Step-by-Step Guide for Windows Server 2008 at [https://go.microsoft.com/fwlink/p/?linkId=202835](https://go.microsoft.com/fwlink/p/?linkId=202835).
    
- A shared cluster for the file share. If you use a shared cluster, you should use cluster servers running Windows Server 2008 or Windows Server 2008 R2. Using cluster servers running an older version of Windows may result in permission issues that prevent some features from being available. Use the Cluster Administrator to create the file shares. For details about using the Cluster Administrator, see Microsoft Knowledge Base article 284838, "How to Create a Server Cluster File Share with Cluster.exe" at [https://go.microsoft.com/fwlink/p/?linkId=140899](https://go.microsoft.com/fwlink/p/?linkId=140899).
    

