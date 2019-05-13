---
title: Standard migration scenario - high-level
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Standard migration scenario - high-level
ms:assetid: e768a7ca-44e3-4969-a6d9-7ed3e7029c5c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205354(v=OCS.15)
ms:contentKeyID: 48185709
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Standard migration scenario - high-level

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

Use the following items as a starting point when migrating Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server. The standard Lync Server 2013 migration path is as follows:

  - Your organization has previously deployed Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat, and you want to deploy Lync Server 2013, Persistent Chat Server.

  - Deploy Lync Server 2013, and then deploy Persistent Chat Server pool(s).

  - Prepare and plan for migration of your Persistent Chat rooms, and determine an appropriate time to shut down the system for migration.

  - Run the Windows PowerShell cmdlets for migration (**Export-CsPersistentChatData** and **Import-CsPersistentChatData**) to move content to Persistent Chat Server.

  - Verify that migration has succeeded.

  - Decommission your legacy deployment.

  - Configure Persistent Chat Server so that legacy clients can connect to Lync Server 2013, Persistent Chat Server. This is necessary because it takes time to deploy new clients, and you want to enable existing users with legacy clients to have access to their chat rooms as soon as possible.

  - Deploy new clients, while continuing to help ensure that workers with legacy Group Chat (clients) can get to their chat rooms.

</div>

<span> </span>

</div>

</div>

</div>

