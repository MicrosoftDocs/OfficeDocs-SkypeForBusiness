---
title: 'Lync Server 2013: Restoring Persistent Chat data'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Restoring Persistent Chat data
ms:assetid: c251a7fa-50da-434b-b39a-17f5978ce736
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945649(v=OCS.15)
ms:contentKeyID: 51541516
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Restoring Persistent Chat data in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-18_

Persistent Chat room content is stored in the Persistent Chat database (mgc.mdf). This is business-critical data that should be backed up regularly. In addition to the chat room content, principals (such as users and groups) and the roles and access that they have to chat rooms and chat room content, is also stored in the Persistent Chat database.

How you restore your Persistent Chat data depends on the method that you used to back it up.

  - If you used SQL Server backup procedures, you must use SQL Server restore procedures.

  - If you used the **Export-CsPersistentChatData** cmdlet to back up Persistent Chat data, then you must use the **Import-CsPersistentChatData** cmdlet to restore the data.

</div>

<span> </span>

</div>

</div>

</div>

