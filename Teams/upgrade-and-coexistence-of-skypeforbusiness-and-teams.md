---
title: Upgrade journey and coexistence of Skype for Business and Microsoft Teams
author: arachmanGitHub
ms.author: MyAdvisor
manager: serdars
ms.date: 04/04/2018
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Details of Skype for Business and Microsoft Teams coexistence options and modes, and upgrade journeys to Teams from Skype for Business with example scenarios.
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---
# Upgrade journey and coexistence of Skype for Business and Microsoft Teams

As an existing Skype for Business customer, your complete transition to Teams might take some time. However, you can begin realizing the value of Teams today, by enabling your users to use Teams alongside Skype for Business. Given that there is some overlapping functionality between the two apps, we recommend that you review the available upgrade modes to help determine which path is right for your organization. For example, you might opt to enable all workloads on both solutions without interoperability. Or, you might decide to manage the user experience, either by gradually introducing Teams capabilities or by targeting groups of users for select capabilities, until your organization is ready to upgrade everyone to Teams.

As with any deployment, we strongly encourage you to [pilot your intended plan](pilot-essentials.md) with a selected group of users before rolling out Teams to your broader organization. Remember, introducing new technology can be disruptive for users. Take time to assess user readiness and implement a communication and training plan to keep users in the know and accelerate their acceptance of Teams. 

> [!IMPORTANT]
> The Skype for Business to Teams upgrade journey is rapidly evolving. This article will help you understand the upcoming Teams upgrade, but it doesn't include end-to-end upgrade instructions. A successful upgrade from Skype for Business will include both technical and user readiness-focused activities. We're working on this guidance now, and we'll be publishing it soon.
 
## Upgrade and coexistence modes defined
To help guide your decision-making process, familiarize yourself with the various modes, concepts, and terminology relevant to upgrading from Skype for Business to Teams.

### Skype for Business with Teams collaboration&ndash;only mode

In this mode, Teams is configured to support teams and channels-based conversations only, with private chats, calling, and meetings disabled.

This mode is a great way to introduce Teams in your environment while you continue leverage your existing investment in Skype for Business. 

### Skype for Business with Teams collaboration and meetings mode
Along with using Teams for teams and channels-based conversations in this mode, users start using Teams to schedule and conduct their meetings. Private chats, and voice and video calling, remain on Skype for Business.

If your organization needs the capabilities that Teams provides for meetings, but business needs require you to keep enterprise voice capabilities in Skype for Business, you can configure Teams to deliver Skype for Business with Teams collaboration and meetings capabilities to your entire organization (or some parts of it).

### Islands mode
This is the default mode. You use it to deploy Teams independently of Skype for Business. 

In this mode, Teams users can immediately use Teams with all its capabilities with other Teams users, while other users can continue using Skype for Business and remain productive with no impact on how they’re using Skype for Business today.

> [!NOTE]
> Islands mode comes with one-way temporary interoperability that allows chat interoperability from Teams to Skype for Business when the following conditions are met:
> - The Teams user is homed at, and enabled for, Skype for Business Online.
> - The Skype for Business user has never used Teams (or isn’t licensed for Teams).
>
> This mode is helpful when you want users who are primarily using Teams to connect with other users in the organization who are still using Skype for Business only.
>
> After the users who previously used only Skype for Business start to use Teams, all their chats from other Teams users will arrive in Teams. This switches these users to islands mode. From that point, they must keep running Teams to ensure they stay connected with the other Teams users in the organization.

### Teams-only mode
In this upgraded mode, the Skype for Business client no longer provides basic IM, presence indicators, chat, calling, or meeting capabilities. Users working in upgraded mode must use Teams as their primary communications and collaboration tool.

Users who are ready to use Teams as their primary communications and collaboration tool can be upgraded as Teams-only users.

An upgraded user can only use the Skype for Business client to join existing Skype for Business meetings or meetings on Skype for Business organized by non-upgraded users or external parties. An upgraded user can continue to communicate with other users in the organization who are still using Skype for Business by using the interoperability capabilities between Teams and Skype for Business.

