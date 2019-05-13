---
title: 'Lync Server 2013: Managing Response Group agent groups'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Managing Response Group agent groups
ms:assetid: 36084cdc-38f1-4c45-922f-f81c7e86210c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520976(v=OCS.15)
ms:contentKeyID: 48183806
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing Response Group agent groups in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

An agent group consists of a group of people who are designated to answer calls to a response group. When you create an agent group, you select the agents who are assigned to the group and specify additional group settings, such as the routing method and whether an agent can sign in to and out of the group.

<div>


> [!NOTE]  
> Users must be enabled for Enterprise Voice before you can add them to agent groups. For details about how to enable a user for Enterprise Voice, see <A href="lync-server-2013-enable-users-for-enterprise-voice.md">Enable users for Enterprise Voice in Lync Server 2013</A>.



</div>

<div>


> [!NOTE]  
> Only on-premises users can be agents. If an agent is moved from on-premises to online, Response Group calls will not be routed to that agent.



</div>

An agent who must sign in and out of the group, which is different from signing in or out of Lync Server, is called a *formal agent*. Formal agents must be signed in to the group before they can receive calls that are routed to the group. This can be useful for agents who answer calls from the group on a part-time basis. Formal agents sign in and out of their groups by clicking a menu item in Lync 2013 to open the Windows Internet Explorer Internet browser and display a webpage console.

An agent who does not sign in or out of the group is called an *informal agent*. Informal agents are automatically signed in to the group when they sign in to Lync Server, and they cannot sign out of the group.

<div>


> [!IMPORTANT]  
> When you assign users as response group agents, inform them that, if they have Privacy mode enabled, they need to search for "RGS Presence Watcher" contacts and add them to their Contacts list. Agents who have Privacy mode enabled, but who do not have "RGS Presence Watcher" in their Contacts list, cannot receive calls to the response group. Agents who do not have Privacy mode enabled are not affected.



</div>

<div>

## In This Section

  - [Create or modify an agent group in Lync Server 2013](lync-server-2013-create-or-modify-an-agent-group.md)

  - [Delete an agent group in Lync Server 2013](lync-server-2013-delete-an-agent-group.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

