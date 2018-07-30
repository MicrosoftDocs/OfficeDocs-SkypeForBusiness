---
title: Microsoft Education governance FAQ for IT pros - Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: serdars
ms.date: 07/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Answers to frequently asked questions from administrators of Microsoft Education teams who use Teams.
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

# Microsoft Education governance FAQ for IT pros

## Can I control who can create teams?

In general, we recommend against preventing anyone from creating teams. If everyone can create teams, Teams is more likely to be widely adopted. Faculty, teachers, or students can  use Teams to create study groups or special interest groups. This will help Teams be accepted inside and outside of the classroom.

In our experience, user education helps ensure responsible Teams usage. As soon as users understand that creating teams isn’t anonymous, they understand the implications of carelessly creating them and tend to shy away from misusing the tool.

If you’re sure you want to control who can create teams, see [Manage who can create Office 365 Groups](https://support.office.com/article/manage-who-can-create-office-365-groups-4c46c8cb-17d0-44b5-9776-005fced8e618).

## How do I control team creation?  I'm worried students are going to create inappropriate Teams.

To avoid inappropriate or misleading names, or just to provide more structure for how teams are named, you can use the Office 365 Groups naming policy (currently in preview):

-   **Prefix-Suffix naming policy** You can use prefixes or suffixes to define the naming convention of teams (groups), for example, **GRP_US_My Group_Engineering**. The prefixes and suffixes can be fixed strings or user attributes (such as **[Department]**) that are added to the name based on the user who’s creating the team.
-   **Custom Blocked Words** You can upload a set of words that users in a specific organization are blocked from using in names of teams they create. For example, you can block the terms **CEO**, **Payroll**, and **HR** from being used in team names for groups they don’t apply to.

For detailed instructions, see [Office group naming policy](https://support.office.com/article/office-365-groups-naming-policy-6ceca4d3-cad1-4532-9f0f-d469dfbbb552).

> [!Note]
> If teams are created automatically by using the input from another system (for example, School Data Sync), verify that the input data complies with the naming policy you’ve configured; if it doesn’t, team creation will fail.

## Can I see who created a team?

To find out who created a specific team, see [Search the audit log for events in Microsoft Teams](audit-log-events.md).

## How do I automatically create a team for each course at the beginning of the semester or quarter?

At the start of each semester or quarter, you’ll need a number of new teams. It might make sense to take an automated approach to create these teams automatically, populate them with the right users, and set the right permissions:

-   School Data Sync can create Office 365 Groups for Exchange Online and SharePoint Online, class teams for Microsoft Teams and OneNote Class notebooks, school groups for Intune for Education, and rostering and single sign-on (SSO) integration for many other third-party applications. Learn more at [Overview of School Data Sync](https://docs.microsoft.com/schooldatasync/overview-of-school-data-sync).
-   With PowerShell, you can create teams and channels, and configure settings automatically. See [Microsoft Teams PowerShell](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information.
-   You can use the Microsoft Graph API (currently in beta) to create, configure, clone, and archive teams. See [Use the Microsoft Graph API to work with Microsoft Teams](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/teams_api_overview) for more information.

## How do I deal with teams when the semester or quarter ends?

We recommend that you first think about how you want to handle Teams data when the school semester or quarter is over: how long to keep it, when (or whether) to delete it. You can use the following tools to implement your strategy:

-   **Retention policy:** Use this to delete all data older than an age you specify to make sure that old data is removed from chats (for all or some users) and channels. You can also configure Teams to retain content so it can’t be deleted. For more information, see [Retention policies for Microsoft Teams](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Retention-policies-for-Microsoft-Teams/ba-p/178011).
-   **Expiry policy:** Configure teams to expire after a certain number of days. Thirty days before expiration, all owners of a team are notified that their team needs to be renewed, otherwise it will be deleted (though an administrator can recover deleted teams for an additional 30 days). This setting is very useful for making sure unused teams are sunsetted.
    > [!Tip]
    > Be sure to set expiration policies in a way that if teams are created at the start of the semester or quarter, they won’t expire during the holidays. Learn more at [Office 365 Group Expiration Policy](https://support.office.com/article/office-365-group-expiration-policy-8d253fe5-0e09-4b3c-8b5e-f48def064733).

-   **Archive team:** This setting puts teams into read-only mode. They can still be browsed and searched, but no one can add any new posts. This might be useful if you want students to be able to access the content of a course even after they’ve completed it. [Archive or restore a team](https://support.office.com/article/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7) describes how team owners can archive a team; administrators can leverage the [Graph API (beta)](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/resources/teams_api_overview).
 
## Can I specify a template for my faculty members to use?

Yes. Users can select **Create Team from existing template** when creating a new team, and administrators can use the [Graph API (beta)](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/resources/teams_api_overview).

## What tasks can I automate via PowerShell or Graph?

The [Microsoft Graph API (beta)](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/resources/teams_api_overview) can do the following:

-   Create a team.
-   Add members and owners.
-   Add channels.
-   Add apps.
-   Shortcut those steps by cloning an existing team, and get its tabs too.
-   Give the user a link to the team you just created.
-   Remove members, owners, channels, and apps when you no longer need them.
-   Archive the team when it's no longer active. 
-   Delete the team.

[PowerShell](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) can do the following:

-   Create a team.
-   Add members and owners.
-   Add channels.
-   Remove members, owners, and channels when you no longer need them.
-   Delete the team.
 
## How do I control guest access for research collaboration?

You can use guest access to invite users from outside of your tenant, which can be useful for research collaboration or guest lectures:

-   Use domain whitelisting to allow or block guests based on their domain.
-   Turn guest access on and off for particular Office 365 Groups and teams, to control which teams can (and can’t) invite guests.
-   Use the audit log to see which alerts were sent to invited guests.

For more information, see [Guest access in Office 365 Groups](https://support.office.com/article/Guest-access-in-Office-365-Groups-bfc7a840-868f-4fd6-a390-f347bf51aff6#PickTab=Manage).

## What should I use the audit logs for?

You can check the audit logs to see:
-   Who was invited as a guest to which team.
-   Who created which team.

For more information, see [Search the audit log for events in Microsoft Teams](audit-log-events.md).

## Teams evolves so quickly. How can I stay up-to-date?
We recommend the following resources to get the latest updates on Teams:

-   [What's new in Microsoft Teams](https://support.office.com/article/What-s-new-in-Microsoft-Teams-d7092a6d-c896-424c-b362-a472d5f105de)
-   [Microsoft Teams blog](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/bg-p/MicrosoftTeamsBlog)