### Skype for Business&ndash;only mode
Users who need to stay in Skype for Business can be configured as Skype for Business&ndash;only users. Users configured in this mode will be prevented from using Teams and will be able to communicate with Teams-only users by using the interoperability capabilities between Teams and Skype for Business.

## Upgrade and coexistence building blocks
To formally prepare your organization for its journey to Teams, you need to start planning for the upgrade scenarios that will eventually let your organization fully embrace Teams as your sole communications and collaboration solution.

When some of your users are ready to use only Teams for their day-to-day communications and collaboration needs, you can start upgrading these users to Teams by enabling Teams-only mode for them.

If it’s not feasible for your whole organization to move to Teams, you can start by fully adopting Teams as a group collaboration solution first while keeping Skype for Business as your organization’s unified communications solution. Another option is to start moving meetings to Teams in addition to introducing Teams group collaboration capabilities, while keeping the rest of the unified communications capabilities in Skype for Business.

![A screenshot of upgrade building blocks from Skype for Business to Teams, consisting of Skype for Business with Teams collaboration&ndash;only mode, Skype for Business with Teams collaboration and meetings mode, Islands mode, Teams-only mode and Skype for Business&ndash;only mode.](media/upgrade_and_coexistence_building_block.png)

The following table compares upgrade and coexistence modes.

|Mode  |Situation  |Short-term goals  |Advantages  |Caveats  |
|---------|---------|---------|---------|---------|
|Skype for Business with Teams collaboration only |Skype for Business deployment with requirements that aren’t yet met by Teams (for example, advanced compliance)<br><br>Long-term need for and/or commitment to Skype for Business|Start Teams adoption quickly, focusing on group collaboration first<br><br> Want to keep all unified communications workloads on Skype for Business for now|No overlapping capabilities between Teams and Skype for Business<br><br>Instant messaging and chat will reside in Skype for Business (tied to calling)<br><br>|
|Skype for Business with Teams collaboration and meetings |Skype for Business deployment with significant use of enterprise voice and requirements that aren’t yet met by Teams calling<br><br>Long-term need for and/or commitment to Skype for Business<br><br>Might be using a third-party meeting service|Start Teams adoption quickly, going beyond group collaboration<br><br>Improve your users’ meetings experience|No overlapping capabilities<br><br>High-value meetings on Teams (WebRTC, cloud meeting recordings, and so on)|Instant messaging and chat will reside in Skype for Business (tied to calling)|
|Islands |Smaller or simpler Skype for Business deployment<br><br>Ability and willingness to manage some short-term complexity to move to Teams more quickly |Go to the full Teams experience as quickly as possible<br><br>Conduct a proof of concept (PoC) of Teams |Simple to operate, no interoperability<br><br>Best Teams experience up-front for all capabilities |Requires good user communication to avoid confusion and to drive usage toward Teams<br><br>Exit strategy requires users to have fully adopted Teams by the time Skype for Business is decommissioned|
|Teams only |Some users need to stay on Skype for Business<br><br>You’re upgrading your Skype for Business Online users to Teams while keeping Skype for Business on-premises users on Skype for Business Server<br><br>You might have already deployed users in islands mode and are ready to retire Skype for Business for groups of users |Reduce variable costs on Skype for Business (on-premises server operations, outsourcing contract, and so on)<br><br>Go to the full Teams experience as quickly as possible, for at least some users|Limits user confusion by providing only one client to work with|Interoperability only supports basic chat and calling between Skype for Business and Teams|
|Skype for Business only |Some users need to stay on Skype for Business<br><br>|Limits user confusion by providing only one client to work with|Continue to meet business requirements that currently can only be met by Skype for Business|Interoperability only supports basic chat and calling between Skype for Business and Teams|

> [!NOTE]
> To help you enable each of the modes described above, we'll publish a Quick Start Guide about how to execute your journey from Skype for Business to Teams when the policies are available at a later time. Stay tuned!

