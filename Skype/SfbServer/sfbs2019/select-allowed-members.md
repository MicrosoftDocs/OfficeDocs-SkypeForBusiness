---
title: "Select Allowed Members"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.SelectAllowedMembers
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e9e6df4a-e58a-4104-9f72-2f5c818353e1
description: "Creating and managing Persistent Chat rooms is much easier with the correct use of categories. A Persistent Chat Administrator can define AllowedMembers and Creators for each category, and can also define the default chat room settings and behaviors that will be applied to all chat rooms created in the category. Persistent Chat Administrators create and manage categories by using Lync Server Control Panel or Windows PowerShell cmdlets."
---

# Select Allowed Members
[]
Creating and managing Persistent Chat rooms is much easier with the correct use of categories. A Persistent Chat Administrator can define **AllowedMembers** and **Creators** for each category, and can also define the default chat room settings and behaviors that will be applied to all chat rooms created in the category. Persistent Chat Administrators create and manage categories by using Lync Server Control Panel or Windows PowerShell cmdlets. 
  
Users, Organizational Units (OUs), and user groups that are identified as Creators of the category are the only individuals and groups that are allowed to create rooms in the category. After the category is created, they can choose users, OUs, and user groups from the category's **AllowedMembers** list as chat room managers and members to manage and participate in the room. 
  
## Tasks that you can perform

You can perform the following tasks on the **Select Allowed Members** page: 
  
- [Configure categories in Lync Server 2013](configure-categories.md)
    
- [New Persistent Chat Server features in Lync Server 2013](new-persistent-chat-server-features.md)
    
For details about the different procedures that you can perform by using the Lync Server 2013 Control Panel, see [Operations in Lync Server 2013](operations.md).
  
## To configure categories for chat rooms

In **Membership**, in the **Allowed members** section, add or remove users and other Active Directory Domain Services principals (users, distribution groups, organizational units, and so on) that are permitted to be added as members of chat rooms belonging to the category. Principals permitted by a category can search for the rooms in the category (unless the room is hidden, in which case only members of the room can search for it in the directory). 
  
### 

For details about Persistent Chat Server features and capabilities, see [Overview of Persistent Chat Server in Lync Server 2013](overview-of-persistent-chat-server.md) in the Planning documentation. For details about working with Persistent Chat Server configurations, see [Configuring Persistent Chat Server in Lync Server 2013](configuring-persistent-chat-server.md) in the Deployment documentation and [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md) in the Operations documentation. 
  
## See also

#### 

[Understanding Persistent Chat membership](understanding-persistent-chat-membership.md)

