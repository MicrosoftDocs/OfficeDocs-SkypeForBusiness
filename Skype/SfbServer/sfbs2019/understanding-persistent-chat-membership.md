---
title: "Understanding Persistent Chat membership"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 900392d6-6e9f-4dae-93d6-39d7474409ef
description: "In this articleActive Directory Domain Services and Persistent ChatHow Category Scoping WorksRoom Category StrategiesNarrowing the Members to User Groups"
---

# Understanding Persistent Chat membership
[]
 **In this article**
  
[Active Directory Domain Services and Persistent Chat](#sectionSection0)
  
[How Category Scoping Works](#sectionSection1)
  
[Room Category Strategies](#sectionSection2)
  
[Narrowing the Members to User Groups](#sectionSection3)
  
User access to Persistent Chat rooms is managed by membership; users must be members of a chat room to be able to post and read messages. Only **Presenters** who have a designated affiliation with chat rooms are allowed to use **Posting to Auditorium rooms**. An auditorium is a type of chat room (the other is **Normal**), where only Presenters can post and everyone can read.
  
In addition, Persistent Chat rooms operate under the rules of a category. For details about categories, see [Managing categories, rooms, and add-ins in Lync Server 2013](managing-categories-rooms-and-add-ins.md), and also the sections "How Category Scoping Works" and "Room Category Strategies" later in this topic.
  
A Persistent Chat administrator can create and manage chat room categories. As part of creating and managing chat room categories, the Persistent Chat administrator can configure principals (Active Directory Domain Services groups, containers, and users) that have access to be members or creators of chat rooms of a particular category.
  
## Active Directory Domain Services and Persistent Chat
<a name="sectionSection0"> </a>

Persistent Chat Server relies on Active Directory for the pool of internal Persistent Chat users. After you install Persistent Chat (client), you can add domains of users and user groups to the room category. You can then add these users and groups to the membership of your room categories.
  
> [!IMPORTANT]
> You must ensure that there are no duplicate names for users who want to make changes to their Persistent Chat room(s). If duplicate user names exist, change them to different names to unblock users from making those changes. If a user has duplicate names in Active Directory and tries to make changes in their room(s), an error message appears prompting the user to contact the administrator for resolution. 
  
## How Category Scoping Works
<a name="sectionSection1"> </a>

A category specifies all the users and groups that can be members in a membership list of a Persistent Chat room in that category, based on its **AllowedMembers** property. For example, if you set the category's **AllowedMembers** to contoso.com, you can add any group or user at Contoso as a member to chat rooms in that category. If you set the **AllowedMembers** on a category to Sales, only groups and users in this distribution list can be added as members to chat rooms in that category. Similarly, the **Creators** property enables you to control who can create chat rooms in that category. After the chat room is created, anyone from the **AllowedMembers** group can be designated as a **Manager** for ongoing management operations on the rooms (for example, membership changes and approvals). 
  
Defining **AllowedMembers** and **Creators** for a category has the following benefits: 
  
- All chat rooms in this category are bound by the restrictions set at the category level. You can use this to segregate chat rooms based on business need and access policies.
    
- A user who is in the **Creators** list can create new chat rooms in that category. If you want to implement a system where a restricted number of personnel in the organization can create chat rooms, this control can be used to meet that requirement. 
    
## Room Category Strategies
<a name="sectionSection2"> </a>

A category's **AllowedMembers** must include all users who will use any Persistent Chat room in this category. Depending on your requirements to protect business data and ensure the appropriate level of access, you may want to define one or more categories to specify who can search and participate in rooms. If you want to allow only a particular set of users (a central helpdesk, or only full-time employees) to create rooms, you can scope the **Creators** of a category to satisfy that requirement. 
  
Categories can also be used to create ethical walls. Ethical walls prevent any conflict of interest in an organization. For example, an administrator can create chat rooms in a category for traders only, whereas chat rooms in another category can be used by analysts only.
  
> [!NOTE]
> In Lync Server 2013, Persistent Chat Server, we do not support access to federated users. If there are chats from federated users in previous versions of Persistent Chat Server, they will be migrated. The federated users are added as disabled principals. 
  
## Narrowing the Members to User Groups
<a name="sectionSection3"> </a>

When you add a domain to a category, the user groups whose group objects are contained in that domain are available to you so that you can specify them as members of rooms in that category.
  
We recommend, as a general rule, that you use Active Directory containers, such as domains and organizational units, for defining a category's **AllowedMembers** and **Creators**. You can add objects from any domain to an **AllowedMembers** or **Creators** list. Only objects within the **AllowedMembers** or **Creators** list can be added to rooms under that category. 
  

