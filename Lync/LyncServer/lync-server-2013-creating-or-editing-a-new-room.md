---
title: 'Lync Server 2013: Creating or editing a new room'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Creating or editing a new room
ms:assetid: aa8f4349-cfd9-4036-9c4d-de8fb2c4c8a4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ215880(v=OCS.15)
ms:contentKeyID: 48706008
ms.date: 03/19/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Creating or editing a new room in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-19_

Configuring Persistent Chat rooms is commonly handled by users; a Persistent Chat administrator typically does not configure or manage chat rooms. Windows PowerShell cmdlets to manage rooms are available only to **CsPersistentChatAdministrator** Administrators.

Users who are **Creators** in any given category can use the Lync client to create and manage rooms. Users who have been designated as managers for a specific chat room can also perform ongoing management of the room, such as editing the room properties or membership.

<div>


> [!TIP]  
> Persistent Chat administrators can also be Creators, and they are not subject to the restrictions placed on Creators.



</div>

Optionally, if you are a Persistent Chat administrator, you can employ a user interface to create and manage chat rooms instead of using Windows PowerShell cmdlets. To do this, SIP-enable an administrator for Persistent Chat Server, and then use the Lync client to create and manage chat rooms.

If you want to create a custom room management workflow for your users, you can set the **RoomManagementUrl** property on your Persistent Chat Server configuration to redirect users to your custom solution from the Lync client.

For details about configuring chat rooms by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).

For details about configuring chat rooms, see [Configure rooms in Lync Server 2013](lync-server-2013-configure-rooms.md) in the Deployment documentation.

<div>


> [!NOTE]  
> Persistent Chat Server lets users create and manage chat room for a specific site. Users cannot, however, create or manage chat rooms on other sites within the same topology. Be sure to specify chat room Creators and Managers for all the sites in your organization.



</div>

<div>


> [!NOTE]  
> Users who are homed on a Lync Server Survivable Branch Appliance are unable to create new chat rooms or view the room card for existing rooms.



</div>

</div>

<span> </span>

</div>

</div>

</div>

