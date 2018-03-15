---
title: "Persistent Chat Server best practices"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dc18e7f7-599b-4d32-abf7-cd9e691426a2
description: "As you create your categories and Persistent Chat rooms and design your scoping and membership, the following tips can help your planning:"
---

# Persistent Chat Server best practices
[]
As you create your categories and Persistent Chat rooms and design your scoping and membership, the following tips can help your planning:
  
- If your company does not require an ethical wall, do not narrow the scope in your category tree. Put all your users in the scope of one category, and create all chat rooms in that category. Subsequently, use only membership lists to grant or restrict access to each chat room.
    
- In most cases, you should enable users to create new chat rooms so that discussions about new topics can be started any time. Do this by making the **Creators** list the same as the **AllowedMembers** list. However, if you want to allow only a central support team or designated users to create rooms, then make the **Creators** list as the appropriate subset. 
    
- Give each chat room a complete name and description summary that describes where it fits in with your organization. Because users cannot see the category name when they use the chat room, you cannot rely on the category name to help users determine the intended discussion forum for the chat room.
    
- You may want to have a custom room creation workflow if you have certain naming conventions or other access controls or validations to implement. The Persistent Chat configuration enables you to customize the **RoomManagementUrl** to something that you host. For example, when users click **Create a room** in their Lync client, they can be redirected to your custom solution. 
    
- Create a variety of add-ins that help to enhance the experience of chat rooms by bringing in other business data into chat rooms. Administrators must register the add-ins that they want to allow in the system. Chat room managers and creators can choose from the list of allowed add-ins for the ones most relevant to their respective rooms.
    
## See also

#### 

[Managing categories, rooms, and add-ins in Lync Server 2013](managing-categories-rooms-and-add-ins.md)

