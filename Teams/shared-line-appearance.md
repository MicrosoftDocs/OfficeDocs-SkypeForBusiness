---
title: "Shared line appearance in Microsoft Teams"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.date: 02/19/2019
ms.reviewer: srividhc
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
- Teams_ITAdmin_Help
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Phone System
description: "Shared line appearance lets a user choose a delegate to answer or handle calls on their behalf."
---

# Shared line appearance in Microsoft Teams

Shared line appearance is part of the delegation feature that lets a user choose a delegate to answer or handle calls on their behalf. This feature is helpful if a user has an administrative assistant who regularly handles the user’s calls. In the context of shared line appearance, a manager is someone who authorizes a delegate to make or receive calls on their behalf, and a delegate can make and receive calls on behalf of someone else.

> [!IMPORTANT]
> This feature is only available in Teams Only deployment mode. For more details on Teams deployment modes, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md)

## License required

A user must be an enterprise voice user to be a delegate or set up delegation and enable others to make or receive calls on their behalf.

Both managers and delegates need to be enterprise voice enabled. The shared line experience is part of delegation, and requires no additional license. For additional details on the licensing model, See [Office 365 licensing for Microsoft Teams](office-365-licensing.md).

## Configuring delegation and shared line appearance

Delegation and shared line appearance are user-driven features: there are no admin settings to configure. For information about how to use the feature, see [Share a phone line with a delegate](https://support.office.com/article/share-a-phone-line-with-a-delegate-16307929-a51f-43fc-8323-3b1bf115e5a8)

The tenant admin should enable delegation via the **TeamsCallingPolicy AllowDelegation** setting for this feature to work.

## Shared line appearance feature availability

Shared line appearance is currently supported by the following apps and devices.

| Capability | Teams Desktop | Teams Mac App | Teams Web App (Edge) |Teams mobile iOS/Android App | Teams IP phone |
|------------|---------------|---------------|----------------------|-----------------------------|----------------|
| Set up delegation | Yes | Yes | Yes | No | No |
| Receive calls on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Call a phone number on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Call a Teams user on behalf of another | Yes | Yes | Yes | Yes | Yes |
| See the admin view of shared lines | Yes | Yes | Yes | No | No |
| See the admin view of manager's call activities | Yes | Yes | Yes | No | No |
| See the manager view of delegates | Yes | Yes | Yes | No | No |
| Admin or manager can hold or resume | Yes | Yes | Yes | No | No |

## Limitations

Managers can add up to 25 delegates, and delegates can have up to 25 managers. There is no limit to the number of delegation relationships that can be created in a tenant. 
 
If the delegator and delegate are not in the same geographic location, it is up to the PSTN provider to allow caller ID to show up from a different geographic location for a delegated (on behalf of) call. 
 
## More information

[Share a phone line with a delegate](https://support.office.com/article/share-a-phone-line-with-a-delegate-16307929-a51f-43fc-8323-3b1bf115e5a8)
