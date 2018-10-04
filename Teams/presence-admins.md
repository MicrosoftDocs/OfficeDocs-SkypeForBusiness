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

- Available
    - Available until *time*
- Busy
    - In a call
    - In a meeting 
- Do not disturb
    - Presenting
- Away
    - Away Last Seen *time*
    - Away be right back
    - Away Off Work

    - Offline
    - Presence unknown
    - Blocked
    - Out of Office
        - Out of office until *date*

Users can manually set their current presence state to first-level options, and their state is reflected to all other users. Additional user presence is also automatically updated based on machine activity (such as Available or Away), Outlook calendar states (such as In a meeting), or Teams app states (In a call, Presenting), to states that are indented in the list.

**(SfB and Outlook integration: are these live outside MSFT yet?)**

Users can specify who can break through (contact them overriding a Do Not Disturb setting). These settings are available in-app.

## Dual environments

If you're in a dual environment where some users are on Skype for Business and some are on Teams, or some users have both, Teams also integrates with Skype for Business and allows presence changes made in one app to be visible in the other. Unified presence also shows up in the user's Office contact card and chat/call options from the Office contact card will use Microsoft Teams. Skype for Business has some other Presence states, but these map into the simpler Teams states when interop is used.

## Teams is not Skype for Business

The following Admin capabilities in Skype for Business are different in Teams:
- Enabling/disabling Client Do Not Disturb and Breakthrough features (always enabled for users in Teams)
- Privacy (who can see presence) configuration (not available in Teams)
- Calendar (includes OOF & other calendar info) integration  (always enabled for users in Teams if integrated with Outlook)
- Last seen/Away since indicator (always enabled for users in Teams)
- Custom presence status (not enabled for users in Teams)
- Disabling presence sharing for the organization (presence is always enabled for users in Teams)
- Customizing whether presence is shared with everyone or only with a user's contact list (always enabled for users in Teams)
