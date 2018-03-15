---
title: "Using categories to administer Persistent Chat Server"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dfcb3ad1-da90-467e-b08c-f4e68673b7b5
description: "Your Persistent Chat Server deployment can host many concurrent Persistent Chat rooms. Chat rooms can be organized into a set of categories on the server. Each chat room belongs to one category, and inherits some settings from that category. This organization creates a useful structure for identifying conversations, based on their business purpose, and facilitates delegated administration and simplified management."
---

# Using categories to administer Persistent Chat Server
[]
Your Persistent Chat Server deployment can host many concurrent Persistent Chat rooms. Chat rooms can be organized into a set of categories on the server. Each chat room belongs to one category, and inherits some settings from that category. This organization creates a useful structure for identifying conversations, based on their business purpose, and facilitates delegated administration and simplified management.
  
> [!NOTE]
> Although many of the management features of chat rooms are available in computers running Persistent Chat (Lync client) for the user, Persistent Chat Administrators (in the **cspersistentchatadministrator** role) must use the Lync Server Control Panel or Windows PowerShell cmdlets to create or manage categories. 
  
Persistent Chat administrators use Lync Server Control Panel or Windows PowerShell cmdlets to create and manage categories, and to design access for chat rooms for the users in their organization.
  
Persistent Chat room managers, who have the ability to manage one or more chat rooms, can use the Lync client to launch a room management Web application to create and manage rooms (or customers can create custom solutions and workflows to be invoked). Persistent Chat administrators can also use Lync Server Control Panel or Windows PowerShell cmdlets to create and manage rooms.
  
> [!NOTE]
> A Persistent Chat room cannot have the same name as a Persistent Chat category. 
  
Chat room managers can make changes to all chat room properties, except for changing the category of the room. They cannot be restricted from performing the following actions:
  
- Disabling a chat room
    
- Changing a chat room name
    
- Changing a chat room description
    
- Changing a chat room type (Auditorium versus Normal)
    
- Changing the privacy of a room (open versus closed versus secret)
    
- Adding or removing members
    
- Adding or removing chat room managers
    
- Adding or removing an add-in
    
- Changing settings such as invitations (according to what's permitted by the category)
    
## Delegated Administration

Creating and managing Persistent Chat rooms is much easier with the correct use of categories. A Persistent Chat Administrator can define **AllowedMembers** and **Creators** for each category, and can also define the default chat room settings and behaviors that will be applied to all chat rooms created in the category. Persistent Chat administrators create and manage categories by using Lync Server Control Panel or Windows PowerShell cmdlets. 
  
Users, Organizational Units (OUs), and user groups that are identified as Creators of the category are the only individuals and groups that are allowed to create rooms in the category. After the category is created, they can choose users, OUs, and user groups from the category's **AllowedMembers** list as chat room managers and members to manage and participate in the room. 
  
Chat rooms that are created in a category adhere to the policies and settings enforced by the category (such as who can be in the room's membership, who can manage the room, whether file uploads are allowed, whether invitations are sent, and so on).
  

