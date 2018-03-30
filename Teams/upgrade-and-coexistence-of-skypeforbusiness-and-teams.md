---
title: Upgrade and Coexistence of Skype for Business and Teams
author: arachmanGitHub
ms.author: MyAdvisor
manager: lehewe
ms.date: 03/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Details of Skype for Business and Teams coexistence options and modes, and upgrade journeys to Teams from Skype for Business with example scenarios.
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---
# Upgrade and coexistence of Skype for Business and Teams

As an existing Skype for Business customer, we understand that a complete transition to Teams may take some time. However, you can begin realizing the value of Teams today, by enabling your users to utilize Teams alongside Skype for Business. Given that there is some overlapping functionality between the two solutions, we recommend exploring the various modes to help determine which path is right for your organization. For example, you may opt to enable all workloads on both solutions without interop. Or, you might decide to manage the user experience, by either gradually introducing Teams capabilities or by targeting groups of users for select capabilities, until your organization is ready to upgrade everyone to Teams.

> [!IMPORTANT]
> As with any deployment, we strongly encourage you to pilot your intended plan with a selected group of users, prior to enabling for your broader organization. Also, introducing new technology can be disruptive for end users. Take time to assess user readiness and implement a communication/training plan to keep users in the know and accelerate their acceptance of Teams. 

## Upgrade and coexistence concepts and terminology
To help guide your decision-making process, familiarize yourself with the following concepts and terminology relevant to upgrading from Skype for Business to Teams.

### Group collaboration–only mode
If your organization’s business requirement is to use Teams solely for group collaboration while keeping unified communications capabilities in Skype for Business—either for the entire organization or some parts of it—you might consider using this mode in your upgrade journey.

In this mode, Teams is configured to support teams and channels-based conversations only, with private chats and calling, and meetings disabled.

### Group collaboration and meetings mode
If your organization needs the capabilities that Teams provides for meetings, but business needs require you to keep enterprise voice capabilities in Skype for Business, you can configure Teams to deliver group collaboration and meetings capabilities to your entire organization (or some parts of it).

Along with using Teams for teams and channels-based conversations in this mode, users start using Teams to schedule and conduct their meetings. Private chats and voice and video calling remain on Skype for Business.

### Islands mode
To facilitate quick adoption of Teams alongside existing Skype for Business deployments, you can deploy Teams independently from Skype for Business in “islands mode.” In this mode, Teams users can immediately use Teams with all its capabilities with other Teams users, while other users can continue using Skype for Business and remain productive with no impact on how they’re using Skype for Business today.

> [!NOTE]
> Islands mode comes with one-way temporary interoperability that allows presence, chat, and calling interoperability from Teams to Skype for Business when the following conditions are met:
> - The Teams user is homed at, and enabled for, Skype for Business Online.
> - The Skype for Business user has never used Teams (or isn’t licensed for Teams).
>
> This mode is helpful when you want users who are primarily using Teams to connect with other users in the organization who are still using Skype for Business only.
>
> After the users who previously used only Skype for Business start to use Teams, all their chats and calls from other Teams users will arrive in Teams. This switches these users to islands mode. From that point, they must keep running Teams to ensure they stay connected with the other Teams users in the organization.

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

![A screenshot of upgrade building blocks from Skype for Business to Teams, consisting of group collaboration-only mode, group collaboration and meetings mode, islands mode, and single-client mode.](media/upgrade_and_coexistence_building_block.png)

The following table compares upgrade and coexistence modes.

|Mode  |Situation  |Short-term goals  |Advantages  |Caveats  |
|---------|---------|---------|---------|---------|
|Group collaboration-only mode |<ul><li>Skype for Business deployment with requirements that aren’t yet met by Teams (for example, advanced compliance)</li><li>Long-term need for and/or commitment to Skype for Business</li></ul> |<ul><li>Start Teams adoption quickly, focusing on group collaboration first</li><li>Want to keep all unified communications workloads on Skype for Business for now</li></ul> |<ul><li>No overlapping capabilities between Teams and Skype for Business</li></ul> |<ul><li>Instant messaging and chat will reside in Skype for Business (tied to calling)</li></ul> |
|Group collaboration and meetings mode |<ul><li>Skype for Business deployment with significant use of enterprise voice and requirements that aren’t yet met by Teams calling</li><li>Long term need for and/or commitment to Skype for Business</li><li>Might be using a third-party meeting service</li></ul> |<ul><li>Start Teams adoption quickly, going beyond group collaboration</li><li>Improve your users’ meetings experience</li></ul> |<ul><li>No overlapping capabilities</li><li>High-value meetings on Teams (WebRTC, cloud meeting recordings, and so on)</li></ul> |<ul><li>Instant messaging and chat will reside in Skype for Business (tied to calling)</li></ul> |
|Islands mode |<ul><li>Smaller or simpler Skype for Business deployment</li><li>Ability and willingness to manage some short-term complexity to move to Teams more quickly</li></ul> |<ul><li>Go to the full Teams experience as quickly as possible</li><li>Conduct a proof of concept (PoC) of Teams</li></ul> |<ul><li>Simple to operate, no interoperability</li><li>Best Teams experience up-front for all capabilities</li></ul> |<ul><li>Requires good user communication to avoid confusion and to drive usage toward Teams</li><li>Exit strategy requires users to have fully adopted Teams by the time Skype for Business is decommissioned</li></ul> |
|Single-client mode |<ul><li>Some users need to stay on Skype for Business</li><li>You’re upgrading your Skype for Business Online users to Teams while keeping Skype for Business on-premises users on Skype for Business Server</li><li>You might have already deployed users in islands mode and are ready to retire Skype for Business for cohorts of users</li></ul> |<ul><li>Reduce variable costs on Skype for Business (on-premises server operations, outsourcing contract, and so on)</li><li>Go to the full Teams experience as quickly as possible, for at least some users</li></ul>|<ul><li>Limits user confusion by providing only one client to work with</li><li>Provides a rapid path to Teams</li></ul>|<ul><li>Interoperability only supports basic chat and calling between Skype for Business and Teams</li></ul>|

