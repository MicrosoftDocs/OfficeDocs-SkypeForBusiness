---
title: Upgrade and Coexistence of Skype for Business and Teams
author: arachmanGitHub
ms.author: MyAdvisor
manager: lehewe
ms.date: 03/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Details of Skype for Business and Teams coexistence options and modes, and upgrade journeys to Teams from Skype for Business with example scenarios.
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---
# Upgrade and coexistence of Skype for Business and Teams

Microsoft Teams, a chat-based workspace for modern collaboration, delivers communications capabilities such as private chat and calling, ad-hoc and scheduled meetings, audio conferencing, and public switched telephone network (PSTN) calling; ultimately, Teams provides a complete communications and collaboration solution.

If your organization has an existing Skype for Business deployment and intends to upgrade to Teams, you can start the journey by letting users discover Teams themselves and organically adopt Teams alongside Skype for Business. Or, you might decide to manage the journey by gradually introducing Teams capabilities until your organization is ready to upgrade everyone to Teams.

Throughout the journey, you can gradually control your users’ experience, ranging from using both Teams and Skype for Business, to using Teams for group collaboration only and Skype for Business for unified communications, to upgrading a select group of your users to a Teams-only experience.

## Upgrade and coexistence concepts and terminology
To help guide your decision-making process, familiarize yourself with the following concepts and terminology relevant to upgrading from Skype for Business to Teams.

### Group collaboration–only mode
If your organization’s business requirement is to use Teams solely for modern collaboration while keeping unified communications capabilities in Skype for Business—either for the entire organization or some parts of it—you might consider using this mode in your upgrade journey.

In this mode, Teams is configured to support teams and channels-based conversations only, with private chats and meetings disabled.

### Group collaboration and meetings mode
If your organization needs the capabilities that Teams provides for meetings, but business needs require you to keep enterprise voice capabilities in Skype for Business, you can configure Teams to deliver modern collaboration and meetings capabilities to your entire organization (or some parts of it).

Along with using Teams for teams and channels-based conversations in this mode, users start using Teams to schedule and conduct their meetings. Private chats and voice and video calling remain on Skype for Business.

### Islands mode
To facilitate quick adoption of Teams alongside existing Skype for Business deployments, you can deploy Teams independently from Skype for Business in “islands mode.” In this mode, Teams users can immediately use Teams with all its capabilities with other Teams users, while other users can continue using Skype for Business and remain productive with no impact on how they’re using Skype for Business today.

### Islands mode with temporary interoperability
This mode allows one-way temporary presence, chat, and calling interoperability from Teams to Skype for Business when the following conditions are met:
- The Teams user is also homed at, and enabled for, Skype for Business Online.
- The Skype for Business user has never used Teams (or isn’t licensed for Teams).

This mode is helpful when you want users who are primarily using Teams to connect with other users in the organization who are still using Skype for Business only.

After the users who previously used only Skype for Business start to use Teams, all their chats and calls from other Teams users will arrive in Teams. This switches these users to islands mode. From that point, they must keep running Teams to ensure they stay connected with the other Teams users in the organization.

### Single-client modes
When you use single-client modes during an upgrade journey, you provide individual users a single client app to work with, either Teams or Skype for Business. The two types of single-client modes are described below.

#### Teams-only single-client mode
Users who are ready to use Teams as their primary communications and collaboration tool can be upgraded as Teams-only users.

An upgraded user can only use the Skype for Business client to join existing Skype for Business meetings or meetings on Skype for Business organized by non-upgraded users or external parties. An upgraded user can continue to communicate with other users in the organization who are still using Skype for Business by using the interoperability capabilities between Teams and Skype for Business.

In this upgraded mode, the Skype for Business client no longer provides basic IM, presence indicators, chat, calling, and meeting capabilities. Users working in upgraded mode must use Teams as their primary communications and collaboration tool.

#### Skype for Business–only single-client mode
Users who need to stay in Skype for Business can be configured as Skype for Business–only users. 
Users configured in this mode will be prevented from using Teams and will be able to communicate with Teams-only users by using the interoperability capabilities between Teams and Skype for Business.

### Upgrade and coexistence building blocks
To formally prepare your organization for its journey to Teams, you need to start planning for the upgrade scenarios that will eventually let your organization fully embrace Teams as your sole communications and collaboration solution.

When some of your users are ready to use only Teams for their day-to-day communications and collaboration needs, you can start upgrading these users to Teams by enabling single-client mode for them.

If it’s not feasible for your whole organization to move to Teams, you can start by fully adopting Teams as a group collaboration solution first while keeping Skype for Business as your organization’s unified communications solution. Another option is to start moving meetings to Teams in addition to introducing Teams group collaboration capabilities, while keeping the rest of the unified communications capabilities in Skype for Business.

[Placeholder for Image]

The following table compares upgrade and coexistence modes.

[Placeholder for table]

To learn more about enabling each of the modes described above, review [Quick start guide: Configuring Teams upgrade and coexistence](https://docs.microsoft.com/MicrosoftTeams/configuring-teams-upgrade-and-coexistence-quickstartguide) (COMING SOON!)

## Upgrade journeys
You can take multiple approaches to upgrading from Skype for Business, either online or on-premises, to Teams:
- In a simple upgrade journey, you first deploy Teams in islands mode as part of evaluation and early adoption, and then implement single-client mode with the goal of eventually removing Skype for Business from the environment for all users in the organization.
- A gradual upgrade journey delivers a specific upgrade mode to a specific group of users (also called a *cohort*), depending on their communications and collaboration requirements. Over time, the entire organization can converge into single-client mode and eventually remove Skype for Business. However, if your organization has compelling business reasons to keep Skype for Business—such as dependency on a Unified Communications Managed API (UCMA)–based solution that integrates with line-of-business applications, or an ethical wall solution currently available for Skype for Business only—you can upgrade a majority of users to single-client mode while retaining Skype for Business for a portion of your user population.

> [!IMPORTANT]
> For both types of upgrade journey, if your organization is currently a Skype for Business on-premises deployment only, you need to start planning to implement Skype for Business hybrid before upgrading your users to single-client mode. This will also help facilitate interoperability with Teams.

> [!NOTE]
> The Teams-only single-client upgrade mode requires that the users who are part of cohorts be homed in Skype for Business Online, and a hybrid relationship between your Skype for Business on-premises deployment and your Skype for Business Online tenant is required to facilitate the upgrade and interoperability between Skype for Business and Teams. The move to Skype for Business Online must be completed for users who are part of the cohorts before they’re upgraded to single-client mode. Skype for Business Server 2019, and also a future cumulative update for Skype for Business Server 2015, will simplify the mechanics of upgrading on-premises users to Teams by managing the migration to Skype for Business Online and upgrading the users to single-client mode in one step.

### Simple upgrade journey
The simple upgrade journey is illustrated in the following diagram.

[placeholder for image]

Teams is deployed to all users in the organization and configured in Skype for Business with Collaboration only in Teams. Over time, all users are upgraded to Skype for Business with collaboration and meetings in Teams. When your organization considers that Teams is ready to fulfil all communications and collaboration needs, the user is upgraded to Teams only. Skype for Business can be retired from the environment.