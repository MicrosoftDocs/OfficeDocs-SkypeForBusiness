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

Presence is part of a user’s profile in Microsoft Teams (and throughout Office 365) – and indicates the user’s current availability and status to other users in the organization.

By default, anyone in your organization using Teams can see whether other users are person are available online, in a meeting, offline, or another indicator.

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

Users can manually set their current presence state to first-level options, and their state is reflected to all other users with whom presence is shared. User presence is also automatically updated based on machine activity (such as Available or Away), Outlook calendar states (In a meeting), or Teams app states (In a call, Presenting) to states that are indented in the list.

Teams integrates with Outlook to gather calendar information, and shows users as "Busy" when they are in a meeting scheduled in Outlook.

If you're in a dual environment where some users are on Skype for Business and some are on Teams, or some users have both, Teams also integrates with Skype for Business and allows presence changes made in one app to be visible in the other. Unified presence also shows up in the user's Office contact card and chat/call options from the Office contact card will use Microsoft Teams. Skype for Business has some other Presence states, but these map into the simpler Teams states when interop is used.

**(SfB and Outlook integration: are these live outside MSFT yet?)**

If enabled by their Admin, users can specify when their presence is set to Do Not Disturb, who can breakthrough, and who is blocked from seeing presence information. These settings are available in-app.

**(Where in Teams admin center can Admins enable this? it Looks like the options exist for SfB but not for Teams. Should these topics really be dual-purpose?)**

 
### Presence Policies

IT Admins can tweak presence policies for
1. Privacy configuration (who can see presence)
2. Calendar integration (includes OOF & other calendar info)
3. Last seen/Away since indicator
4. Custom presence status

IT Admins can specify 
- whether or not presence is shared 
- whether it’s with everyone or with folks on the contact list 

**Where in teams admin center can Admins set it?**


