---
title: Onboarding checklist for configuring Microsoft Teams core capabilities
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 03/13/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Follow the core, to-do tasks and activities in this checklist when you configure Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Configure Microsoft Teams core capabilities

| No | Activity or task | Description | Completed? | Additional information |
|----|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | Validate that your environment includes all Teams prerequisites | Teams depends on other platforms to construct an end-to-end collaboration solution. Work with your IT teams to ensure that you’ve deployed and properly configured Exchange, SharePoint Online, and OneDrive for Business. | | [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md) <br/><br/>[How Exchange and Microsoft Teams interact](exchange-teams-interact.md) |
| 2  | Validate that Teams is enabled for the tenant | Teams is turned on by default for all organizations. Check the **Services & add-ins** page in the Office 365 admin center to verify that Teams is enabled for your tenant, and enable it if necessary. | | [Set up Microsoft Teams in your Office 365 organization](office-365-set-up.md) |
| 3  | Configure roles and permissions | Teams support two types of roles: Member and Owner. <br/><br/>After adding a member to a team, an owner can also promote a member to the Owner role. As a best practice, we recommend that you have at least two owners assigned to each team. <br/><br/>By default, everyone in the organization who has a mailbox hosted on Exchange Online can create a team. A user who creates a new team is automatically granted the Owner role for that team. <br/><br/>If you need to, you can configure Office 365 group settings to only let specific users create new teams. | | [Assign roles and permissions in Microsoft Teams](assign-roles-permissions.md) <br/><br/>[Office 365 groups and Microsoft Teams](office-365-groups.md) <br/><br/>[Manage who can create Office 365 Groups](https://support.office.com/article/Manage-who-can-create-Office-365-Groups-4c46c8cb-17d0-44b5-9776-005fced8e618) |
| 4  | Configure tenant-wide Teams settings | You can configure some Teams settings at the tenant level. Users who are enabled for Teams inherit these settings from the tenant configuration:<ul><li>General</li><li>Email integration</li><li>Apps</li><li>Custom cloud storage</li><li>Calls and meetings</li><li>Messaging</li></ul>| | [Manage Microsoft Teams settings for your organization](enable-features-office-365.md) |
| 5  | OPTIONAL: Configure guest access | You use guest access in Teams to collaborate with people outside your organization by granting them access to teams and channels. Guest access is a tenant-level setting in Teams. It’s turned off by default. <br/>Enable guest access and configure tenant-wide guest settings, if your organization plans to use that feature. | | [Guest access in Microsoft Teams](guest-access.md) |
| 6  | OPTIONAL: Configure Teams naming policy | Teams leverages the naming policies for Office 365 Groups when users create or edit team names. <br/><br/>By default, no naming restrictions are applied when a user creates a team. <br/><br/>If you need to enforce rules for teams names, configure Office 365 Groups naming policies that apply to your organization. You can set mandatory prefixes and suffixes and specify blocked words. | | [Plan for Office 365 groups when creating teams in Microsoft Teams](plan-office-365-groups.md) <br/><br/>[Office 365 Groups naming policy](https://support.office.com/article/Office-365-Groups-naming-policy-6ceca4d3-cad1-4532-9f0f-d469dfbbb552) |
| 7  | Configure Exchange for the Teams SMTP domain | Teams uses Exchange Online to send notifications to team members by using the SMTP domain — email.teams.microsoft.com — when they’ve been added or removed. <br/><br/>Be sure to add this SMTP domain to the accepted domains list in your Exchange infrastructure. | | [Add the Microsoft Teams SMTP domain as an accepted domain in Exchange Online](smtp-accepted-domain.md) |
| 8  | Configure and manage user access to Teams | Although we highly recommend that you enable all users for Teams, you can allow or disallow access to Teams on a per-user basis by assigning or removing the Teams product license. | | [Manage user access to Microsoft Teams](user-access.md) |
| 9  | Assign licenses to users | Assign licenses to your users for features like Audio Conferencing, Phone System, and Calling Plans | | [Assign Skype for Business and Microsoft Teams licenses](assign-teams-licenses.md) <br/><br/>[MyAdvisor – User enablement scripts](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_2_0_6,5_2_0_3) |
| 10 | Optional: Use PowerShell to administer Teams | You can use PowerShell cmdlets rather than the Office 365 admin center to administer and manage Teams settings. | | [Microsoft Teams PowerShell](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) |
