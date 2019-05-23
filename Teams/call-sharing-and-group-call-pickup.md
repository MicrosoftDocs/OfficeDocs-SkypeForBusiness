---
title: "Call sharing and group call pickup in Microsoft Teams"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.date: 02/19/2019
ms.reviewer: srividhc
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
- Teams_ITAdmin_Help
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Phone System
description: "Call sharing and group call pickup let users share incoming calls with colleagues so that calls can be captured when the user is unavailable."
---

# Call sharing and group call pickup in Microsoft Teams

The call sharing and group call pickup features of Microsoft Teams let users share their incoming calls with colleagues so that the colleagues can answer calls that occur while the user is unavailable.

Group call pickup is less disruptive to recipients than other forms of call sharing (such as call forwarding or simultaneous ringing) because users can configure how they want to be notified of an incoming shared call (via audio and visual notification, visual only, or banner in the Teams app), and they can decide whether to answer it.

To share calls with others, a user creates a call group and adds the users they want to share their calls with. Then they choose a simultaneous ring or forward setting. See [Call forwarding and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e) for details.

> [!IMPORTANT]
> Users, the call group owner, and members of the call group must be in Teams Only deployment mode. For more details on Teams deployment modes, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md)

## License required

Users must be Enterprise Voice enabled to set up and use call sharing and group call pickup. For additional details on the licensing model, See [Office 365 licensing for Microsoft Teams](office-365-licensing.md).

## Configure group call pickup

To set up group call pickup, a user first configures a call group (this is not the same as a security group or an Office 365 group), and then adds the users they want to share their calls with. Then, they choose a simultaneous ring or call forward setting. For more information and step-by-step procedures, see [Call forwarding and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e).

Call group creation and notification preferences are user-driven features; administrators do not have to configure these features for their users. Call groups cannot be created from security groups or Office 365 groups; they must be created in Teams.

Admins should enable call groups via the **TeamsCallingPolicy AllowCallGroups** setting for a user. Admins can only control whether this user can configure call groups. Once the bit is set to true, admins cannot prevent the user from configuring and adding the call group users of their choice.

## Limitations

A tenant can contain a maximum of 32,768 call groups. There can be a maximum of 5 users in each call group. 

## More information

[Call forwarding and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e)