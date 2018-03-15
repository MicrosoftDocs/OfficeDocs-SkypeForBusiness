---
title: "New Archiving features in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c002e367-41ad-498d-9d23-8b117ac435b2
description: "Archiving in Lync Server 2013 can archive the following types of content:"
---

# New Archiving features in Lync Server 2013
[]
Archiving in Lync Server 2013 can archive the following types of content:
  
- Peer-to-peer instant messages
    
- Conferences (meetings) that are multi-party instant messages
    
- Conference content, including uploaded content (for example, handouts) and event-related content (for example, joining, leaving, uploading sharing, and changes in visibility)
    
Additionally, Archiving in Lync Server 2013 provides new features that improve deployment and operations efficiency. These new features consist of:
  
- **Collocation of Archiving on Front End Servers.** Lync Server 2013 does not have a separate Archiving Server role. Archiving is an optional feature available on all Front End Servers in an Enterprise Edition deployment, and on Standard Edition servers, that can be implemented configured for a pool or a site. 
    
- **Microsoft Exchange integration.** When you deploy Archiving, you can integrate data storage for Archiving with your existing Exchange 2013 storage for all users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold, so you don't need to deploy separate SQL Server databases to archive Lync data. If you do not have an Exchange 2013 deployment, or if you prefer not to integrate with it, or if you have any Lync 2013 users who are not homed on Exchange 2013 with their mailboxes put on In-Place Hold, you can deploy separate Archiving databases by using SQL Server to store archived data from Lync communications. You can use both Microsoft Exchange integration and Lync Server 2013 Archiving databases if you want to use Microsoft Exchange integration for some but not all users in your deployment. For details about In-Place Hold, see "In-Place Hold" at [https://go.microsoft.com/fwlink/p/?LinkId=267500](https://go.microsoft.com/fwlink/p/?LinkId=267500).
    
- **SQL Store Mirroring.** When you deploy Archiving, you can enable SQL Server database mirroring for your Archiving database. 
    
- **Archiving of Whiteboards and Polls.** Archived conference content now includes whiteboards and polls that are shared during the meeting. 
    
The following types of content are not archived:
  
- Peer-to-peer file transfers
    
- Audio/video for peer-to-peer instant messages and conferences
    
- Application sharing for peer-to-peer instant messages and conferences
    
## See also

#### 

[Planning for Archiving in Lync Server 2013](planning-for-archiving.md)

