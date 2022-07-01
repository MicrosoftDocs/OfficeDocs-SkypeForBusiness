---
title: User presence in Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: rakayala
description: Learn the Presence states in Teams and the administrative settings for the Presence feature.
ms.custom: seo-marvel-apr2020
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# User presence in Teams

Presence is part of a user's profile in Microsoft Teams (and throughout Microsoft 365 or Office 365). Presence indicates the user's current availability and status to other users. By default, anyone in your organization using Teams can see (in nearly real time) if other users are available online. Presence is updated in real time on the web and desktop versions when you refresh the page on mobile.

 > [!NOTE]
 > For details about Teams user profiles on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

 > [!NOTE]
 > Teams respects your privacy configuration so if you have enabled the privacy mode, your presence will not be visible to external users.

## Presence states in Teams


|User configured|App configured|
|:--- |:---|
| ![Solid green check mark, indicates Presence Available.](media/Presence_Available.png) Available|![Solid green check mark, indicates Presence Available](media/Presence_Available.png) Available|
|| ![Open green check mark, indicates available oof.](media/Presence_Available_OOF.png) Available, Out of Office. Note: Out of office is automatically set for the periods of time where the user sets "automatic replies". If the user is using the app during these periods of time, a dual presence might be shown, such as "Out of office, available". |
|  ![Solid red circle, indicates Busy.](media/Presence_Busy.png) Busy |  ![Solid red circle, indicates Busy](media/Presence_Busy.png) Busy  |
|| ![Solid red circle, indicates Busy in a call.](media/Presence_Busy.png) In a call|
|| ![Solid red circle, indicates Busy in a meeting.](media/Presence_Busy.png) In a meeting |
|| ![Open red circle, indicates Busy.](media/Presence_Busy_OOF.png) On a call, out of office|
|  ![Red circle with white line, indicates Do Not Disturb.](media/Presence_DND.png) Do not disturb ||
|| ![Red circle with white line, indicates Presenting.](media/Presence_DND.png) Presenting|
|| ![Red circle with white line, indicates Focusing.](media/Presence_DND.png) Focusing. Focus happens when the users schedule focus time in MyAnalytics/Insights in their calendars.|
| ![Yellow clock icon, indicates away.](media/Presence_Away.png) Away| ![Yellow clock icon, indicates away.](media/Presence_Away.png) Away|
|| ![Yellow clock icon, indicates away](media/Presence_Away.png) Away Last Seen *time*|
|![Yellow clock icon, indicates away, be right back.](media/Presence_Away.png) Be right back| |
|![Gray circle with x, indicates Offline.](media/Presence_Offline.png) Appear offline|![Gray circle with x, indicates Offline](media/Presence_Offline.png) Offline.  When users aren't logged in on any of their devices for a few minutes, they appear offline. |
|| ![Open gray circle, indicates status unknown.](media/Presence_Unknown.png) Status unknown|
|| ![Purple circle with arrow, indicates Out of office.](media/Presence_OOF.png) Out of Office. Out of Office is used when an automatic reply is set. |

 > [!NOTE]
 > For users that have their mailbox hosted on-prem, presence delays of one hour (maximum) are expected.

App-configured presence states are based on user activity (Available, Away), Outlook calendar states (In a meeting), or Teams app states (In a call, Presenting). When you're in focus mode based on your calendar, **Focusing** will be the state people see in Teams. Focus mode will display as **Do not disturb** in other products.

Your current presence state changes to Away when you lock your computer or when your computer enters idle or sleep mode. On a mobile device, your presence status changes to Away whenever the Teams app is in the background.

Users receive all chat messages sent to them in Teams regardless of their presence state. If a user is offline when someone sends them a message, the chat message appears in Teams the next time the user is online. If a user state is set to Do not disturb, the user will still receive chat messages, but banner notifications aren't displayed.

Users receive calls in all presence states except for Do not disturb, in which incoming calls go to voicemail. If the recipient blocked the caller, the call won't be delivered and the caller sees the recipient's presence as Offline.

Users can add people to their priority access list by going to **Settings** > **Privacy** in Teams. People who have priority access can contact the user even when the user's status is set to Do not disturb.

### Dual presence

  The way presence works for most users is motivated by the events in the calendar or device events, such as a call. The user can override this status in the UI by manually setting states, which have some expiration time.

## User configured states expiration

When a user selects a specific presence state, it takes precedence over any app activity update. For example, if a user sets herself as Do not disturb, her presence will remain as Do not disturb even if she attends a meeting or answers a call.

User configured states have default expiration settings in Teams, in order to prevent users from displaying a status that may not be relevant after a period of time.

|User configured state|Default expiration|
|:--- |:---|
| Busy|1 day|
| Do not disturb|1 day|
| Others|7 days|

> [!NOTE]
> A user can also configure manually a duration for her presence. For instance, a user can set herself as Appear offline until tomorrow morning.

## Admin settings in Teams compared to Skype for Business

The following admin settings Skype for Business are different in Teams:

- In Teams, presence sharing is always enabled for users in the organization. Privacy (where you define who can see presence) configuration isn't available in Teams.
- Presence sharing with everyone (including Federated services) is always enabled for users in Teams. Their contact list (if they had one in Skype for Business) is visible under **Chat > Contacts** or under **Calls > Contacts**.
- Client Do Not Disturb and Breakthrough features are always enabled for users in Teams.
- Calendar (includes out of office and other calendar information) integration  is always enabled for users when Teams is integrated with Outlook.
- The *Last seen* or *Away since*  indicator is always enabled for users in Teams if the organization also uses Skype for Business.

> [!NOTE]
> The ability of a Teams admin to customize these settings is not currently supported.

## Admin settings in Teams compared to Microsoft Outlook

Teams presence in Outlook is supported on the Outlook 2013 desktop app and later for contacts in the same organization.

If the upgrade mode policy of the user account is set to TeamsOnly, Outlook talks to Teams to get presence. If the user account isn't set to TeamsOnly, then Outlook talks to Skype for Business.

## Coexistence with Skype for Business

See [Coexistence with Skype for Business](coexistence-chat-calls-presence.md) for details on how Teams presence functions when your organization also uses Skype for Business.
