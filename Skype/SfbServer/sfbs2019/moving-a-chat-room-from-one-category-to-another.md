---
title: "Moving a chat room from one category to another in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7e93b8f6-5a18-4476-a432-3918e01bcfa6
description: "We recommend that you do not change the category of a Persistent Chat room after the chat room is created. However, if the chat room manager has Creator privileges in another category, he or she can move the room from one category to another. The room is not deleted and recreated. It is a change of association within the database."
---

# Moving a chat room from one category to another in Lync Server 2013
[]
We recommend that you do not change the category of a Persistent Chat room after the chat room is created. However, if the chat room manager has **Creator** privileges in another category, he or she can move the room from one category to another. The room is not deleted and recreated. It is a change of association within the database. 
  
Changing a chat room category should be done rarely. A category determines the allowed membership for the chat room, so when a chat room is moved to another category, all the system access control lists (SACLs) that are no longer supported by the new category are purged. For example, if a user was a member of the room and is no longer an **AllowedMember** in the new category, the room membership will be modified and the user will be removed from the room. 
  
For details about moving a chat room by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).
  
For details about configuring chat rooms, see [Configure rooms in Lync Server 2013](configure-rooms.md) in the Deployment documentation. 
  

