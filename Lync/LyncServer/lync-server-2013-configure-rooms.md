---
title: 'Lync Server 2013: Configure rooms'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure rooms
ms:assetid: 8956bd2c-c863-4704-bc65-5c0d83556258
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205067(v=OCS.15)
ms:contentKeyID: 48184750
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure rooms in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

Configuring Persistent Chat rooms is commonly handled by users or other central teams by using Windows PowerShell command-line interface; an administrator typically does not manage chat rooms. However, if you have to create and manage chat rooms, you can use the Windows PowerShell command-line interface, or add yourself as a member to a chat room and use the Lync 2013 client.

For details about configuring chat rooms by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).

<div>

## Managing Data in Chat Rooms

Persistent Chat Server lets users collaborate by posting messages into Persistent Chat rooms. The data is persisted on the server, and members of the room can have access to the data, including historical data. However, users with different roles have different access to the persisted data, as outlined in the following list.

  - Administrators can delete earlier content (for example, content that was posted before a certain date) from any chat room to keep the database from growing too large. Or, they can remove or replace messages that are considered inappropriate for a particular chat room.

  - End users, including message authors, cannot delete content from any chat room.

  - Chat room managers can disable rooms, but cannot delete rooms. Only administrators can delete a chat room after it has been created.

When a message is deleted, you cannot undo the action. However, deleted messages can be restored if there is a backup. If a Persistent Chat Compliance server is enabled, old messages are persisted in the compliance database.

<div>


> [!NOTE]  
> This chat room data usage applies to the Lync Server 2013, Persistent Chat Server API application, except for the case when the administrator role is involved. The Persistent Chat Server API cannot be used to do any of the administrator’s operations. You must perform these operations in the Lync Server Management Shell.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

