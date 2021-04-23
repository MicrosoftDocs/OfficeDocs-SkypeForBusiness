---
title: Assisted upgrades | Skype Business Online to Teams Upgrade 
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: billkau
audience: admin
description: Overview of assisted upgrades from Skype for Business Online to Teams
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: Teams-upgrade-guidance
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Assisted upgrades from Skype for Business Online to Microsoft Teams

Microsoft offers assisted upgrades to Teams to help organizations make a successful transition from Skype for Business Online as the service retires July 31, 2021. Assisted upgrades reduce the number of technical tasks you need to do and allow for greater focus on organizational preparedness, user awareness, and Teams training.

We recommend that you review our [upgrade guidance](https://aka.ms/SkypeToTeams) before your upgrade. Our upgrade guidance includes recommended activities and helpful resources for completing an upgrade from Skype for Business Online to Teams. This guidance applies to any organization planning an upgrade to Teams, whether they manage all aspects of the upgrade or use the assisted process.

> [!NOTE]
> If you're scheduled for an assisted upgrade to Teams, you can perform your own upgrade from Skype for Business Online before your scheduled upgrade date. For more information about how to manually upgrade to Teams, see our [upgrade guidance](https://aka.ms/SkypeToTeams).
>
> Assisted upgrade is not available for on-premises deployments of Skype for Business Server.

## Notifications for scheduled customers

Skype for Business Online customers that are scheduled for assisted upgrades to Teams will receive a series of upgrade notifications. These notifications will begin 90 days before the scheduled upgrade date. These notifications will be delivered as *Plan for Change* posts in the Microsoft 365 Message Center, upgrade dashboard notifications in Teams admin center, and in-app flags to end users.

Upgrade notifications will include the scheduled date of the assisted upgrade, and will link to upgrade resources and training to help drive adoption and usage of Teams.

## The assisted upgrade experience

Assisted upgrades will begin in August 2021 with tenant-specific dates shared in the scheduling notifications mentioned above.

The duration of the upgrade will vary by volume of users and the characteristics of the deployment. However, in most cases, users within a tenant will be upgraded within 24 hours of the start of the upgrade. During this time, end users will still have access to Skype for Business Online functionality. Once the upgrade has completed and users sign out of Skype for Business Online, they'll start using Teams for messaging, meetings, and calling.

## The post-upgrade experience

When the assisted upgrade completes, the **Coexistence Mode** for upgraded users is set to Teams Only and can only be changed to a different coexistence mode by Microsoft. We recommend that you review [Teams Only mode considerations](teams-only-mode-considerations.md) before your upgrade. The table below provides a high-level overview of the Teams Only user experience.

|  |  |
|---------|---------|
|**Chat and Calling**     | <UL><LI>All calls and chats are started and received in Teams<LI>Users can communicate (chat/call) with any Skype for Business user<LI>Organizations can enable Teams users to communicate with users of the Skype consumer service by managing [external access permissions](manage-external-access.md)<LI>Teams users who attempt to sign in to Skype for Business Online will be redirected to Teams</UL>  |
|**Meetings**     |  <UL><LI>Users schedule all new meetings in Teams (plugin replaced)    </UL>   |
|**Migrated Data**     |<UL><LI>Existing contacts from Skype for Business Online including federated (but no distribution lists)<LI>Existing Skype for Business Online meetings are converted to Teams meetings</UL>         |

## Related content

- [Getting started with your Microsoft Teams upgrade](upgrade-start-here.md)
- [Skype for Business Online retirement](skype-for-business-online-retirement.md)
- [Get-CsTeamsUpgradeStatus](/powershell/module/skype/get-csteamsupgradestatus?view=skype-ps)
- [Teams Only mode considerations](teams-only-mode-considerations.md)
