---
title: "Call sharing and group call pickup"
ms.author: lolaj
author: lolaj
manager: serdars
ms.date: 12/13/2018
ms.reviewer: srividhc
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: 
- msteams
search.appverid: MET150
ms.collection:
- Teams_ITAdmin_Help
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Phone System
description: "Call sharing and group call pickup let users share incoming calls with colleagues so that calls can be captured when the user is unavailable."
---

# Call sharing and group call pickup

The call sharing and group call pickup features of Microsoft Teams let users share their incoming calls with colleagues so that the colleagues can answer calls that occur while the user is unavailable.

Group call pickup is less disruptive to recipients than other forms of call sharing (such as call forwarding or simultaneous ringing) because users can configure how they want to be notified of an incoming shared call (via audio and visual notification, visual only, or banner in the Teams app), and they can decide whether to answer it.

To share calls with others, a user creates a call group and adds the users they want to share their calls with. Then they choose a simultaneous ring or forward setting. See [Call forwarding and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e) for details.

> [!IMPORTANT]
> Users, the call group owner, and members of the call group must be in Teams Only deployment mode. For more details on Teams deployment modes, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md)

## License required

Users must be Enterprise Voice enabled to set up and use call sharing and group call pickup. For additional details on the licensing model, See [Office 365 licensing for Microsoft Teams](office-365-licensing.md).

## Configure group call pickup

To set up group call pickup, a user first configures a call group and then adds the users they want to share their calls with. Then, they choose a simultaneous ring or call forward setting. For more information, see [Call forwarding and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e). For more information about how a user can configure group call pickup, see [Add a delegate](https://support.office.com/article/add-a-delegate-for-calls-in-teams-16307929-a51f-43fc-8323-3b1bf115e5a8?storagetype=live)

Call group creation and notification preferences are user-driven features; administrators do not have to configure these features for their users. Call groups cannot be created from security groups or Office 365 groups; they must be created in Teams.

Admins cannot prevent users from creating groups and changing other call pickup setting. The functionality is not blocked.

## Limitations

A tenant can contain a maximum of 32,768 call groups. There can be a maximum of 5 users in each call group. 