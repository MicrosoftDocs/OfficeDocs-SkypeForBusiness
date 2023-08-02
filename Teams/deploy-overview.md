---
title: Microsoft Teams deployment overview (IT Admins)
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 01/26/2021
ms.topic: article
ms.service: msteams
audience: admin
description: Learn which Microsoft Teams deployment option is right for you.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
---

# Microsoft Teams deployment overview (IT Admins)

> [!TIP]
> Are you looking for information on how to install the Teams client on your PC or mobile device? Go here: [Download Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app).

There are several options for setting up Teams. To help you find the information you need, we've split up some articles into two audiences: **Small business** (fewer than 50 users) and **Medium/large business** (more than 50 users). When reading an article, choose the audience tab that best matches your organization. Here are what the tabs look like:

:::image type="content" source="media/small-large-tabs-example.png" alt-text="Example showing small and large audience tabs that appear in some articles.":::

> [!TIP]
> As a companion to this article, we recommend using the [Microsoft Teams automated setup guide](https://go.microsoft.com/fwlink/?linkid=2224815) when signed in to the Microsoft 365 admin center. This guide will customize your experience based on your environment.  To review best practices without signing in and activating automated setup features, go to the [Microsoft 365 setup portal](https://go.microsoft.com/fwlink/?linkid=2222975).

## Start with a pilot rollout

If you're a larger organization, pilot Teams with a small group of early adopters so you can learn about Teams and start planning your org-wide deployment. Later, use the guidance on the [Microsoft Teams Adoption](https://adoption.microsoft.com/microsoft-teams/#get-started) site to help you roll out Teams across your organization.

We recommend rolling out Teams in stages, workload by workload, as your organization is ready. **You don't have to wait until you've completed one step before you move to the next.** Some organizations may want to roll out all Teams features at once, while others may prefer a phased approach. Here are the Teams workloads, in the order we recommend rolling them out:

- [Chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md)
- [Meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md)
- [Cloud voice](cloud-voice-landing-page.md)

![Diagram illustrating Teams deployment pathways.](media/get-started-with-teams-quick-start-pathways.png)


If you have a medium or large organization, [use Advisor for Teams to help you roll out Microsoft Teams](use-advisor-teams-roll-out.md) to help you plan the rollout of these workloads across your organization. The Advisor uses Teams itself to create planning tasks and assign them to owners, share documents, and enable discussions amongst your deployment team.

See these additional resources to help you get started:

|Section  |Description  |
|---------|---------|
|[Small business setup](deploy-small-business.md)| The **Small business setup** section guides smaller businesses through setting up Teams. Small business may want all the core features of Teams (such as chat, teams, channels, meetings, and phone support), but don't need to plan for multiple office locations, rolling out Teams to large numbers of users, and so on.
|[Enterprise setup](deploy-enterprise-overview.md)     | The **Enterprise setup** section guides larger business through setting up Teams in situations where network planning, lifecycle management, and wide-scale adoption, are critical factors to successful deployment. This section also helps you understand the requirements for audio and video conferencing, and configuring Phone System and PSTN connectivity.         |
|[Deploy Team clients](get-clients.md)     | The **Deploy Teams clients** section provides instructions for setting up the Teams client on PC, mobile, and other devices. It also includes information on how larger business can deploy Teams across your organization and what URLs and IP addresses should be opened on your firewalls.       |
|[Teams training](training-microsoft-teams-landing-page.md)     | The **Teams training** section provides training materials for end-users who use the Teams clients, and also for organization admins who need to manage Teams across your organization.        |

## Upgrade or migrate from Skype for Business

If you're coming to Teams from Skype for Business (online or on premises), or if you need a hybrid configuration, you still want to follow the recommended path above for a Teams deployment, but first you need to do some extra planning. Start by reviewing the guidance in the table below that applies to your organization's profile.

|&nbsp;|Your organization's profile|Guidance  |
|---------|---------|---------|
|<IMG src="/office/media/icons/migration-teams.svg" alt="Migration arrow symbol" height="50" width="50">|I'm currently using Skype for Business Online, and I'm ready to move to Teams. |Go to [Upgrade to Teams](upgrade-start-here.md). |
|<IMG SRC="/office/media/icons/hybrid-teams.svg" alt="Hybrid symbol" height="50" width="50">|My organization is running Skype for Business Server, and I want to roll out Teams. |For a full-scale Teams rollout, first you need to configure hybrid connectivity between your on-premises environment and Microsoft 365. Start by reading [Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](/skypeforbusiness/hybrid/plan-hybrid-connectivity). <br><br>You should also review [Upgrade to Teams](upgrade-start-here.md).   |
|<IMG src="/office/media/icons/on-premises-teams.svg" alt="On premises symbol" height="50" width="50">|I don't have Skype for Business Server, but I do have an on-premises Public Switched Telephone Network (PSTN) solution. I want to roll out Teams, but I want to keep my on-premises PSTN solution. |Roll out Teams following  the suggestions in this article.<br><br>Then read [Plan Direct Routing](direct-routing-plan.md) to learn about using Phone System Direct Routing to hook up your on-premises PSTN solution with Teams.|