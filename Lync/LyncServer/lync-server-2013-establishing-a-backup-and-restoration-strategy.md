---
title: 'Lync Server 2013: Establishing a backup and restoration strategy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Establishing a backup and restoration strategy
ms:assetid: f545a75f-bbc4-4968-b510-8f6f3920112b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202195(v=OCS.15)
ms:contentKeyID: 51541532
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Establishing a backup and restoration strategy for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-26_

Before you can develop a backup and restoration plan for Lync Server, you need to develop a strategy that fits with your organization's goals. To develop an effective backup and restoration strategy, you will need to:

  - Establish business priorities.

  - Identify backup and restoration requirements.

<div>

## Establishing Business Priorities

Evaluate the business priorities of your organization. Typically, the primary business priorities that affect your backup and restoration strategy are the following:

  - Business continuity requirements

  - Data completeness

  - Data criticality

  - Portability requirements

  - Cost constraints

Business needs such as these help to determine the service level agreements (SLAs) that you develop with your customers. Service level agreements greatly influence your backup and recovery strategy.

</div>

<div>

## Identifying Backup and Restoration Requirements

Your business priorities and service level agreements act in determining your organizations' requirements for backing up and restoring Lync Server. Identify and document your requirements for the following:

  - **Frequency of backups**   For details about best practices for backup frequency, see [Best practices for backup and restoration for Lync Server 2013](lync-server-2013-best-practices-for-backup-and-restoration.md).

  - **Backup and restoration tools**   Include who is to use the tools, and on which computers. For details about the tools discussed in this topic and necessary permissions, see [Backup and restoration requirements in Lync Server 2013: tools and permissions](lync-server-2013-backup-and-restoration-requirements-tools-and-permissions.md).

  - **Backup location**   Identify whether the backups are kept locally or remotely, taking security and accessibility into consideration. Specify the media to be used for the backups.

  - **Hardware and software requirements**   Identify and document your specific hardware and software requirements, including the hardware for backup storage and restoration of specific components and any software and network connectivity required to support backup and restoration. As you develop your hardware and software requirements, keep in mind the various restoration scenarios that follow.

  - **Restoration scenarios**   Here are the restoration processes for the following scenarios:
    
      - A Lync Server pool fails. This scenario requires rebuilding each server in the pool.
    
      - A Standard Edition server fails. This scenario requires rebuilding the server on a new or clean computer and restoring databases.
    
      - Loss of the Central Management store. At a minimum, this scenario requires restoring and publishing the Central Management store.
    
      - Loss of a Back End Server when the Central Management store is still functioning normally. This scenario requires rebuilding the server on a new or clean computer and restoring databases.
    
      - A server that is a member of a Lync Server pool fails. This scenario requires rebuilding the server on a new or clean computer.
    
      - A File Store fails. This scenario requires restoring the file server or file cluster.
    
      - An Archiving, Monitoring, or Persistent Chat database fails. This scenario requires recreating the databases, and, if the data is critical to your organization, restoring the data. Archiving, Monitoring, and Persistent Chat data is not required to get Lync Server back up and running.

</div>

</div>

<span> </span>

</div>

</div>

</div>