## Upgrade journeys
You can take multiple approaches to upgrading from Skype for Business, either online or on-premises, to Teams:
- In a simple upgrade journey, you first deploy Teams in Skype for Business with Teams collaboration&ndash;only mode as part of evaluation and early adoption, and then implement Teams-only mode with the goal of eventually retiring Skype for Business from the environment for all users in the organization.
- A gradual upgrade journey delivers a specific upgrade mode to a specific group of users (also called a *cohort*), depending on their communications and collaboration requirements. Over time, the entire organization can converge into using Teams only and eventually replace Skype for Business. However, if your organization has compelling business reasons to keep Skype for Business—such as a dependency on a Unified Communications Managed API (UCMA)–based solution that integrates with line-of-business applications, or an ethical wall solution currently available for Skype for Business only—you can upgrade a majority of users to Teams-only mode while retaining Skype for Business users in one of the Skype for Business modes for a portion of your user population.

> [!IMPORTANT]
> For both types of upgrade journey, if your organization is currently a Skype for Business on-premises deployment only, you need to start planning to implement Skype for Business hybrid before upgrading your users to Teams-only mode. This will also help facilitate interoperability with Teams.
> Use [MyAdvisor](https://myadvisor.fasttrack.microsoft.com/) to guide your Skype for Business hybrid implementation.

> [!NOTE]
> Teams-only mode requires that the users who are part of cohorts be homed in Skype for Business Online, and a hybrid relationship between your Skype for Business on-premises deployment and your Skype for Business Online tenant is required to facilitate the upgrade and interoperability between Skype for Business and Teams. The move to Skype for Business Online must be completed for users who are part of the cohorts before they’re upgraded to Teams-only mode. Skype for Business Server 2019, and also a future cumulative update for Skype for Business Server 2015, plan to simplify the mechanics of upgrading on-premises users to Teams by managing the migration to Skype for Business Online and upgrading the users to Teams-only mode in one step.

Whichever journey you choose, Microsoft is here to support you through the upgrade process. From technical requirements to user readiness resources, we’ll share guidance and best practices to help ensure a successful transition from Skype for Business to Teams. Detailed upgrade guidance will be ready soon, so be sure to check back for more information.

### Simple upgrade journey
The simple upgrade journey is illustrated in the following diagram.

![A screenshot of the simple upgrade journey. All users initially use Teams in Skype for Business with Teams collaboration&ndash;only mode, then transition to Teams-only mode, with the end state of the entire organization upgraded to Teams.](media/upgrade_and_coexistence_simple_upgrade_journey.png)

Teams is deployed to all users in the organization and configured in Skype for Business with Teams collaboration&ndash;only mode. When your organization determines that Teams is ready to fulfill all of your communications and collaboration needs, all users are upgraded to Teams-only mode. At that point, Skype for Business can be retired from the environment.

### Gradual upgrade journey
An example of a gradual upgrade journey is illustrated in the following diagram.

![In the gradual upgrade journey, cohorts of users initially use Teams in a variety of upgrade modes, side by side with Skype for Business. Some cohorts transition to Teams-only mode, while one group of users stays with Skype for Business with Teams collaboration and meetings mode.](media/upgrade_and_coexistence_gradual_upgrade_journey.png)

Teams is deployed in the organization by using different upgrade modes for different groups of users, or cohorts. For example, a group of users can be enabled for islands mode, another enabled for Skype for Business with Teams collaboration and meetings mode, while a third group of users might initially be enabled for Skype for Business with Teams collaboration&ndash;only mode.

Over time, groups of users can be upgraded to Teams-only mode, followed by the rest of the organization. Eventually, the entire organization will be ready to retire Skype for Business and use only Teams for communications and collaboration, or—if business requirements dictate that Skype for Business be retained for a specific group—the majority of users in the organization can use Teams only. <br><br>
<table>
<tr><td>![](media/audio_conferencing_image7.png) <br/>Decision points</td><td><ul> Which upgrade journey is suitable to your organization's business requirements?<br><br></ul></td></tr>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td><ul> Identifying your current deployment model, use case scenarios, and key considerations for your organization will inform the journey to Teams that's best suited to your organization.<br><br></ul></td></tr>
</table>

## Upgrade scenarios
Based on the upgrade journeys described earlier in this article, the following prescriptive guidance is provided for specific Skype for Business deployment models that might map to your current deployment model. 

|Deployment model  |Starting point  |Considerations  |Journey  |
|---------|---------|---------|---------|
|Skype for Business Online–only with Calling Plans |Office 365 tenant with Azure AD Connect, SharePoint Online, Exchange Online, and Skype for Business Online<br><br> Phone System with Calling Plans implemented using Skype for Business Online for all users |All users leverage certified headsets<br><br> Meetings require internal and anonymous external VoIP participants<br><br> Messaging includes internal and external contacts |**Messaging roadmap**: Federation feature targeted for release Q2 of 2018<br><br> **Meetings roadmap**: Features you want are already available<br><br> **Calling roadmap**: Features you want are already available<br><br> Building blocks:<ul><li> Skype for Business with Teams collaboration&ndash;only mode</li><li> Teams-only mode</li></ul>|
|Skype for Business Online with Cloud Connector Edition (CCE) |Office 365 tenant with Azure AD Connect, SharePoint Online, Exchange Online, and Skype for Business Online<br><br> Phone System with hybrid voice via CCE implemented by using Skype for Business Online at multiple office locations<br><br> 1,000 users are using messaging and voice workloads only|80% of the user population leverages Phone System with hybrid voice via CCE<br><br> All messaging is contained within the company<br><br> Meetings aren’t currently being used, but there’s interest in enabling Audio Conferencing in the future|**Messaging roadmap**: Features you want are available<br><br> **Meetings roadmap**: Future requirements can be met<br><br> **Calling roadmap**: Direct routing to Teams feature targeted for release Q2 of 2018 <br><br> Building blocks:<ul><li> Skype for Business with Teams collaboration and meetings mode</li><li> Teams-only mode</li></ul> |
|Skype for Business Hybrid |Office 365 tenant with Azure AD Connect, SharePoint Online, Exchange Online, and Skype for Business Online<br><br> Skype for Business Server 2015 deployed and hybrid is configured with Skype for Business Online|A number of users require the ability to record meetings<br><br> There are 10 conference rooms, currently leveraging Skype Room Systems v2<br><br> The organization wants to take advantage of Teams as a collaboration tool as quickly as possible|**Messaging roadmap**: Features you want are available<br><br> **Meetings roadmap**: Cloud meeting recording, meeting room devices feature targeted for release Q2 of 2018<br><br> **Calling roadmap**: Features you want are available<br><br> Building blocks:<ul><li>Skype for Business with Teams collaboration&ndash;only mode</li><li> Skype for Business with Teams collaboration and meetings mode</li><li>Islands mode</li><li>Teams-only mode</li></ul> |
|Skype for Business Server (on-premises) |Office 365 tenant with Azure AD Connect and Exchange Online<br><br> SharePoint and Skype for Business are deployed on-premises|Full enterprise voice feature set (Skype for Business Server 2015) currently in use<br><br> Contact center deployed<br><br> Meetings are conducted with internal and external federated users, using both VoIP and dial-in conferencing<br><br> Messaging with internal and external users|Deploy SharePoint Online<br><br> Configure Skype for Business hybrid (split domain)<br><br>**Messaging roadmap**: Federation feature targeted for release Q2 of 2018<br><br> **Meetings roadmap**: Federated meeting-join, PSTN lobby feature targeted for release Q2 of 2018<br><br> **Calling roadmap**: Feature targeted for release Q4 of 2018 and onward<br><br>Building blocks:<ul><li>Islands mode (pilot)</li><li>Skype for Business with Teams collaboration&ndash;only mode</li><li>Skype for Business with Teams collaboration and meetings mode</li><li>Teams-only mode and Skype for Business&ndash;only mode</li></ul><br>Investigate upgrade to Skype for Business Server 2019|

<table>
<tr><td>![](media/audio_conferencing_image7.png) <br/>Decision points</td><td><ul> Which upgrade scenario is applicable to your organization?<br><br></ul></td></tr>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td><ul> Decide the timeline of your organization's upgrade journey based on messaging, meetings, and calling business requirements.<br><br> Decide the required additional work to complete your upgrade journey.<br><br></ul></td></tr>
</table>

## See also
[Manage Teams during the transition to the new Microsoft Teams and Skype for Business Admin Center](manage-teams-skypeforbusiness-admin-center.md)