To learn more about enabling each of the modes described above, review [Quick start guide: Configuring Teams upgrade and coexistence](https://docs.microsoft.com/MicrosoftTeams/configuring-teams-upgrade-and-coexistence-quickstartguide) (COMING SOON!)

## Upgrade journeys
You can take multiple approaches to upgrading from Skype for Business, either online or on-premises, to Teams:
- In a simple upgrade journey, you first deploy Teams in group collaboration-only mode as part of evaluation and early adoption, and then implement Teams-only single-client mode with the goal of eventually retiring Skype for Business from the environment for all users in the organization.
- A gradual upgrade journey delivers a specific upgrade mode to a specific group of users (also called a *cohort*), depending on their communications and collaboration requirements. Over time, the entire organization can converge into single-client mode and eventually remove Skype for Business. However, if your organization has compelling business reasons to keep Skype for Business—such as dependency on a Unified Communications Managed API (UCMA)–based solution that integrates with line-of-business applications, or an ethical wall solution currently available for Skype for Business only—you can upgrade a majority of users to single-client mode while retaining Skype for Business for a portion of your user population.

> [!IMPORTANT]
> For both types of upgrade journey, if your organization is currently a Skype for Business on-premises deployment only, you need to start planning to implement Skype for Business hybrid before upgrading your users to single-client mode. This will also help facilitate interoperability with Teams.
> You can leverage [MyAdvisor](https://myadvisor.fasttrack.microsoft.com/) to guide your Skype for Business hybrid implementation.

> [!NOTE]
> The Teams-only single-client upgrade mode requires that the users who are part of cohorts be homed in Skype for Business Online, and a hybrid relationship between your Skype for Business on-premises deployment and your Skype for Business Online tenant is required to facilitate the upgrade and interoperability between Skype for Business and Teams. The move to Skype for Business Online must be completed for users who are part of the cohorts before they’re upgraded to single-client mode. Skype for Business Server 2019, and also a future cumulative update for Skype for Business Server 2015, plan to simplify the mechanics of upgrading on-premises users to Teams by managing the migration to Skype for Business Online and upgrading the users to single-client mode in one step.

### Simple upgrade journey
The simple upgrade journey is illustrated in the following diagram.

![A screenshot of the simple upgrade journey. All users initially use Teams in group collaboration-only mode side-by-side with Skype for Business, then transition to Teams-only single client mode, with the end state of the entire organization upgraded to Teams.](media/upgrade_and_coexistence_simple_upgrade_journey.png)

Teams is deployed to all users in the organization and configured in group collaboration-only mode. When your organization considers that Teams is ready to fulfil all communications and collaboration needs, all users are upgraded to Teams-only single-client mode. Skype for Business can be retired from the environment.

### Gradual upgrade journey
An example of a gradual upgrade journey is illustrated in the following diagram.

![[placeholder for image]](media/upgrade_and_coexistence_gradual_upgrade_journey.png)

Teams is deployed in the organization by using different upgrade modes for different groups of users, or cohorts. For example, a group of users can be enabled for islands mode, another enabled for group collaboration and meetings, while a third group of users might initially be enabled for group collaboration only.

Over time, groups of users can be upgraded to Teams-only single-client mode, followed by the rest of the organization. Eventually, the entire organization will be ready to retire Skype for Business and use only Teams for communications and collaboration, or—if business requirements dictate that Skype for Business be retained for a specific group—the majority of users in the organization can use Teams only.

<table>
<tr><td>![](media/audio_conferencing_image7.png) <br/>Decision points</td><td><ul><li>Which upgrade journey is suitable to your organization's business requirements?</li></ul></td></tr>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td><ul><li>Identifying your current deployment model and use case scenarios and key considerations for your organization will inform the journey to Teams best suited to your organization.</li></ul></td></tr>
</table>

## Upgrade scenarios
Based on the upgrade journeys described earlier in this article, the following prescriptive guidance is provided for specific Skype for Business deployment models that might map to your current deployment model.

|Deployment model  |Starting point  |Considerations  |Journey  |
|---------|---------|---------|---------|
|Skype for Business Online–only with Calling Plans |<ul><li>Office 365 tenant with Azure AD Connect, SharePoint Online, Exchange Online, and Skype for Business Online</li><li>Phone System with Calling Plans implemented using Skype for Business Online for all users</li></ul> |<ul><li>All users leverage certified headsets</li><li>Meetings require internal and anonymous external VoIP participants</li><li>Messaging includes internal and external contacts, including Skype (consumer)</li></ul> |<ul><li>Roadmap:<ul><li>**Messaging**: Federation feature targeted for release Q1 of 2018</li><li>**Meetings**: features you want are already available</li><li>**Calling**: Skype (consumer) calling feature targeted for release Q2 of 2018 (Skype [consumer] calling)</li></ul></li><li>Building blocks:<ul><li>Group collaboration-only mode</li><li>Teams-only single-client mode</li></ul></li></ul> |
|Skype for Business Online with Cloud Connector Edition (CCE) |<ul><li>Office 365 tenant with Azure AD Connect, SharePoint Online, Exchange Online, and Skype for Business Online</li><li>Phone System with hybrid voice via CCE implemented by using Skype for Business Online at multiple office locations</li><li>1,000 users are using messaging and voice workloads only</li></ul> |<ul><li>80% of the user population leverages Phone System with hybrid voice via CCE</li><li>All messaging is contained within the company</li><li>Meetings aren’t currently being used, but there’s interest in enabling Audio Conferencing in the future</li></ul> |<ul><li>Roadmap:<ul><li>**Messaging**: features you want are available</li><li>**Meetings**: future requirements can be met</li><li>**Calling**: Direct routing to Teams feature targeted for release Q2 of 2018 </li></ul></li><li>Building blocks:<ul><li>Group collaboration and meetings mode</li><li>Teams-only single-client mode</li></ul></li></ul> |
|Skype for Business Hybrid |<ul><li>Office 365 tenant with Azure AD Connect, SharePoint Online, Exchange Online, and Skype for Business Online</li><li>Skype for Business Server 2015 deployed and hybrid is configured with Skype for Business Online</li></ul> |<ul><li>A number of users require the ability to record meetings</li><li>There are 10 conference rooms, currently leveraging Skype Room Systems v2</li><li>The organization wants to take advantage of Teams as a collaboration tool as quickly as possible</li></ul> |<ul><li>Roadmap:<ul><li>**Messaging**: features you want are available</li><li>**Meetings**: Cloud meeting recording, meeting room devices feature targeted for release Q2 of 2018</li><li>**Calling**: features you want are available</li></ul></li><li>Building blocks:<ul><li>Group collaboration–only mode</li><li>Group collaboration and meetings mode</li><li>Islands mode</li><li>Teams-only single-client mode</li></ul></li></ul> |
|Skype for Business Server (on-premises) |<ul><li>Office 365 tenant with Azure AD Connect and Exchange Online</li><li>SharePoint and Skype for Business are deployed on-premises</li></ul> |<ul><li>Full enterprise voice feature set (Skype for Business Server 2015) currently in use</li><li>Contact center deployed</li><li>Meetings are conducted with internal and external federated users, using both VoIP and dial-in conferencing</li><li>Messaging with internal and external users, including Skype (consumer)</li></ul> |<ul><li>Deploy SharePoint Online</li><li>Configure Skype for Business hybrid (split domain)</li><li>Roadmap:<ul><li>**Messaging**:Federation feature targeted for release Q1 of 2018</li><li>**Meetings**: Federated meeting-join, PSTN lobby feature targeted for release Q2 of 2018</li><li>**Calling**: feature targeted for release Q4 of 2018 and onward</li></ul></li><li>Building blocks:<ul><li>Islands mode (pilot)</li><li>Group collaboration–only mode</li><li>Group collaboration and meetings mode</li><li>Single-client modes (Teams-only and Skype for Business-only)</li></ul></li><li>Investigate upgrade to Skype for Business Server 2019</li></ul> |

<table>
<tr><td>![](media/audio_conferencing_image7.png) <br/>Decision points</td><td><ul><li>Which upgrade scenario is applicable to your organization?</li></ul></td></tr>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td><ul><li>Decide the timeline of your organization's upgrade journey based on messaging, meetings, and calling business requirements.</li><li>Decide the required additional work to complete your upgrade journey.</li></ul></td></tr>
</table>

## See also

[Quick start guide: Configuring Teams upgrade and coexistence](https://docs.microsoft.com/MicrosoftTeams/configuring-teams-upgrade-and-coexistence-quickstartguide) (COMING SOON!)