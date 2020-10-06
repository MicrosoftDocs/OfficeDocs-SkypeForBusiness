---
title: User presence in Teams
author: msdmaguire
ms.author: dmaguire
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: rakayala
description: Learn the Presence states in Teams, as well as the administrative settings for the Presence feature.
ms.custom: seo-marvel-apr2020
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# User presence in Teams

Presence is part of a user's profile in Microsoft Teams (and throughout Microsoft 365 or Office 365) that indicates the user's current availability and status to other users. By default, anyone in your organization using Teams can see (in nearly real time) if other users are available online.

Teams presence in Outlook is supported on the Outlook 2013 desktop app and later.

 > [!Note]
 > For details about Teams user profiles on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Presence states in Teams

|User configured|App configured|
|:--- |:---|
| ![Solid green check mark, indicates Presence Available](media/Presence_Available.png) Available|![Solid green check mark, indicates Presence Available](media/Presence_Available.png) Available|
|| ![Open green check mark, indicates available oof](media/Presence_Available_OOF.png) Available, Out of Office |
|  ![Solid red circle, indicates Busy](media/Presence_Busy.png) Busy |  ![Solid red circle, indicates Busy](media/Presence_Busy.png) Busy  |
|| ![Solid red circle, indicates Busy in a call](media/Presence_Busy.png) On a call|
|| ![Solid red circle, indicates Busy in a meeting](media/Presence_Busy.png) In a meeting |
|| ![Open red circle, indicates Busy](media/Presence_Busy_OOF.png) On a call, out of office|
|  ![Red circle with white line, indicates Do Not Disturb](media/Presence_DND.png) Do not disturb ||
|| ![Red circle with white line, indicates Presenting](media/Presence_DND.png) Presenting|
|| ![Red circle with white line, indicates Focusing](media/Presence_DND.png) Focusing|
| ![Yellow clock icon, indicates away](media/Presence_Away.png) Away| ![Yellow clock icon, indicates away](media/Presence_Away.png) Away|
|| ![Yellow clock icon, indicates away](media/Presence_Away.png) Away Last Seen *time*|
|![Yellow clock icon, indicates away, be right back](media/Presence_Away.png) Be right back| |
|| ![Yellow clock icon, indicates away, off work](media/Presence_Away.png)  Off Work|
|| ![Gray circle with x, indicates Offline](media/Presence_Offline.png) Offline |
|| ![Open gray circle, indicates status unknown](media/Presence_Unknown.png) Status unknown|
||![Open red circle with diagonal line, indicates blocked](media/Presence_Blocked.png) Blocked |
|| ![Purple circle with arrow, indicates Out of office](media/Presence_OOF.png) Out of Office|
|||

App-configured presence states are based on user activity (Available, Away), Outlook calendar states (In a meeting), or Teams app states (In a call, Presenting). Note that when you are in focus mode based on your calendar, Focusing will be the state people see in Teams, but it will display as Do not disturb in other products.

Your current presence state changes to Away when you lock your computer or when your computer enters idle or sleep mode. On a mobile device, your presence status changes to Away whenever the Teams app is in the background.

Users receive all chat messages sent to them in Teams regardless of their presence state. If a user is offline when someone sends them a message, the chat message appears in Teams the next time the user is online. If a user state is set to Do not disturb, the user will still receive chat messages, but banner notifications aren't displayed.

Users receive calls in all presence states except for Do not disturb, in which incoming calls go to voicemail. If the recipient blocked the caller, the call won't be delivered and the caller sees the recipient's presence as Offline.

Users can add people to their priority access list by going to **Settings** > **Privacy** in Teams. People who have priority access can contact the user even when the user's status is set to Do not disturb.

## User configured states expiration
When a user selects a specific presence state, it takes precedence over any app activity update. For example, if a user sets herself as Do not disturb, her presence will remain as Do not disturb even if she attends a meeting or answers a call.

User configured states have default expiration settings in Teams, in order to prevent users from displaying a status that may not be relevant after a period of time.
|User configured state|Default expiration|
|:--- |:---|
| Busy|1 day|
| Do not disturb|1 day|
| Others|7 days|
|||

## Admin settings in Teams compared to Skype for Business

The following admin settings Skype for Business are different in Teams:

- In Teams, presence sharing is always enabled for users in the organization. Privacy (where you define who can see presence) configuration is not available in Teams.
- Presence sharing with everyone (including Federated services) is always enabled for users in Teams. Their contact list (if they had one in Skype for Business) is visible under **Chat > Contacts** or under **Calls > Contacts**.
- Client Do Not Disturb and Breakthrough features are always enabled for users in Teams.
- Calendar (includes out of office and other calendar information) integration  is always enabled for users when Teams is integrated with Outlook.
- The *Last seen* or *Away since*  indicator is always enabled for users in Teams if the organization also uses Skype for Business.

> [!NOTE]
> The ability of a Teams admin to customize these settings is not currently supported.

## Coexistence with Skype for Business

See [Coexistence with Skype for Business](coexistence-chat-calls-presence.md) for details on how Teams presence functions when your organization also uses  Skype for Business.
