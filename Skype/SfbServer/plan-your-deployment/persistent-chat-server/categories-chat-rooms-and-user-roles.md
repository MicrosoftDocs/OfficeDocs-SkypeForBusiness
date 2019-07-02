---
title: "Persistent chat categories, chat rooms, and user roles in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 8/17/2015
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 343a0563-9ca5-4ad0-b4f3-a72f1d7f1a81
description: "Summary: Read this topic to learn about categories, chat rooms, and user and administrator roles for Persistent Chat Server in Skype for Business Server 2015."
---

# Persistent chat categories, chat rooms, and user roles in Skype for Business Server 2015
 
**Summary:** Read this topic to learn about categories, chat rooms, and user and administrator roles for Persistent Chat Server in Skype for Business Server 2015.
  
You can control access to chat rooms by creating chat room categories, then specifying access to categories and chat rooms within categories. You can also specify various administrator roles. This topic describes: 
  
- Categories for organizing chat rooms
    
- Chat rooms and user roles
    
- Administrator roles

> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Getting started with your Microsoft Teams upgrade](/microsoftteams/upgrade-start-here). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
    
## Categories for organizing chat rooms

Categories let you organize chat rooms and control which users and groups are permitted to create or join the chat rooms within those categories. Each category has associated properties that determine the options available for the chat rooms within the category. You control access to a particular category by specifying whether a user is Allowed or Denied access.
  
The primary rationale for the concept of Allowed and Denied Members is ethical walls. For example, it is common in banking and financial institutions to have ethical boundaries that prevent traders and analysts from sharing communications while implementing policies and conventions. To address this requirement, an administrator can create categories so that one category allows rooms to be created and used by traders, and another category allows rooms to be created and used by analysts. Users cannot be added as a member of a chat room if the parent category prevents it.
  
> [!IMPORTANT]
> Allowed and Denied members in a category are not the same as a **Member** role, which applies to a Persistent Chat room.> Searches display all open and closed chat rooms for which the user performing the search is in the Allowed and Denied member list. Secret rooms are not displayed unless the user who performs the search is a member of the secret room. The user can search only for rooms that he or she is already a member of, or those for which they can request membership. 
  
## Chat rooms and user roles

In addition to Allowed and Denied Members for categories, you can also control access to chat rooms by specifying the following user roles: Creator, Manager, Member, and Presenter.
  
- **Creator**: Users who have permission to create chat rooms. These users are in the Creators list of certain categories: they can create chat rooms in that category, and they can also assign membership according to the category, and assign managers to manage the chat room. The user who creates a chat room is automatically added as a manager of the room.
    
    > [!NOTE]
    > Being a Creator simply provides rights for creating chat rooms. It is the automatic promotion to Manager that enables the Creator to further refine memberships, managers, and so on, on the created chat services. 
  
    This role exists to give you the option of controlling who creates chat rooms in your organization, particularly if you want to centrally manage creating chat rooms to enforce policies and conventions, and subsequently delegate the chat room management to other users in the organization.
    
- **Manager**: Users who manage properties of a chat room. Chat room managers can modify the member list (add and remove members), and modify the chat room managers list (add and remove managers). Chat room managers can add themselves to the members or presenters list (for auditorium rooms) so they can participate in the chat room. Chat room managers can also disable chat rooms (administrators can query for disabled chat rooms and can permanently delete them). Managers can change all the properties of a chat room, except the category of the chat room. Only the Persistent Chat Administrator can change the category after the chat room has been created.
    
    > [!IMPORTANT]
    > If the manager is also a Creator in another category, he or she can change the category to one where they are authorized to create rooms. 
  
- **Member**: Users who are members of a chat room. These users can see the chat rooms in the directory (even if the chat room is secret), as well as subscribe to the chat room (including metadata options such as unread messages, ego filters, and keyword filters), and participate in the chat room (can post, unless the room is an auditorium room where only presenters can post, get content, and search). Users who aren't members of the chat room can search for the chat room if they are in the Allowed Members list of the category, but need to request access to join these chat rooms to access content. (There is no request access or approvals built into the system; these are done externally by email, phone, or other forms of contact.)
    
- **Presenter**: Users who can post to an auditorium room.
    
## Administrator roles

The following are administrator roles for Persistent Chat Server:
  
- **Persistent Chat Administrator**: The Persistent Chat Administrator role can manage chat rooms (modify all properties including membership, managers, categories, mark rooms as disabled), as well as create and manage chat room categories that define who can create and access chat rooms. Administrators can also mark chat rooms as disabled and clean up chat rooms that are no longer active. Administrators are not subject to the Creators or Allowed Members restrictions. Administrators can create any kind of chat room and add themselves as a member to any chat room. Administrators can also modify and manage Persistent Chat configuration (pool properties, global settings, and compliance configuration) and can also plan and implement migration from an older Group Chat Server deployment to Skype for Business Server 2015 Persistent Chat Server.
    
    Persistent Chat Administrators are able to administer Persistent Chat Server by using Windows PowerShell cmdlets remotely (that is, from a computer other than the Persistent Chat Server). Persistent Chat Server checks that the Persistent Chat Administrator is a member of the RTC Local administrator local group on the Persistent Chat Server Front End Server.
    
- **Skype for Business Server 2015 Administrator**: Overall enterprise administrator for Skype for Business Server 2015 responsible for deployment.
    
- **Operations Manager**: User responsible for managing day-to-day operations.
    
- **Third-party developers and partners**: Third-party developers extend the system, in particular providing an ethical wall solution for group conversations, compliance support and tools, web/mobile clients, and a framework for Bot development.
    
## For more information

For more information about configuring and managing chat rooms and user roles, see the following topics:
  
- [Create a Persistent Chat administrator in Skype for Business Server 2015](../../deploy/deploy-persistent-chat-server/create-a-persistent-chat-administrator.md)
    
- [Manage categories in Persistent Chat Server in Skype for Business Server 2015](../../manage/persistent-chat/categories.md)
    
- [Manage chat rooms in Persistent Chat Server in Skype for Business Server 2015](../../manage/persistent-chat/chat-rooms.md)
    

