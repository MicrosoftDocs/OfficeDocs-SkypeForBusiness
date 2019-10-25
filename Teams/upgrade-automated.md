---
title: Automated upgrades| Skype Business to Teams Upgrade 
author: serdarsoysal
ms.author: billkau
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: billkau
audience: admin
description: Overview of automated upgrades from Skype for Business to Teams
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Automated Upgrades from Skype for Business Online to Microsoft Teams

Microsoft offers automated upgrades to Teams to help Small Businesses make the successful transition from Skype for Business Online prior to the July 31, 2021 retirement of the service. The automated upgrade reduces the number of technical tasks required of customers and allows for greater focus on organizational preparedness, user awareness, and Teams training.

A successful upgrade from Skype for Business to Microsoft Teams requires planning for technical and user readiness. When you’re ready to get started,  Microsoft offers an [upgrade action plan](upgrade-basic.md) featuring core recommended activities and associated resources for implementing a successful move from Skype for Business to Teams.

## Notifications for scheduled customers

Skype for Business Online customers eligible for automated upgrades to Teams will receive a series of upgrade notifications beginning 30 days prior to their scheduled upgrade date. These notifications will be delivered as *Plan for Change* posts in the Admin Message Center, upgrade emails to the Global Admin, and in-app flags to end-users.

These notifications will communicate the scheduled date of the automated upgrade, will link to upgrade resources and training to help drive adoption and usage of Teams, and will give customers the option to postpone their automated upgrade an additional 30 days in the event they are not ready to upgrade by their scheduled date.

## The automated upgrade experience

Automated upgrades execute on their scheduled upgrade date which is communicated in the notification emails, Message Center, as well as the Teams Admin portal. The upgrade will take approximately 15 minutes during which time end users will still have access to Skype for Business Online functionality. Once the upgrade has completed, and users logout of Skype for Business Online, users will only be able to use Teams for messaging, meetings and calling.

## The post-upgrade experience

When your automated upgrade completes, the **Coexistence Mode** is set to Teams Only and can only be changed to a different coexistence mode by Microsoft. Admins should review [Teams Only mode considerations](teams-only-mode-considerations.md) prior to upgrade. The table below provides a high-level overview of the Teams Only user experience.


|  |  |
|---------|---------|
|**Chat and Calling**     | <UL><LI>All calls and chats are initiated and received in Teams<LI>Users can interop (chat/call) with any Skype for Business user<LI>Users cannot communicate with users who are using Skype for Consumer<LI>Users are redirected to Teams if they try to sign in to Skype for Business      </UL>  |
|**Meetings**     |  <UL><LI>Users schedule all new meetings in Teams (plugin replaced)    </UL>   |
|**Migrated Data**     |<UL><LI>Existing contacts from Skype for Business including federated (but no distribution lists)<LI>Existing Skype for Business meetings (both on-prem and online) get converted to Teams meetings</UL>         |

## Postponing your automated upgrade

Successful transitions from Skype for Business Online to Microsoft Teams require technical planning and user readiness to ensure your organization is prepared to take advantage of expanded functionality and performance of Teams. However, as you plan your upgrade, you may find your organization is not yet ready to upgrade to Teams at this time.

If you receive a notification regarding your scheduled automated upgrade to Teams and you wish to postpone to a later date, the Office 365 Global Admin may log into the Teams Admin portal and click the *Postpone* button. Doing so will push out the automated upgrade date 30 days. When you refresh the Teams Admin portal after postponing, you will see a notification that includes your new automated upgrade date.

## Requests to downgrade to Skype for Business

We allow one-time downgrades from Teams to SfBO, to allow tenants to further prepare for their upgrade to Teams. Tenants that have downgraded will be re-engaged for automated upgrade 60 days from their downgrade date.

## Related content

- [Getting started with your Microsoft Teams upgrade](upgrade-start-here.md)
- [Skype for Business Online retirement](skype-for-business-online-retirement.md)
- [Get-CsTeamsUpgradeStatus](https://docs.microsoft.com/powershell/module/skype/get-csteamsupgradestatus?view=skype-ps)
- [Teams Only mode considerations](teams-only-mode-considerations.md)

