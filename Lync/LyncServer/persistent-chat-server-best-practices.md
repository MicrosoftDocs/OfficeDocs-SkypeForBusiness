---
title: Persistent Chat Server best practices
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Persistent Chat Server best practices
ms:assetid: dc18e7f7-599b-4d32-abf7-cd9e691426a2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398970(v=OCS.15)
ms:contentKeyID: 48185612
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Persistent Chat Server best practices

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

As you create your categories and Persistent Chat rooms and design your scoping and membership, the following tips can help your planning:

  - If your company does not require an ethical wall, do not narrow the scope in your category tree. Put all your users in the scope of one category, and create all chat rooms in that category. Subsequently, use only membership lists to grant or restrict access to each chat room.

  - In most cases, you should enable users to create new chat rooms so that discussions about new topics can be started any time. Do this by making the **Creators** list the same as the **AllowedMembers** list. However, if you want to allow only a central support team or designated users to create rooms, then make the **Creators** list as the appropriate subset.

  - Give each chat room a complete name and description summary that describes where it fits in with your organization. Because users cannot see the category name when they use the chat room, you cannot rely on the category name to help users determine the intended discussion forum for the chat room.

  - You may want to have a custom room creation workflow if you have certain naming conventions or other access controls or validations to implement. The Persistent Chat configuration enables you to customize the **RoomManagementUrl** to something that you host. For example, when users click **Create a room** in their Lync client, they can be redirected to your custom solution.

  - Create a variety of add-ins that help to enhance the experience of chat rooms by bringing in other business data into chat rooms. Administrators must register the add-ins that they want to allow in the system. Chat room managers and creators can choose from the list of allowed add-ins for the ones most relevant to their respective rooms.

<div>

## See Also


[Managing categories, rooms, and add-ins in Lync Server 2013](lync-server-2013-managing-categories-rooms-and-add-ins.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

