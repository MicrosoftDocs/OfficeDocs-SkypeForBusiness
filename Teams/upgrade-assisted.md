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
ms.localizationpriority: medium
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

Microsoft retired Skype for Business Online on July 31, 2021.  Microsoft is providing an assisted upgrade process to help organizations move remaining Skype for Business Online users to Teams Only.  Microsoft assisted upgrades reduce the number of technical tasks and simplify the transition to a world without Skype for Business Online whether your organization is:
 - A pure online organization that needs to upgrade from *Skype for Business Online* to become pure Teams Only, or
 - A hybrid organization with users in both *Skype for Business Online* **and** an on-premises *Skype for Business Server* environment, which must upgrade only its Skype for Business *Online* user to Teams Only.

We recommend that you review our [upgrade guidance](https://aka.ms/SkypeToTeams) before your upgrade. Our upgrade guidance includes recommended activities and helpful resources for completing an upgrade from Skype for Business Online to Teams. This guidance applies to any organization planning an upgrade to Teams, whether they manage all aspects of the upgrade or use the assisted process.

## The assisted upgrade experience
Skype for Business Online customers that are scheduled for assisted upgrades to Teams will receive various forms of notifications: *Plan for Change* posts in the Microsoft 365 Message Center, upgrade dashboard notifications in Teams admin center, and in-app flags to end users. Upgrade notification in the Message Center and Teams admin center include the scheduled date of the assisted upgrade as well as a link to upgrade resources and training to help drive adoption and usage of Teams.

The assisted upgrade experience differs slightly depending on whether your organization has any users homed in an on-premises Skype for Business Server environment:
- **Pure online organizations:** For organizations *without* any on-premises Skype for Busineess Server users, the assisted upgrade process applies the `TeamsUpgradeOverridePolicy` policy to your organization. When this policy is applied, all users of Skype for Business Online will be placed in TeamsOnly mode.
- **Hybrid Organizations with on-premises Skype for Business users:** This includes organizations with any users homed in Skype for Business Server, regardless of whether Hybrid has been configured. These organizations may have users that fall into one of the following categories:

  - On-premises users homed on Skype for Business Server (that may or may not use Teams, but are not Teams Only users)
  - TeamsOnly users that homed in Skype for Business Online
  - Non-TeamsOnly users that are homed in Skype for Business Online

The assisted upgrade process will only impact the last category of users: Non-Teams Only users homed in Skype for Business Online will be upgraded to Teams Only mode. On-premises Skype for Business users and existing TeamsOnly users won't be impacted by the assisted upgrade process.

> [!NOTE]
> Your organization can continue to use Skype for Business Online until your upgrade is complete. If you're scheduled for an assisted upgrade to Teams, you can perform your own upgrade from Skype for Business Online before your scheduled upgrade date. For more information about how to manually upgrade to Teams, see our [upgrade guidance](https://aka.ms/SkypeToTeams).

The duration of the upgrade will vary by volume of users and the characteristics of the deployment. In most cases, users within a tenant will be upgraded within 24 hours of the start of the upgrade. During this time, end users will still have access to Skype for Business Online functionality. Once the upgrade has completed and users sign out of Skype for Business Online, they'll start using Teams for messaging, meetings, and calling.

## The post-upgrade experience

When the assisted upgrade completes, the **Coexistence Mode** for upgraded users is set to Teams Only. We recommend that you review [Teams Only mode considerations](teams-only-mode-considerations.md) before your upgrade. The table below provides a high-level overview of the Teams Only user experience.

:::row:::
    :::column span="1":::
        **Chat and Calling**
    :::column-end:::
    :::column span="3":::
        - All calls and chats are started and received in Teams
        - Users can communicate (chat/call) with any Skype for Business user
        - Organizations can enable Teams users to communicate with users of the Skype consumer service by managing [external access permissions](manage-external-access.md)
        - Teams users who attempt to sign in to Skype for Business Online are redirected to Teams
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        **Meetings**
    :::column-end:::
    :::column span="3":::
        - Users schedule all new meetings in Teams (plugin replaced)
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        **Migrated Data**
    :::column-end:::
    :::column span="3":::
        - Existing contacts from Skype for Business Online including federated (but no distribution lists)
        - Contacts are migrated when users log into Teams for the first time.
            > [!IMPORTANT]
            >Contacts must be migrated within 90 days of the completion of your upgrade.
        - Existing Skype for Business Online meetings are converted to Teams meetings
            > [!IMPORTANT]
            > Customers with pure Skype for Business Online configurations need to use the Meeting Migration Service (MMS) to migrate existing Skype for Business Online meetings to Teams meetings. We recommend using MMS prior to the assisted upgrade date. For more information about MMS, see [Using the Meeting Migration Service (MMS)](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).
    :::column-end:::
:::row-end:::

If you have a Skype for Business Server hybrid deployment and upgrade to Teams, you can move users between Skype for Business Server and Teams after your upgrade is complete.

## Related content

- [Getting started with your Microsoft Teams upgrade](upgrade-start-here.md)
- [Skype for Business Online retirement](skype-for-business-online-retirement.md)
- [Get-CsTeamsUpgradeStatus](/powershell/module/skype/get-csteamsupgradestatus?view=skype-ps&preserve-view=true)
- [Teams Only mode considerations](teams-only-mode-considerations.md)
