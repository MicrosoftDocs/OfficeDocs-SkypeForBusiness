---
title: "Creating or editing a new room in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/19/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa8f4349-cfd9-4036-9c4d-de8fb2c4c8a4
description: "Configuring Persistent Chat rooms is commonly handled by users; a Persistent Chat administrator typically does not configure or manage chat rooms. Windows PowerShell cmdlets to manage rooms are available only to CsPersistentChatAdministrator Administrators."
---

# Creating or editing a new room in Lync Server 2013
[]
Configuring Persistent Chat rooms is commonly handled by users; a Persistent Chat administrator typically does not configure or manage chat rooms. Windows PowerShell cmdlets to manage rooms are available only to **CsPersistentChatAdministrator** Administrators. 
  
Users who are **Creators** in any given category can use the Lync client to create and manage rooms. Users who have been designated as managers for a specific chat room can also perform ongoing management of the room, such as editing the room properties or membership. 
  
> [!TIP]
> Persistent Chat administrators can also be Creators, and they are not subject to the restrictions placed on Creators. 
  
Optionally, if you are a Persistent Chat administrator, you can employ a user interface to create and manage chat rooms instead of using Windows PowerShell cmdlets. To do this, SIP-enable an administrator for Persistent Chat Server, and then use the Lync client to create and manage chat rooms.
  
If you want to create a custom room management workflow for your users, you can set the **RoomManagementUrl** property on your Persistent Chat Server configuration to redirect users to your custom solution from the Lync client. 
  
For details about configuring chat rooms by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).
  
For details about configuring chat rooms, see [Configure rooms in Lync Server 2013](configure-rooms.md) in the Deployment documentation. 
  
> [!NOTE]
> Persistent Chat Server lets users create and manage chat room for a specific site. Users cannot, however, create or manage chat rooms on other sites within the same topology. Be sure to specify chat room Creators and Managers for all the sites in your organization. 
  
> [!NOTE]
> Users who are homed on a Lync Server Survivable Branch Appliance are unable to create new chat rooms or view the room card for existing rooms. 
  

