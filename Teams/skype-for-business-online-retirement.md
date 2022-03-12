---
title: Skype for Business Online retirement
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: landerl
audience: admin
description: Learn about the retirement plan for Skype for Business Online, and how Microsoft is helping customers migrate to Teams. 
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
f1.keywords:
- NOCSH
appliesto:
- Microsoft Teams
ms.custom: seo-marvel-apr2020
---


# Skype for Business Online retirement

In July 2019, we announced the July 31, 2021 retirement of Skype for Business Online, giving our customers two years to plan their upgrades to Microsoft Teams. Teams is the core app for communication and collaboration in Microsoft 365. As Skype for Business Online is retired, we want to ensure customers have the information and resources they need to plan and execute a successful upgrade to Teams.   The Skype consumer service is not affected by this retirement.

## Why is Skype for Business Online retiring?

Since its introduction, Skype for Business Online has been a valuable tool for millions of people around the world. By combining instant messaging, calling, and video into one application, Skype for Business Online established new possibilities for business communications. Microsoft Teams is the next chapter in that vision.

The capabilities of Microsoft Teams go beyond those of Skype for Business Online. By combining chat, video, calling, document collaboration, and application integration into a single experience, Teams enables entirely news way of working. And ongoing platform innovation and development means Teams users benefit from richer performance, functionality, flexibility, and security.

Teams isn’t just an upgrade for Skype for Business Online, it’s a powerful tool that enables companies, schools, and organizations to become more agile and improve the efficiency of key workflows. Learn more about the potential benefits of Teams for your organization in the Forrester white paper, [The Total Economic Impact™ of Microsoft Teams](https://www.microsoft.com/microsoft-365/blog/wp-content/uploads/sites/2/2019/04/Total-Economic-Impact-Microsoft-Teams.pdf?rtc=1).

For more information about the Skype for Business Online retirement, see [FAQ — Upgrading from Skype for Business to Microsoft Teams](FAQ-journey.yml).

## What this means for organizations with Skype for Business Online

 Microsoft provides an assisted upgrade process to help you move remaining Skype for Business Online users to Teams Only. Teams is available in most Microsoft 365 Business and Enterprise plans, and your existing licensing investments carry forward to Teams. Capabilities that are premium workloads in Skype for Business Online today will continue to be premium workloads in Teams. For example, if you have purchased Audio Conferencing standalone or as part of E5 with Skype for Business, Audio Conferencing will be enabled in Teams.

## What this means for organizations with on-premises deployments of either Skype for Business Server or Lync Server
Support for on-premises deployment of Skype for Business Server and Lync Server are not affected by the retirement of Skype for Business Online. However, hybrid customers with a mix of users homed in online and on-premises must upgrade any *online* users with Skype for Business Online to Microsoft Teams by assigning them Teams Only mode using TeamsUpgradePolicy. In addition, Microsoft is providing assisted upgrades to help automate the upgrade of any remaining Skype for Business Online users to Teams Only mode.  Hybrid organizations need not move their on-premises Skype for Business users to the cloud as as result of this retirement. Microsoft fully supports hybrid organizations with a mix of TeamsOnly users and on-premises Skype for Business users. Customers with hybrid deployments of Skype for Business Server or Lync Server 2013 should review [Implications of the upcoming retirement of Skype for Business Online](/skypeforbusiness/hybrid/plan-hybrid-connectivity#implications-of-the-upcoming-retirement-of-skype-for-business-online).


## How Microsoft is helping customers upgrade to Teams

We strongly recommend that you begin your upgrade from Skype for Business Online to Teams today.

Take advantage of the resources available to help plan your Teams deployment and upgrade from Skype for Business:

- [Teams deployment and upgrade documentation](upgrade-start-here.md) – Free technical guidance for IT administrators.

- [Teams upgrade planning workshops](./upgrade-workshops-landing-page.yml) – Free interactive upgrade planning workshops, where you’ll receive guidance, best practices and resources designed to help you plan and implement your upgrade to Teams.

- [Assisted upgrades from Skype for Business Online to Microsoft Teams](upgrade-assisted.md) – Automated program that assists you with the technical steps of upgrading Skype for Business Online users to Teams.

- [FastTrack for Microsoft 365](https://www.microsoft.com/fasttrack/microsoft-365) – Teams deployment assistance available for qualifying plans.

- [Teams live training](./instructor-led-training-teams-landing-page.yml) – Free online training classes designed to get your organization up and running with Teams.

- [Teams Chalk Talks](./chalk-talks-landing-page.yml) – Free online workshops for IT pros and decision makers sharing best practices for some of the most popular and compelling scenarios in Teams.

- [Microsoft Partners](https://www.microsoft.com/solution-providers/home) – Microsoft solution providers can help you take full advantage of Teams.

- [Microsoft Teams blog](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/bg-p/MicrosoftTeamsBlog) – Get the latest Teams news covering new features, adoption and usage resources, Teams devices, and integration with other business productivity applications.

If you’re a current Skype for Business Online customer, start planning your upgrade to Teams today. We’re excited for you to experience its powerful communication and collaboration capabilities, and we’re committed to helping along the way.

## What to expect post-retirement
It is no longer possible for users homed in the cloud to be assigned a mode other than TeamsOnly. This means:
 - When licensing new users (except if user is homed in on-premises Skype for Business Server), these users will automatically be assigned TeamsOnly mode, regardless of the tenant's global policy of TeamsUpgradePolicy.
 - In hybrid organizations, when moving a user homed on-premises to the cloud, users are automatically assigned TeamsOnly mode (regarldess of whether the `MoveToTeams` switch was specified in `Move-CsUser`.)
 - Users that are homed in the cloud (e.g. do use Skype for Business server on-premises) cannot be assigned a mode other than TeamsOnly.

However, customers may have remaining portions of their user population that are homed in Skype for Business Online and are not yet assigned Teams Only mode.  Customers should assign Teams Only mode to these users as soon as possible.  In addition, Microsoft will provide assisted upgrades for Skype for Business Online users not in Teams Only mode.  The assisted upgrade experience depends on whether your organization is a pure online organization or an organization with on-premises Skype for Business users. After the assisted upgrade is complete, all *online* users will be in Teams Only mode. Any on-premises users remain on-premises are not Teams Only. Users in Teams Only mode receive incoming chats and calls, and schedule meetings, in Teams. Users in Teams Only mode will not be able to initiate chats or calls or schedule meetings in Skype for Business Online. Teams Only users will still be able to join Skype for Business meetings scheduled by users still using Skype for Business Server.

For more information, see [Assisted Upgrades from Skype for Business Online to Microsoft Teams](upgrade-assisted.md).


