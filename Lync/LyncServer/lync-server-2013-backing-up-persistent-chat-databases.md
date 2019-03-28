---
title: 'Lync Server 2013: Backing up Persistent Chat databases'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Backing up Persistent Chat databases
ms:assetid: b99ebdc0-a025-44d7-9d74-37a7365f330d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945646(v=OCS.15)
ms:contentKeyID: 51541507
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Backing up Persistent Chat databases in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-17_

Persistent Chat room content is stored in the Persistent Chat database (Mgc.mdf). This is business-critical data that should be backed up regularly. In addition to the chat room content, the Persistent Chat database also stores information about the principals (such as users and user groups), and the roles and access that they have to chat rooms and chat room.

There are two ways of backing up Persistent Chat data.

  - SQL Server Backup

  - The `Export-CsPersistentChatData` cmdlet, which exports Persistent Chat data as a file

Data that is created by using SQL Server backup requires significantly more disk space—possibly 20 times more—than that created by `Export-CsPersistentChatData`, but SQL Server backup is more likely to be a procedure that administrators are familiar with.

</div>

<span> </span>

</div>

</div>

</div>

