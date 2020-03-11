---
title: User presence in Teams
author: lolajacobsen
ms.author: lolaj
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: rakayala
description: Information for Admins about Presence in Teams.
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

Presence is part of a user’s profile in Microsoft Teams (and throughout Office 365) that indicates the user’s current availability and status to other users. By default, anyone in your organization using Teams can see (in nearly real time) if other users are available online.

> [!IMPORTANT]
> If you uninstall the Skype for Business client after you move a user to **Teams Only** mode, presence may stop working in Outlook and other Office apps. Presence works fine in Teams. This is resolved in Teams version 1.3.00.2160 and higher. Please ensure you have updated to the latest version of Teams, and restarted the Outlook client; then you can safely remove the Skype for Business client if desired.

Teams presence in Outlook is supported on the Outlook 2013 desktop app and later.

## Presence states in Teams

The user presence states available in Teams are:

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
 
Users can manually set their current presence state to some options, and their state gets reflected to all other users. More user presence details are also automatically updated. The changes are based on user activity (Available, Away), Outlook calendar states (In a meeting), or Teams app states (In a call, Presenting), to states that are indented in the list. There's a 15-minute inactivity timeout, after which a current presence state is reset to Away.

Users receive all chat messages sent to them in Teams regardless of their presence state. If a user is offline when someone sends them a message, the chat message appears in Teams the next time the user is online. If a user is in a Do Not Disturb state, the user will still get chat messages but a banner notification won't be displayed.

Users receive calls in all presence states except for Do Not Disturb states, in which incoming calls are delivered to their voicemail. If the recipient blocked the caller, the call won't be delivered and the caller sees the recipient's presence as Offline.

Users can add people to their priority access list by going to **Settings** > **Privacy** in Teams. People who have priority access can contact the user even when the user is in a Do Not Disturb state.

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
