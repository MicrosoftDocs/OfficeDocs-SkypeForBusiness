---
title: User presence in Teams
author: jambirk
ms.author: jambirk
manager: serdars
ms.date: 08/21/2018
ms.topic: conceptual
ms.service: msteams
ms.reviewer: rakayala
description: Information Admins need to understand about Presence in Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration 
appliesto:
- Microsoft Teams
---

# User presence in Teams

Presence is part of a user’s profile in Microsoft Teams (and throughout Office 365) – and indicates the user’s current availability and status to other users in the organization. By default, anyone in your organization using Teams can see - in nearly real time - whether or not other users are available online.

## Presence states in Teams

The user presence states available in Teams are:

|User configured|App configured|
|:--- |:---|
| ![Solid green chek mark, indicating Presence Available](media/Presence_Available.png) Available|![Solid green chek mark, indicating Presence Available](media/Presence_Available.png) Available|
|| ![Open green chek mark, indicating available oof](media/Presence_Available_OOF.png) Available, Out of Office |
|  ![Solid red circle, indicating Busy](media/Presence_Busy.png) Busy |  ![Solid red circle, indicating Busy](media/Presence_Busy.png) Busy  |
|| ![Solid red circle, indicating Busy in a call](media/Presence_Busy.png) In a call|
|| ![Solid red circle, indicating Busy in a meeting](media/Presence_Busy.png) In a meeting |
|| ![Open red circle, indicating busy oof](media/Presence_Busy_OOF.png) In a call, out of office|
|  ![Red circle with white line, indicating Do Not disturb](media/Presence_DND.png) Do not disturb ||
|| ![Red circle with white line, indicating Presenting](media/Presence_DND.png) Presenting|
| ![Yellow clock icon, indicating away](media/Presence_Away.png) Away| ![Yellow clock icon, indicating away](media/Presence_Away.png) Away|
|| ![Yellow clock icon, indicating away](media/Presence_Away.png) Away Last Seen *time*|
|![Yellow clock icon, indicating away, be right back](media/Presence_Away.png) Be right back| |
|| ![Yellow clock icon, indicating away, off work](media/Presence_Away.png)  Off Work|
|| ![Gray circle with x, indicating Offline](media/Presence_Offline.png) Offline |
|| ![Open gray circle, indicating status unknown](media/Presence_Unknown.png) Status unknown|
||![Open red circle with diagonal line, indicating blocked](media/Presence_Blocked.png) Blocked |
|| ![Purple circle with arrow, indicating Out of office](media/Presence_OOF.png) Out of Office|
|||
 
Users can manually set their current presence state to some options, and their state gets reflected to all other users. Additional user presence details are also automatically updated based on user activity (such as Available or Away), Outlook calendar states (such as In a meeting), or Teams app states (In a call, Presenting), to states that are indented in the list.

There is a 15 minute inactivity timeout, after which your users' current presence state will be reset to Away.

Users can specify who can break through (contact them overriding a Do Not Disturb setting). These settings are available in-app.

## Teams is not Skype for Business

The following admin settings in Skype for Business are different in Teams:
- Presence sharing is always enabled in Teams for users in the organization. Privacy (deciding who can see presence) configuration is not available in Teams.
- Presence sharing with everyone (including Federated services) is always enabled for users in Teams. Their contact list (if they had one in Skype for Business) is visible under **Chat > Contacts** or under **Calls > Contacts**.
- Client Do Not Disturb and Breakthrough features are always enabled for users in Teams.
- Calendar (includes out of office and other calendar information) integration  is always enabled for users in Teams if integrated with Outlook.
- The *Last seen* or *Away since* (if in a dual environment with Skype for Business) indicator is always enabled for users in Teams.

> [!NOTE]
> The ability of a Teams admin to customize these settings is not currently supported.


## Coexistence with Skype for Business

See [Coexistence with Skype for Business](coexistence-chat-calls-presence.md) for details on how Teams presence functions when coexisting with Skype for Business. 
