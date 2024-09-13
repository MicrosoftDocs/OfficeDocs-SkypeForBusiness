---
title: User presence in Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: petrhudecek
ms.date: 09/12/2024
description: Learn the Presence states in Teams and the administrative settings for the Presence feature.
ms.custom: 
  - seo-marvel-apr2020
  - chat-teams-channels-revamp
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# User presence in Teams

Presence is part of a user's profile in Microsoft Teams (and throughout Microsoft 365). Presence indicates the user's current availability and status to other users. By default, anyone in any organization using Teams can see (in nearly real time) if other users are available online.

For details about Teams user profiles on different platforms, see also [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

 > [!NOTE]
 > Teams respects your privacy configuration so if you have enabled the [privacy mode](/powershell/module/skype/set-csprivacyconfiguration#-enableprivacymode), your presence isn't visible to people outside the organization.

## Presence states in Teams

|User-configured|App-configured|
|:--- |:---|
| ![Solid green check mark, indicates Presence Available.](media/Presence_Available.png) Available|![Solid green check mark, indicates Presence Available](media/Presence_Available.png) Available|
|| ![Open green check mark, indicates available oof.](media/Presence_Available_OOF.png) Available, Out of Office. Note: Out of office is automatically set for the periods of time where the user sets "automatic replies." If the user is using Teams during these periods of time, the user's presence is shown alongside the Out of Office indicator. |
|  ![Solid red circle, indicates Busy.](media/Presence_Busy.png) Busy |  ![Solid red circle, indicates Busy](media/Presence_Busy.png) Busy  |
|| ![Solid red circle, indicates Busy in a call.](media/Presence_Busy.png) In a call|
|| ![Solid red circle, indicates Busy in a meeting.](media/Presence_Busy.png) In a meeting |
|| ![Open red circle, indicates Busy.](media/Presence_Busy_OOF.png) In a call, out of office|
|  ![Red circle with white line, indicates Do Not Disturb.](media/Presence_DND.png) Do not disturb ||
|| ![Red circle with white line, indicates Presenting.](media/Presence_DND.png) Presenting|
|| ![Red circle with white line, indicates Focusing.](media/Presence_DND.png) Focusing. Focus happens when the users schedule focus time in MyAnalytics/Insights in their calendars.|
| ![Yellow clock icon, indicates away.](media/Presence_Away.png) Away| ![Yellow clock icon, indicates away.](media/Presence_Away.png) Away|
|| ![Yellow clock icon, indicates away](media/Presence_Away.png) Away Last Seen *time*|
|![Yellow clock icon, indicates away, be right back.](media/Presence_Away.png) Be right back| |
|![Gray circle with x, indicates Offline.](media/Presence_Offline.png) Appear offline|![Gray circle with x, indicates Offline](media/Presence_Offline.png) Offline.  When users aren't logged in on any of their devices for a few minutes, they appear offline. |
|| ![Open gray circle, indicates status unknown.](media/Presence_Unknown.png) Status unknown|
|| ![Purple circle with arrow, indicates Out of office.](media/Presence_OOF.png) Out of Office. Out of Office is used when an automatic reply is set or your calendar has an event that's set to show as "Out of Office." |

The order of statuses, from most available to least available, is:

1. Available
1. Busy
1. In a meeting
1. In a call
1. Do not disturb
1. Be right back
1. Away
1. Offline

> [!NOTE]
> For users that have their mailbox hosted on-prem, presence delays of one hour (maximum) are expected.

## Automatic status settings and user experience

App-configured presence states are based on user activity (Available, Away), Outlook calendar states (In a meeting), or Teams app states (In a call, Presenting). When you're in focus mode based on your calendar, **Focusing** is the state people see in Teams. Focus mode displays as **Do not disturb** in other products.

Your current presence state changes to Away when you lock your computer or when your computer enters idle or sleep mode. On a mobile device, your presence status changes to Away whenever the Teams app is in the background.

Users receive all chat messages sent to them in Teams regardless of their presence state. If a user is offline when someone sends them a message, the chat message appears in Teams the next time the user is online. If a user state is set to Do not disturb, the user still receives chat messages, but banner notifications aren't displayed.

Users receive calls in all presence states except for Do not disturb, in which incoming calls go to voicemail. If the recipient blocked the caller, the call won't be delivered and the caller sees the recipient's presence as Offline.

Users can add people to their priority access list by going to **Settings** > **Privacy** in Teams. People who have priority access can contact the user even when the user's status is set to Do not disturb.

Call queues can use presence to route calls to agents. For more information, see [Create a Call Queue in Microsoft Teams](create-a-phone-system-call-queue.md).

## Manual status settings by users

Users can manually select a status as follows:

- Users in a call or in a meeting can select any status and it lasts for the duration of the call or the meeting.

- Otherwise, users can select any status that is less available than the automatically calculated status. (For example, if a user's calculated status is **Do not disturb**, they could choose a status of **Away** but not **Available**.)

Users can set a duration for the presence that they set manually. If a user doesn't set a duration, their presence remains manually set as follows:

- Indefinitely if it's **Appear offline**
- For 1 day if it's **Busy** or **Do not disturb**
- For 7 days if it's any other status

## Admin settings in Teams compared to Skype for Business

The following admin settings Skype for Business are different in Teams:

- In Teams, presence sharing is always enabled for users in the organization unless Privacy mode is enabled. In Privacy mode, presence isn't visible to people outside the organization.
- Presence sharing with everyone (including Federated services) is always enabled for users in Teams. Their contact list (if they had one in Skype for Business) is visible under **Chat > Contacts** or under **Calls > Contacts**.
- Client Do Not Disturb and Breakthrough features are always enabled for users in Teams.
- Calendar integration (includes out of office and other calendar information) is always enabled for users when Teams is integrated with Outlook.
- The *Last seen* or *Away since*  indicator is always enabled for users in Teams if the organization also uses Skype for Business.

> [!NOTE]
> The ability of a Teams admin to customize these settings is not currently supported.

## Admin settings in Teams compared to Microsoft Outlook

Teams presence in Outlook is supported on the Outlook 2013 desktop app and later for contacts in the same organization.

If the upgrade mode policy of the user account is set to TeamsOnly, Outlook talks to Teams to get presence. If the user account isn't set to TeamsOnly, then Outlook talks to Skype for Business.

## Coexistence with Skype for Business

See [Coexistence with Skype for Business](coexistence-chat-calls-presence.md) for details on how Teams presence functions when your organization also uses Skype for Business.
