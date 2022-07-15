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

On July 31, 2021, Microsoft retired Skype for Business Online. This retirement was announced in July 2019 to give customers two years advance notice to plan their upgrades to Microsoft Teams. Teams is the core app for communication and collaboration in Microsoft 365. With Skype for Business Online being retired, Microsoft wants to ensure customers have the required information and resources to plan and execute a successful upgrade to Teams.  The Skype consumer service isn't affected by this retirement. For background on why Skype for Business Online was retired, see [FAQ—Upgrading from Skype for Business to Microsoft Teams](FAQ-journey.yml).

Microsoft will begin decommissioning the Skype for Business Online infrastructure on or after June 30, 2022. This article contains guidance for organizations with TeamsOnly users that were upgraded from any version of Skype for Business.


## Organizations with on-premises deployments of Skype for Business Server

The retirement of Skype for Business Online doesn't affect support for on-premises deployments of Skype for Business Server and Lync Server 2013. However, hybrid customers with a mix of users homed online and on-premises must upgrade any *online* users. Any online users must be assigned TeamsOnly mode using TeamsUpgradePolicy. Microsoft is providing assisted upgrades to help automate the upgrade of remaining Skype for Business Online users to TeamsOnly mode. Hybrid organizations need not move their *on-premises* Skype for Business users to the cloud as a result of this retirement. Microsoft fully supports hybrid organizations with a mix of TeamsOnly users and on-premises Skype for Business users. Customers with hybrid deployments of Skype for Business Server or Lync Server 2013 should review [Retirement of Skype for Business Online](/skypeforbusiness/hybrid/plan-hybrid-connectivity#implications-of-the-upcoming-retirement-of-skype-for-business-online).

When creating new users in your on-premises Active Directory environment, if these users will be synchronized to Azure AD and you intend to license them for Teams, then *before assigning these users the license*, **you must first enable them in your on-premises Skype for Business deployment and ensure the change has synchronized to the cloud via Azure AD connect**.  You can verify the change has fully sync'd to the cloud using Get-CsOnlineUser. The change has synchronized if the user's HostingProvider= "SRV:".  It should not be "sipfed.online.lync.com".   

## What to expect post-retirement

It's no longer possible for users homed in the cloud to be assigned a mode other than TeamsOnly. This means:

 - When licensing new users that aren't homed in on-premises Skype for Business Server, users are automatically assigned TeamsOnly mode, regardless of the tenant's global policy of TeamsUpgradePolicy.
 - In hybrid organizations, when moving users homed on-premises to the cloud, users are automatically assigned TeamsOnly mode regardless of whether the `MoveToTeams` switch was specified in `Move-CsUser`.
 - Users homed in the cloud can't be assigned a mode other than TeamsOnly. Users homed online do *not* use Skype for Business server on-premises.

Customers may have remaining users who are homed in Skype for Business Online and who are not yet assigned TeamsOnly mode. Customers should assign TeamsOnly mode to these users as soon as possible. Microsoft will provide assisted upgrades for Skype for Business Online users not in TeamsOnly mode. The assisted upgrade experience depends on whether your organization is a pure online organization or an organization with on-premises Skype for Business users. For more information, see [Assisted Upgrades from Skype for Business Online to Microsoft Teams](upgrade-assisted.md).

After the assisted upgrade is complete, all *online* users will be in TeamsOnly mode. Users in TeamsOnly mode receive incoming chats and calls in Teams, and also schedule meetings in Teams. They can't initiate chats or calls or schedule meetings in Skype for Business Online.  However, TeamsOnly users can join Skype for Business meetings they already have or receive in the future. Finally, *any users homed on-premises remain on-premises and won't be made TeamsOnly*.

## Actions to take before June 30, 2022
Now that Skype for Business Online is retired, Microsoft will begin decommissioning the supporting infrastructure no sooner than June 30, 2022.  For any organization with TeamsOnly users that were upgraded from any version of Skype for Business, you need to take action if either of these situations applies:

- If you have any TeamsOnly users users that previoulsy had contacts in Skype for Business *and* who have not yet logged in to Teams since being upgraded.
- If you have any TeamsOnly users that still have Skype for Business Online meetings that they organized before they were upgraded to TeamsOnly.

If either of these situations apply to your organization, you must take action by June 30, 2022 as described below:

 - **Skype for Business Online Contacts:**  After a user has been upgraded to TeamsOnly mode, the first time that user logs on to Teams, any existing contacts in that user’s Skype for Business Online account will be migrated to Teams. After Microsoft removes the Skype for Business Online infrastructure, you can no longer migrate contacts *for users who haven't yet logged on to Teams.* To migrate contacts from Skype for Business to Teams, Microsoft recommends that all users who previously had Skype for Business log on to Teams at least once before June 30, 2022.

 - **Skype for Business Online Meetings:** After an organization is upgraded to TeamsOnly, users create all new meetings as Teams meetings. In some cases, TeamsOnly users may still have Skype for Business Online meetings which they previously organized. Currently, upgraded TeamsOnly users and any invited attendees can join these Skype for Business Online meetings using their Skype for Business client. After Microsoft removes the Skype for Business Online infrastructure for a given TeamsOnly user, however, any remaining Skype for Business Online meetings organized by that user will no longer exist. The organizer and any attendees won't be able to join these meetings. If users in TeamsOnly organizations have any remaining Skype for Business Online meetings that they organized, Microsoft recommends that they reschedule these meetings as Teams meetings. Alternatively, administrators may use the [Meeting Migration Service](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms#trigger-meeting-migration-manually-via-powershell-cmdlet) to convert these meetings to Teams meetings. In either case, complete these actions by June 30, 2022.  


## How Microsoft is helping customers upgrade to Teams

We strongly recommend that you begin your upgrade from Skype for Business Online to Teams today. Take advantage of the resources available to help plan your Teams deployment and upgrade from Skype for Business:

- [Teams deployment and upgrade documentation](upgrade-start-here.md) – Free technical guidance for IT administrators.

- [Teams upgrade planning workshops](./upgrade-workshops-landing-page.yml) – Free interactive upgrade planning workshops, where you’ll receive guidance, best practices, and resources designed to help you plan and implement your upgrade to Teams.

- [Assisted upgrades from Skype for Business Online to Microsoft Teams](upgrade-assisted.md) – Automated program that assists you with upgrading Skype for Business Online users to Teams.

- [FastTrack for Microsoft 365](https://www.microsoft.com/fasttrack/microsoft-365) – Teams deployment assistance available for qualifying plans.

- [Teams live training](./instructor-led-training-teams-landing-page.yml) – Free online training classes designed to get your organization up and running with Teams.

- [Teams Chalk Talks](./chalk-talks-landing-page.yml) – Free online workshops for IT pros and decision makers that describe best practices for key scenarios in Teams.

- [Microsoft Partners](https://www.microsoft.com/solution-providers/home) – Microsoft solution providers can help you take full advantage of Teams.

- [Microsoft Teams blog](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/bg-p/MicrosoftTeamsBlog) – Teams news about new features, adoption and usage resources, Teams devices, and integration with other business applications.

If you’re a current Skype for Business Online customer, start planning your upgrade to Teams today. We’re excited for you to experience its powerful communication and collaboration capabilities, and we’re committed to helping along the way.  For more information about the Skype for Business Online retirement, see [FAQ—Upgrading from Skype for Business to Microsoft Teams](FAQ-journey.yml).





