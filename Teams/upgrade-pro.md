---
title: Upgrade Pro for Microsoft Teams - Microsoft Teams
author: dearbeen
ms.author: dearbeen
manager: serdars
ms.date: 06/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Use this guidance if you're in a large org or you have heavily customized your Skype for Business deployment. 
localization_priority: Priority
ms.custom: Teams-upgrade-guidance
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

# Upgrade Pro

Designed for larger organizations or those with complex deployments of Skype for Business (for example, hybrid or cloud voice deployments), Upgrade Pro accounts for a longer upgrade lifecycle along with a variety of upgrade scenarios, including running Microsoft Teams alongside Skype for Business until Teams is ready for your organization. 

Segmented into three phases, Upgrade Pro covers:

-   **Pre-upgrade**: Start realizing the value of Teams as you prepare for your upgrade over time. Consider these steps an upgrade prerequisite to help ensure a positive experience as you transition to Teams when it’s ready for you. If your organization has already been running Teams alongside Skype for Business, use these pre-upgrade activities as a validation checkpoint for your organization’s readiness to upgrade users to Teams.
-    **Upgrade**: When your organization is ready for users to stop using Skype for Business, you’ll want to ensure they have ample notice to get training and start using Teams (if they haven’t already). You’ll also want to take steps such as moving their Skype for Business meetings to Teams to ensure an optimal experience.
-    **Post-upgrade**: After your entire organization is on Teams, implement a plan to maximize value. This includes monitoring your network for quality, promoting adoption of Teams while ensuring that Skype for Business usage is winding down, and planning for expanded functionality as the Teams roadmap continues to evolve.
 
> [!NOTE]
> The plan below is based on the assumption that you’ve enabled [Islands mode](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md#islands-mode) for your users before the upgrade and you’ve segmented your upgrade journey into four upgrade groups or waves, allowing you to control the user upgrade experience while maintaining momentum. Adjust the plan as needed to meet the needs of your organization. Additional guidance based on expanded coexistence capabilities will be available later this year.

## Pre-Upgrade

**Prepare your organization for Teams.**  To help ensure a successful upgrade to Teams, it’s important to allocate adequate time for preparation. Not only will your organization be able to quickly start realizing the value of Teams, you’ll be able to accelerate your upgrade from Skype for Business as soon as Teams is ready for you. Monitor the [roadmap](https://aka.ms/skype2teamsroadmap) for the enhancements that are planned for Teams; this will help you identify the right upgrade timeline for your organization. If you’ve already enabled Teams alongside Skype for Business, use these pre-upgrade activities as a checkpoint to validate your organization’s readiness before you upgrade users to Teams.

Days 1&ndash;5
-   [Gather your project stakeholders](upgrade-enlist-stakeholders.md)
-   [Define your project scope](upgrade-define-project-scope.md).
-   [Understand upgrade and coexistence modes](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md).

Days 6&ndash;10
-   [Prepare your environment for Teams](upgrade-prepare-environment.md).
-   [Prepare your organization](upgrade-prepare-organization.md).
-   Announce the pending launch of Microsoft Teams.
-   Notify your helpdesk that it needs to prepare to support Teams.
-   Conduct a launch event.

Days 10&ndash;40
-   [Conduct a user pilot of Teams alongside Skype for Business](pilot-essentials.md).

Day 45
-   Announce the official launch of Teams.
-   Enable the appropriate coexistence mode for your users.
-   Enlist your Teams champions.

Day 45 until upgrade begins
-   Make a plan to monitor the Teams [roadmap](https://aka.ms/skype2teamsroadmap) and continually assess organizational readiness, to identify the right time for your organization to move to Teams.
-   Send additional communications to drive excitement and adoption of Teams.

## Upgrade

**Make the official move to Teams.** When you upgrade your users, you move them into Teams-only coexistence mode. Teams becomes their primary app for chat, meetings, calling, and collaboration, and access to the Skype for Business app is disabled. Although the technical aspects of this phase are quite simple, consider the effect the change might have on user experience and allow time for users to officially transition their activities from Skype for Business to Teams. To reduce users’ having different experiences with different clients, try to limit the end-to-end upgrade window to approximately 45 days.

Days 1&ndash;2
-   Validate that you’ve completed the pre-upgrade activities described above.
-   Segment your user base into four upgrade groups.
-   Send notification of the upgrade to all users.
-   Enable **Notify** mode for all users.

Day 7
-   Send notification to upgrade group 1 that their upgrade will begin in two weeks.
-   Monitor network health and helpdesk calls for any technical or user upgrade experience issues, and mitigate as needed.

Day 14
-   Send a reminder to upgrade group 1 that their upgrade will begin in one week.
-   Monitor network health and helpdesk calls for any technical or user upgrade experience issues, and mitigate as needed.

Day 21
-   Move upgrade group 1 to Teams-only mode.
-   Send a “Welcome to Teams” notification to upgrade group 1.

Days 14&ndash;42
-   Repeat the preceding upgrade activities for the remaining upgrade groups on a rolling cycle. That is, begin upgrade group 2 notifications on day 14, upgrade group 3 notifications on day 21, and upgrade group 4 notifications on day 28. This should allow for all upgrades to be complete by day 42.

Day 45
-   Send [post-upgrade feedback surveys](upgrade-essentials.md#sample-surveys) to all users.

## Post-Upgrade

**Maximize business value with Teams.** After your organization is fully upgraded to Teams, take time to evaluate your success against your goals and implement a plan to continue forward momentum.

Days 1&ndash;14
-   Assess your initial upgrade success against the goals you established in the pre-upgrade phase.
-   Implement a mitigation plan for any goals that aren’t on track.

Ongoing
-   Monitor network health and helpdesk calls for any technical or user upgrade experience issues, and mitigate as needed.
-   Drive user momentum with email, newsletters, or other communications that focus on upcoming new features, success stories, and so on. <!-- – NOTE – add direct links back to SWT or Teams adoption content-->
-   Plan technical readiness and user readiness initiatives to prepare for new functionality and Microsoft 365 optimization. <!-- (point to blog??)-->

> [!Note]
> Our Upgrade Pro content is continually evolving. Be sure to check back for the latest guidance, and read the [Teams blog](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/bg-p/MicrosoftTeamsBlog). 

> [!Important]
> If you’re an admin on your Office 365 tenant, you might start seeing upgrade options in your PowerShell cmdlet or Teams Admin Center. Having the option to upgrade doesn’t necessarily mean your organization is ready for this change. For an optimal user experience, confirm that Teams meets your collaboration and communication requirements, validate that your network is ready to support Teams, and implement your user readiness plan before upgrading users to Teams.
 
