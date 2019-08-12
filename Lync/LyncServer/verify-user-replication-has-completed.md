---
title: Verify user replication has completed
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Verify user replication has completed
ms:assetid: 119e9896-45e5-4f8b-af43-7b09360ada0b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204680(v=OCS.15)
ms:contentKeyID: 48183441
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Verify user replication has completed

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-17_

When running the **Move-CsUser** cmdlet, you may experience a failure because user information between Active Directory Domain Services (AD DS) and the Lync Server 2013 databases are out of sync because the initial replication is incomplete. The time it takes for the successful completion of the Lync Server 2013 User Replicator service's initial synchronization depends on the number of domain controllers that are hosted in the Active Directory forest that hosts the Lync Server 2013 pool. The Lync Server 2013 User Replicator service initial synchronization process occurs when the Lync Server 2013 Front End Server is started for the first time. After that, the synchronization is then based on the User Replicator interval. Complete the following steps to verify user replication has completed before running the **Move-CsUser** cmdlet.

<div>

## To verify user replication has completed

1.  Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.

2.  Click the **Start** menu, and then click **Run**.

3.  Enter **eventvwr.exe** and then click **OK**.

4.  In Event Viewer, click **Applications and Services logs** to expand it, and then select Lync Server.

5.  In the **Actions** pane click **Filter Current Log**.

6.  From the **Event sources** list, click **LS User Replicator**.

7.  In **\<All Event IDs\>** enter **30024** and then click **OK**.

8.  In the filtered events list, on the **General** tab, look for an entry that states user replication has completed successfully.

</div>

</div>

<span> </span>

</div>

</div>

</div>

