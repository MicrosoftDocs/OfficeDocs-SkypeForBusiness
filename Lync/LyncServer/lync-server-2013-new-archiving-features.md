---
title: 'Lync Server 2013: New Archiving features'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: New Archiving features
ms:assetid: c002e367-41ad-498d-9d23-8b117ac435b2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205225(v=OCS.15)
ms:contentKeyID: 48185288
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New Archiving features in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

Archiving in Lync Server 2013 can archive the following types of content:

  - Peer-to-peer instant messages

  - Conferences (meetings) that are multi-party instant messages

  - Conference content, including uploaded content (for example, handouts) and event-related content (for example, joining, leaving, uploading sharing, and changes in visibility)

Additionally, Archiving in Lync Server 2013 provides new features that improve deployment and operations efficiency. These new features consist of:

  - **Collocation of Archiving on Front End Servers.**   Lync Server 2013 does not have a separate Archiving Server role. Archiving is an optional feature available on all Front End Servers in an Enterprise Edition deployment, and on Standard Edition servers, that can be implemented configured for a pool or a site.

  - **Microsoft Exchange integration.**   When you deploy Archiving, you can integrate data storage for Archiving with your existing Exchange 2013 storage for all users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold, so you don’t need to deploy separate SQL Server databases to archive Lync data. If you do not have an Exchange 2013 deployment, or if you prefer not to integrate with it, or if you have any Lync 2013 users who are not homed on Exchange 2013 with their mailboxes put on In-Place Hold, you can deploy separate Archiving databases by using SQL Server to store archived data from Lync communications. You can use both Microsoft Exchange integration and Lync Server 2013 Archiving databases if you want to use Microsoft Exchange integration for some but not all users in your deployment. For details about In-Place Hold, see “In-Place Hold” at [http://go.microsoft.com/fwlink/p/?LinkId=267500](http://go.microsoft.com/fwlink/p/?linkid=267500).

  - **SQL Store Mirroring.**   When you deploy Archiving, you can enable SQL Server database mirroring for your Archiving database.

  - **Archiving of Whiteboards and Polls.**   Archived conference content now includes whiteboards and polls that are shared during the meeting.

The following types of content are not archived:

  - Peer-to-peer file transfers

  - Audio/video for peer-to-peer instant messages and conferences

  - Application sharing for peer-to-peer instant messages and conferences

<div>

## See Also


[Planning for Archiving in Lync Server 2013](lync-server-2013-planning-for-archiving.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

