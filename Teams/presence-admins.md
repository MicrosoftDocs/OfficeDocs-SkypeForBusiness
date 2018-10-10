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
|<span style="color: green">&bull; </span> Available||
||<span style="color: green">&bull; </span> Available until *time*|
|<span style="color: red">&bull; </span> Busy||
||<span style="color: red">&bull; </span> In a call|
||<span style="color: red">&bull; </span> In a meeting|
|<span style="color: red">&bull; </span> Do not disturb||
||<span style="color: red">&bull; </span> Presenting|
|<span style="color: yellow">&bull; </span> Away|<span style="color: yellow">&bull; </span>Away|
||<span style="color: yellow">&bull; </span> Away Last Seen *time*|
||<span style="color: yellow">&bull; </span> Away be right back|
|| <span style="color: yellow">&bull; </span> Away Off Work|
|||
||<span style="color: gray">&bull; </span> Offline|
||<span style="color: gray">&bull; </span> Presence unknown|
||<span style="color: gray">&bull; </span> Blocked|
||<span style="color: gray">&bull; </span> Out of Office|
||<span style="color: gray">&bull; </span> Out of office until *date*|
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
- Presence sharing is always enabled for users in Teams for the organization
- Presence sharing with everyone is always enabled for users in Teams. Their contact list (if they had one in SfB) is visible under **Chat > Contacts** or under **Calls > Contacts**.

The ability of an Admin to customize these settings is not currently supported.