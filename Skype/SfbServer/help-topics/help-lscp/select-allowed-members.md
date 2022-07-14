---
title: "Select Allowed Members"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/24/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.lscp.SelectAllowedMembers
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: e9e6df4a-e58a-4104-9f72-2f5c818353e1
description: "Creating and managing Persistent Chat rooms is much easier with the correct use of categories. A Persistent Chat Administrator can define AllowedMembers and Creators for each category, and can also define the default chat room settings and behaviors that will be applied to all chat rooms created in the category. Persistent Chat Administrators create and manage categories by using the control panel or Windows PowerShell cmdlets."
---

# Select Allowed Members

Creating and managing Persistent Chat rooms is much easier with the correct use of categories. A Persistent Chat Administrator can define **AllowedMembers** and **Creators** for each category, and can also define the default chat room settings and behaviors that will be applied to all chat rooms created in the category. Persistent Chat Administrators create and manage categories by using the control panel or Windows PowerShell cmdlets.

Users, Organizational Units (OUs), and user groups that are identified as Creators of the category are the only individuals and groups that are allowed to create rooms in the category. After the category is created, they can choose users, OUs, and user groups from the category's **AllowedMembers** list as chat room managers and members to manage and participate in the room.

## Tasks that you can perform

You can perform the following tasks on the **Select Allowed Members** page:

- [Configure Categories](/previous-versions/office/lync-server-2013/lync-server-2013-configure-categories)

- [New Persistent Chat Server Features](/previous-versions/office/lync-server-2013/lync-server-2013-new-persistent-chat-server-features)

For details about the different procedures that you can perform by using the Skype for Business Server Control Panel, see [Manage Skype for Business Server 2015](../../manage/manage.md).

## To configure categories for chat rooms

In **Membership**, in the **Allowed members** section, add or remove users and other Active Directory Domain Services principals (users, distribution groups, organizational units, and so on) that are permitted to be added as members of chat rooms belonging to the category. Principals permitted by a category can search for the rooms in the category (unless the room is hidden, in which case only members of the room can search for it in the directory).


For details about Persistent Chat Server features and capabilities, see [Overview of Persistent Chat Server](/previous-versions/office/lync-server-2013/lync-server-2013-overview-of-persistent-chat-server) in the Planning documentation. For details about working with Persistent Chat Server configurations, see [Configuring Persistent Chat Server](/previous-versions/office/lync-server-2013/lync-server-2013-configuring-persistent-chat-server) in the Deployment documentation and [Managing Lync Server 2013, Persistent Chat Server](/previous-versions/office/lync-server-2013/managing-lync-server-2013-persistent-chat-server) in the Operations documentation.

## See also

[Understanding Persistent Chat Membership](/previous-versions/office/lync-server-2013/understanding-persistent-chat-membership)