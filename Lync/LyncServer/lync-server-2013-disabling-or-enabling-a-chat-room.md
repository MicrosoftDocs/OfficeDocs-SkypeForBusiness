---
title: 'Lync Server 2013: Disabling or enabling a chat room'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Disabling or enabling a chat room
ms:assetid: db0908fc-aae3-46e8-bc0b-245e9adfa1e2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ215883(v=OCS.15)
ms:contentKeyID: 48706011
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Disabling or enabling a chat room in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

If the topic of a Persistent Chat room is no longer relevant, you can make the chat room unavailable to users by disabling it. When a chat room is disabled, all members are immediately disconnected from the room. After a chat room is disabled, users cannot rejoin it or find it in chat room searches.

A disabled chat room can be enabled later by a Persistent Chat administrator. If a chat room is disabled, its membership list and other settings are preserved. If you enable the room again, you do not need to manually re-create the settings.

If the chat room’s history persists (chat room history persistence is an optional setting on a category that applies to all rooms within the category; the default is that it is persisted, but can be turned off by setting the category’s **Enable Chat History** to false), the content is preserved when the chat room is disabled. However, that content will not appear in searches during the time that the chat room remains in a disabled state. If you later enable the chat room, users can search for messages that were posted before the chat room was disabled.

For details about disabling and enabling chat rooms by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md). To disable a chat room, use a command similar to this:

    Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $True

To enabled a chat room, set the Disabled property to False:

    Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $False

Note that chat rooms cannot be enabled or disabled by using the Lync Server Control Panel.

For details about configuring chat rooms, see [Configure rooms in Lync Server 2013](lync-server-2013-configure-rooms.md) in the Deployment documentation.

</div>

<span> </span>

</div>

</div>

</div>

