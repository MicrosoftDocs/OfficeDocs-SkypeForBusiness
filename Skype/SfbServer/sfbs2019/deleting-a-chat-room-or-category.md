---
title: "Deleting a chat room or category in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: adccb869-0015-4eba-ac73-718bac7843b5
description: "Persistent Chat rooms can be deleted. If you have a chat room that is no longer being used, you can disable it. For details, see Disabling or enabling a chat room in Lync Server 2013."
---

# Deleting a chat room or category in Lync Server 2013
[]
Persistent Chat rooms can be deleted. If you have a chat room that is no longer being used, you can disable it. For details, see [Disabling or enabling a chat room in Lync Server 2013](disabling-or-enabling-a-chat-room.md).
  
A Persistent Chat administrator can query for disabled chat rooms, and can periodically purge and permanently delete the chat rooms, by using the Windows PowerShell cmdlet, **Remove-CsPersistentChatRoom**. 
  
Categories can be deleted. However, to delete a category, you must first either delete all chat rooms under it or move the chat rooms to a new category, leaving an empty category for deletion. Persistent Chat Server does not allow you to delete a category that contains chat rooms. For details, see [Moving a chat room from one category to another in Lync Server 2013](moving-a-chat-room-from-one-category-to-another.md).
  
For details about deleting empty categories by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).
  
For details about chat rooms and categories, see [Configure rooms in Lync Server 2013](configure-rooms.md) and [Configure categories in Lync Server 2013](configure-categories.md) in the Deployment documentation. 
  

