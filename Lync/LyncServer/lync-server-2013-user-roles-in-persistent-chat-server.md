---
title: 'Lync Server 2013: User roles in Persistent Chat Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: User roles in Persistent Chat Server
ms:assetid: 343a0563-9ca5-4ad0-b4f3-a72f1d7f1a81
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ676774(v=OCS.15)
ms:contentKeyID: 49361095
ms.date: 03/19/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# User roles in Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-19_

Persistent Chat Server provides the concept of Allowed/Denied members, which applies to Persistent Chat categories and controls who can access rooms in a particular category.

<div>


> [!IMPORTANT]  
> Allowed/Denied members in a Category is not the same as a <STRONG>Member</STRONG> role, which applies to a Persistent Chat room.<BR>Searches display all open and closed chat rooms for which the user performing the search is in the Allowed/Denied member list. Secret rooms are not displayed unless the user who performs the search is a member of the secret room. The user can search only for rooms that he or she is already a member of, or those for which they can request membership.



</div>

The primary rationale for the concept of Allowed/Denied Members is ethical walls. For example, it is common in banking and financial institutions to have ethical boundaries that prevent traders and analysts from sharing communications while implementing policies and conventions. To address this requirement, an administrator can create categories so that one category allows rooms to be created and used by traders, and another category allows rooms to be created and used by analysts. With this constraint is designed into the system prohibits adding a user as a member of the room if the parent category prevents it.

Following are the four user roles Persistent Chat Server:

  - **Creator:** Users who have permissions to create chat rooms. These users are in the Creators list of certain categories: they can create chat rooms in that category, and they can also assign membership according to the category, and assign managers to manage the chat room. The user who creates a chat room is automatically added as a manager of the room.
    
    <div>
    

    > [!NOTE]  
    > Being a Creator simply provides rights for creating chat rooms. It is the automatic promotion to Manager that enables the Creator to further refine memberships, managers, and so on, on the created chat services.

    
    </div>
    
    This role exists to give you the option of controlling who creates chat rooms in your organization, particularly if you want to centrally manage creating chat rooms to enforce policies and conventions, and subsequently delegate the chat room management to other users in the organization.

  - **Manager:** Users who manage properties of a chat room. Chat room managers can modify the member list (add and remove members), and modify the chat room managers list (add and remove managers). Chat room managers can add themselves to the members or presenters list (for auditorium rooms) so they can participate in the chat room. Chat room managers can also disable chat rooms (administrators can query for disabled chat rooms and can permanently delete them). Managers can change all the properties of a chat room, except the category of the chat room. Only the Persistent Chat Administrator can change the category after the chat room has been created.
    
    <div>
    

    > [!IMPORTANT]  
    > If the manager is also a Creator in another category, he or she can change the category to one where they are authorized to create rooms.

    
    </div>

  - **Member:** Users who are members of a chat room. These users can see the chat rooms in the directory (even if the chat room is secret), as well as subscribe to the chat room (including metadata options such as unread messages, ego filters, and keyword filters), and participate in the chat room (can post, unless the room is an auditorium room where only presenters can post, get content, and search). Users who aren’t members of the chat room can search for the chat room if they are in the Allowed Members list of the category, but need to request access to join these chat rooms to access content. (There is no request access or approvals built into the system; these are done externally by email, phone, or other forms of contact.)

  - **Presenter:** Users who can post to an auditorium room.

<div>


> [!NOTE]  
> Persistent Chat Server lets users create and manage chat room for a specific site. Users cannot, however, create or manage chat rooms on other sites within the same topology. Be sure to specify chat room Creators and Managers for all the sites in your organization.



</div>

The following roles are administrator roles for Persistent Chat Server:

  - **Persistent Chat Administrator (CsPersistentChatAdministrator):** This is a new Role-Based Access Control (RBAC) role to administer and manage Persistent Chat Server. Users or security groups designated as CsPersistentChatAdministrator are able administer Persistent Chat Server by using Windows PowerShell cmdlets remotely (that is, from a computer other than the Persistent Chat Server). Persistent Chat Server checks that the Persistent Chat Administrator is member of the RTC Local administrator local group on the Persistent Chat Server Front End Server.
    
    The CsPersistentChatAdministrator role can manage chat rooms (modify all properties including membership, managers, categories, mark rooms as disabled), as well as create and manage chat room categories that define who can create and access chat rooms. Administrators can also mark chat rooms as disabled and clean up chat rooms that are no longer active. Administrators are not subject to the Creators or Allowed Members restrictions. Administrators can create any kind of chat room and add themselves as a member to any chat room. Administrators can also modify and manage Persistent Chat configuration (pool properties, global settings, and compliance configuration) and can also plan and implement migration from an older Group Chat Server deployment to Lync Server 2013 Persistent Chat Server.

  - **Lync Administrator:** Overall enterprise administrator for Lync Server 2013 responsible for deployment.

  - **Operations Manager:** User responsible for managing day-to-day operations.

  - **Third-party developers and partners:** Third-party developers extend the system, in particular providing an ethical wall solution for group conversations, compliance support and tools, web/mobile clients, and a framework for Bot development.

</div>

<span> </span>

</div>

</div>

</div>

