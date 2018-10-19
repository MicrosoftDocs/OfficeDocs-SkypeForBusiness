---
title: User Presence in Teams
author: jambirk
ms.author: jambirk
manager: serdars
ms.date: 08/21/2018
ms.topic: article
ms.service: msteams
ms.reviewer: arachman
description: Information Admins need to understand about Presence in Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_Help
appliesto:
- Microsoft Teams
---

# User Presence in Teams

Presence is part of a user’s profile in Microsoft Teams (and throughout Office 365) – and indicates the user’s current availability and status to other users in the organization. By default, anyone in your organization using Teams can see whether or not other users are available online.

## Presence states in Teams

The user presence states available in Teams are:

|User configured|App configured|
|:--- |:---|
| ![Presence Available](media/Presence_Available.png) Available||
|| ![Presence Available](media/Presence_Available.png) Available until *time* |
|| ![available oof](media/Presence_Available_OOF.png) Available, Out of Office |
|  ![Busy](media/Presence_Busy.png) Busy ||
|| ![Busy](media/Presence_Busy.png) In a call|
|| ![Busy](media/Presence_Busy.png) In a meeting |
|| ![busy oof](media/Presence_Busy_OOF.png) In a call, out of office|
|  ![Do Not disturb](media/Presence_DND.png) Do not disturb ||
|| ![Do Not disturb](media/Presence_DND.png) Presenting|
| ![away](media/Presence_Away.png) Away| ![away](media/Presence_Away.png) Away|
|| ![away](media/Presence_Away.png) Away Last Seen *time*|
|| ![away](media/Presence_Away.png) Away be right back|
|| ![away](media/Presence_Away.png)  Away Off Work|
| ||
|| ![Offline](media/Presence_Offline_Alt.png) ![Offline](media/Presence_Offline.png) Offline |
|| ![unknown](media/Presence_Unknown.png) Status unknown|
||![blocked](media/Presence_Blocked.png) Blocked |
|| ![Out of office](media/Presence_OOF.png) Out of Office|
|||
 
Users can manually set their current presence state to some options, and their state gets reflected to all other users. Additional user presence details are also automatically updated based on user activity (such as Available or Away), Outlook calendar states (such as In a meeting), or Teams app states (In a call, Presenting), to states that are indented in the list.

**(SfB and Outlook integration: are these live outside MSFT yet?)**
**What is the inactivity timeout for available vs away? Will this ever be admin configurable?**

Users can specify who can break through (contact them overriding a Do Not Disturb setting). These settings are available in-app.

## Dual environments

If you're in a dual environment where some users are on Skype for Business and some are on Teams, or some users have both, Teams also integrates with Skype for Business and allows presence changes made in one app to be visible in the other. Unified presence also shows up in the user's Office contact card and chat/call options from the Office contact card will use Microsoft Teams. Skype for Business has some other Presence states, but these map into the simpler Teams states when interop is used.

## Teams is not Skype for Business

The following Admin settings in Skype for Business are different in Teams:
- Client Do Not Disturb and Breakthrough features are always enabled for users in Teams.
- Privacy (who can see Presence) configuration is not available in Teams.
- Calendar (includes OOF & other calendar info) integration  is always enabled for users in Teams if integrated with Outlook.
- The *Last seen* or *Away since* (if in a dual environment) indicator is always enabled for users in Teams.
- Custom presence status is not enabled for users in Teams.
- Presence sharing is always enabled in Teams for for users in the organization
- Presence sharing with everyone (including Federated services) is always enabled for users in Teams. Their contact list (if they had one in SfB) is visible under **Chat > Contacts** or under **Calls > Contacts**.

The ability of a Teams Admin to customize these settings is not currently supported.