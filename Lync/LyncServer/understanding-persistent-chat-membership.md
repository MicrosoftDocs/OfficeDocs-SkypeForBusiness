---
title: Understanding Persistent Chat membership
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Understanding Persistent Chat membership
ms:assetid: 900392d6-6e9f-4dae-93d6-39d7474409ef
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398730(v=OCS.15)
ms:contentKeyID: 48184781
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Understanding Persistent Chat membership

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

User access to Persistent Chat rooms is managed by membership; users must be members of a chat room to be able to post and read messages. Only **Presenters** who have a designated affiliation with chat rooms are allowed to use **Posting to Auditorium rooms**. An auditorium is a type of chat room (the other is **Normal**), where only Presenters can post and everyone can read.

In addition, Persistent Chat rooms operate under the rules of a category. For details about categories, see [Managing categories, rooms, and add-ins in Lync Server 2013](lync-server-2013-managing-categories-rooms-and-add-ins.md), and also the sections "How Category Scoping Works" and "Room Category Strategies" later in this topic.

A Persistent Chat administrator can create and manage chat room categories. As part of creating and managing chat room categories, the Persistent Chat administrator can configure principals (Active Directory Domain Services groups, containers, and users) that have access to be members or creators of chat rooms of a particular category.

<div>

## Active Directory Domain Services and Persistent Chat

Persistent Chat Server relies on Active Directory for the pool of internal Persistent Chat users. After you install Persistent Chat (client), you can add domains of users and user groups to the room category. You can then add these users and groups to the membership of your room categories.

<div>


> [!IMPORTANT]  
> You must ensure that there are no duplicate names for users who want to make changes to their Persistent Chat room(s). If duplicate user names exist, change them to different names to unblock users from making those changes. If a user has duplicate names in Active Directory and tries to make changes in their room(s), an error message appears prompting the user to contact the administrator for resolution.



</div>

</div>

<div>

## How Category Scoping Works

A category specifies all the users and groups that can be members in a membership list of a Persistent Chat room in that category, based on its **AllowedMembers** property. For example, if you set the category’s **AllowedMembers** to contoso.com, you can add any group or user at *Contoso* as a member to chat rooms in that category. If you set the **AllowedMembers** on a category to *Sales*, only groups and users in this distribution list can be added as members to chat rooms in that category. Similarly, the **Creators** property enables you to control who can create chat rooms in that category. After the chat room is created, anyone from the **AllowedMembers** group can be designated as a **Manager** for ongoing management operations on the rooms (for example, membership changes and approvals).

Defining **AllowedMembers** and **Creators** for a category has the following benefits:

  - All chat rooms in this category are bound by the restrictions set at the category level. You can use this to segregate chat rooms based on business need and access policies.

  - A user who is in the **Creators** list can create new chat rooms in that category. If you want to implement a system where a restricted number of personnel in the organization can create chat rooms, this control can be used to meet that requirement.

</div>

<div>

## Room Category Strategies

A category’s **AllowedMembers** must include all users who will use any Persistent Chat room in this category. Depending on your requirements to protect business data and ensure the appropriate level of access, you may want to define one or more categories to specify who can search and participate in rooms. If you want to allow only a particular set of users (a central helpdesk, or only full-time employees) to create rooms, you can scope the **Creators** of a category to satisfy that requirement.

Categories can also be used to create ethical walls. Ethical walls prevent any conflict of interest in an organization. For example, an administrator can create chat rooms in a category for traders only, whereas chat rooms in another category can be used by analysts only.

<div>


> [!NOTE]  
> In Lync Server 2013, Persistent Chat Server, we do not support access to federated users. If there are chats from federated users in previous versions of Persistent Chat Server, they will be migrated. The federated users are added as disabled principals.



</div>

</div>

<div>

## Narrowing the Members to User Groups

When you add a domain to a category, the user groups whose group objects are contained in that domain are available to you so that you can specify them as members of rooms in that category.

We recommend, as a general rule, that you use Active Directory containers, such as domains and organizational units, for defining a category’s **AllowedMembers** and **Creators**. You can add objects from any domain to an **AllowedMembers** or **Creators** list. Only objects within the **AllowedMembers** or **Creators** list can be added to rooms under that category.

</div>

</div>

<span> </span>

</div>

</div>

</div>

