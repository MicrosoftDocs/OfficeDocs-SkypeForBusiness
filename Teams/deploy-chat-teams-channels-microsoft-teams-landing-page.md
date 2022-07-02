---
title: Chat, teams, channels, & apps in Microsoft Teams
ms.reviewer: 
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: article
ms.service: msteams
ms.subservice: teams-chat
ms.custom: intro-get-started
audience: admin
search.appverid: MET150
description: Contains step-by-step guidance to configure Teams settings for chat, teams, apps, and channels in Microsoft Teams.
ms.localizationpriority: high
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.dashboard.helparticle.quickstartteamsadmin
appliesto: 
  - Microsoft Teams
  - seo-marvel-apr2020
  - seo-marvel-may2020
---

# Chat, teams, channels, & apps in Microsoft Teams

Teams provides a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups, starting with the core set of [changes you're more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

To get started, watch our short Teams chat, teams, and channels video (4:30 minutes):

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE476Yj]

You can use [Advisor for Teams](use-advisor-teams-roll-out.md) to help you roll out Microsoft Teams. Advisor for Teams walks you through your Teams rollout. It assesses your Microsoft 365 environment and identifies the most common configurations that you may need to update or modify before you can successfully roll out Teams.

> [!TIP]
> We recommend that you include our featured apps -- such as Planner -- in your initial Teams rollout. Add other [apps, bots, and connectors](deploy-apps-microsoft-teams-landing-page.md) as you drive Teams adoption.

 > [!Note]
 > For details about Teams features on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Chat deployment prerequisites

Before you roll out Teams across your organization, take time to confirm that your environment is ready for Teams. Review [Prepare your organization's network for Teams](prepare-network.md) and make any required changes to your environment.

|Ask yourself|Action |
|------------|-------|
|Is my organization ready to roll out Teams?|To answer this question, see: <ul><li>[Prepare your organization's network for Teams](prepare-network.md)</li><li>[URLs and IP address ranges](office-365-urls-ip-address-ranges.md)</li><li>[Plan for Microsoft 365 Groups when creating teams](plan-office-365-groups.md)</li></ul>|

## Core deployment decisions

These are the chat, teams, and channels settings that most organizations want to change (if the default settings don't work for them).

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators.

| Ask yourself | Action |
|--------------|--------|
|Who will be assigned the Teams Communications Administrator role?|To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).|
|Who will be assigned the Teams Communications Support Engineer role?|To assign admin roles, see [Assign administrator and non-administrator roles to users with Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).|
|Who will be assigned the Teams Communications Support Specialist role?||

### Teams owners and members

In addition to administrator roles, Teams lets you assign owner and member user roles, and selectively give them moderator capabilities (if moderation has been set up) to control who can perform certain actions within a channel. Moderation allows you to control who can start new posts in a channel, add and remove team members as moderators, and control whether team members can reply to existing channel messages.

|Ask yourself|Action |
|------------|-------|
|Who should be assigned to each role? | To compare the capabilities of each role, see [Assign team owners, moderators, and members in Microsoft Teams](assign-roles-permissions.md).
|How do I assign a user role? | To assign or change a role, see [Assign a user role](assign-roles-permissions.md#assign-a-user-role).
|Do I need to control who can post and reply in a channel? | To configure moderation, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

### Messaging policies

Messaging policies control which chat and channel messaging features are available to users in Teams. For example, who can edit and delete sent messages, who can use chat, who can use memes in conversations, and more. By default, users are assigned the global messaging policy and all features are **On**. You can use the default global policy or create one or more custom messaging policies for people in your organization. 

|Ask yourself|Action |
|------------|-------|
|Will I customize the global messaging policy?|For information about using the Microsoft Teams admin center to change the global messaging policy or add a new policy, see [Manage messaging policies in Teams](messaging-policies-in-teams.md).|
|Do I require multiple messaging policies?|To create and assign a messaging policy in PowerShell, see [PowerShell script sample - Create and assign a messaging policy](scripts/powershell-script-teams-messaging-policy-edu.md).|
|How will I determine which groups of users get which messaging policy?|To learn about the CsTeamsMessagingPolicy cmdlets, see [Set-CsTeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy).|

### External access

External access (federation) lets your users communicate with people outside of your organization via chat. By turning this on and adding domains to the allowed list, your users can communicate with users in other domains and organizations. External access is turned on by default.

|Ask yourself|Action |
|------------|-------|
|<ul><li>Will I turn off external access for my organization?</li><li>If enabled, will I limit which domains my organization can communicate with?</li></ul> |<br>To turn external access on or off, see [Plan for external access](manage-external-access.md#plan-for-external-access).|

### Guest access

Guest access in Teams lets individuals outside your organization access teams and channels. You can use the guest access settings to control which features guests can or can't use. Guest access is turned on by default. To learn more, see [Guest access in Teams](./guest-access.md).

> [!NOTE]
> For more on external access and guest access see here - [Communicate with users from other organizations in Microsoft Teams](communicate-with-users-from-other-organizations.md)


|Ask yourself|Action |
|------------|-------|
|Will I turn off guest access for my organization?|To turn guest access on or off, see [Turn on or off guest access in Teams](set-up-guests.md).|
|If enabled, will I customize the features available to guests in my organization?|To customize guest access feature availability, see [Authorize guest access in Teams](teams-dependencies.md).|

### Private channels

Private channels allow a subset of team members to collaborate in a private space that other team members can't see or access. Anyone, including guests, can be added as a member of a private channel as long as they are already members of the team.

|Ask yourself|Action |
|------------|-------|
|Do I want to allow team owners and members to create private channels?|To set private channels policy for your organization, see [Manage channel policies in Microsoft Teams](teams-policies.md)|

### Shared channels

Shared channels allow you to add people who are not members of a team to a channel. This includes people who are outside your organization. Shared channels provide advantages over guest access in that people outside your organization no not require a guest account in your directory.

|Ask yourself|Action |
|------------|-------|
|When do I use shared channels versus guest access?|See [Shared channels in Microsoft Teams](shared-channels.md).|
|<ul><li>Will I allow team owners to create shared channels?</li><li>Will I allow team owners to share channels with people outside the organization?</li><li>Will I allow users to participate in shared channels that are outside the organization?</li></ul> |<br>To set shared channels policy for your organization, see [Manage channel policies in Microsoft Teams](teams-policies.md).|

### Teams settings

Teams settings let you set up your teams for features such as email integration, cloud storage options, organization tab, meeting room device setup, and search scope. When you make changes to these settings, they apply to all the teams in your organization. To learn more, see [Teams settings](enable-features-office-365.md#teams-settings).

|Ask yourself|Action |
|------------|-------|
|Will I customize Teams settings for my organization? | To learn about Teams settings and how to customize them, see [Teams settings](enable-features-office-365.md#teams-settings).|

### Teams clients

Teams supports a number of clients from web to desktop to mobile, and the default configuration lets users choose whichever clients they want. To learn more, see [Get clients for Teams](get-clients.md).

|Ask yourself|Action |
|------------|-------|
|Will I customize Teams client availability for my organization?|Check out [Hardware requirements for the Teams app](hardware-requirements-for-the-teams-app.md). |
|Will I customize Teams client settings for my organization?|Learn how to [Install Teams using MSI](msi-deployment.md).|

### Teams usage reporting

The Global Admin, Teams Service Admin, and Reports Readers roles can view Teams usage reports. To learn more, see the [Microsoft 365 usage analytics](/microsoft-365/admin/usage-analytics/usage-analytics).

|Ask yourself|Action |
|------------|-------|
|<br> Who needs to see the Teams usage reports, and do they have the correct role to view them? |<ul><li>If the user isn't an admin, [assign the Reports reader role](teams-activity-reports.md#reports-reader-role).</li><li>See [Roles and permissions](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) and [View and assign roles](/azure/active-directory/users-groups-roles/directory-manage-roles-portal) to learn how to assign admin roles in Azure Active Directory.|

### Teams default apps 

Teams provides a number of first-party (Microsoft provided) and third-party apps to engage users, support productivity, and integrate commonly used business services into Teams. Get apps from the Teams Store. Apps are turned on by default in Teams. 

To learn more about rolling out and managing apps in Teams, see our in-depth [Apps, bots, & connectors](deploy-apps-microsoft-teams-landing-page.md) guidance.

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Teams licensing

Teams is provided as part of many Microsoft 365 licenses.

|Ask yourself|Action |
|------------|-------|
|Do my users have the licenses they need in order to use all the Teams features I want to roll out? | To learn about licensing requirements, read [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description).|

### Exchange and SharePoint interoperability

For the full Teams experience, every user should be enabled for Exchange, SharePoint, and Microsoft 365 group creation. The following articles outline information related to Exchange mailboxes hosted in various environments, how Exchange and Teams interact, and similar considerations for SharePoint and OneDrive.

|Ask yourself|Action |
|------------|-------|
| Will I be able to deploy the Teams features that I require with the current Exchange and SharePoint deployments? |For more information about Exchange and SharePoint in Teams, see:<ul><li> [How Exchange and Teams interact](exchange-teams-interact.md)</li><li>[How SharePoint Online and OneDrive interact with Teams](sharepoint-onedrive-interact.md)|

### Teams limits and specifications 

When planning an enterprise deployment of Teams, you should take into account any relevant limitations and specifications, such as the maximum number of members in a team, the maximum number of teams a user can create, and so on.

|Ask yourself|Action |
|------------|-------|
| What limits am I likely to hit with my Teams rollout? | To learn more, read [Limits and specifications for Teams](limits-specifications-teams.md). |

### URLs and ports

Organizations that maintain fine-grained control of their internet traffic should read [URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges) for an up-to-date list of the URLs, IP addresses, ports, and protocols that must be correctly configured for Teams. Microsoft is continuously improving the Microsoft 365 services and adding new functionality, which means the required ports, URLs, and IP addresses may change over time. We recommend that you subscribe via RSS to receive notifications when this information is updated or changed. At a minimum, make sure you've opened the ports listed above in [Chat deployment prerequisites](#chat-deployment-prerequisites).

|Ask yourself|Action |
|------------|-------|
| Do I require internet access rules to enable users to use Teams, or is it sufficient to open the minimum required ports? | To learn more, see [URLs and IP address ranges](office-365-urls-ip-address-ranges.md).|

### Governance (naming conventions, who can create teams)

Your organization might require that you implement controls on how teams are named and classified, who can create teams, and team expiration, retention, and archiving. This is called governance. You can use Azure Active Directory (Azure AD) to configure each of these areas.


| Ask yourself | Action |
|--------------|--------|
|Will I need to implement controls on who can create teams?| Read [Plan for governance in Teams](plan-teams-governance.md).|
|Will I need to implement controls on how teams are named?|Read [Enforce a naming policy for Microsoft 365 Groups in Azure AD](/azure/active-directory/users-groups-roles/groups-naming-policy).|

### Teams application policy (side-rail control)

A pinned app shows up in the side rail in Teams. By creating Teams application policies, you can preconfigure sets of pinned Teams apps to personalize Teams for select groups of users. By default, the **Allow external apps in Microsoft Teams** setting is turned on.

| Ask yourself | Action |
|--------------|--------|
|Should I create preconfigured sets of pinned Teams applications? | Read [Admin settings for apps in Teams](admin-settings.md).|
|How will I decide which groups receive these app groupings?|Read [Teams apps permissions and considerations](app-permissions.md).|

### Archiving and compliance 

Your organization might require that you implement controls on how teams are archived and the types of data that are held in certain types of teams. Read [Overview of security and compliance in Teams](security-compliance-overview.md) to learn which Teams settings are turned on by default.

| Ask yourself | Action |
|--------------|--------|
|Will I need to configure team retention?|To set up retention policies, see [Set up Teams retention policies](retention-policies.md).|
|Will I need to configure team archiving?|To archive or restore a team, see [Archive or restore a team](https://support.office.com/article/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7).|
|Will I need to configure additional compliance settings?|For more information about security and compliance, see [Overview of security and compliance in Teams](security-compliance-overview.md).|

### Conditional access 

Teams relies heavily on Exchange and SharePoint for core productivity scenarios, including meetings, calendars, interop chats, and file sharing. Conditional access policies that are set for these cloud apps apply to Teams when a user signs in directly to Teams, on any client. Conditional access policies that are set for the Teams cloud app control aspects such as whether users can access Teams services from certain networks.

| Ask yourself | Action |
|--------------|--------|
|<br>Will I need to configure conditional access for Teams?|<ul><li>To understand how access policies work, see [How do conditional access policies work for Teams?](security-compliance-overview.md#how-conditional-access-policies-work-for-teams)</li><li>To set up multi-factor authentication (MFA) for Teams, see:<ul><li>[Quickstart: Require MFA for specific apps with Azure Active Directory conditional access](/azure/active-directory/conditional-access/app-based-mfa)</li><li>[Azure Active Directory conditional access settings reference](/azure/active-directory/conditional-access/technical-reference)</li></ul></ul>|

### Education (EDU) 

IT pros working in education can take advantage of Teams for Education, which comes with a number of capabilities that have been tailored to meet education-specific scenarios for students, faculty, and the wider business.

| Ask yourself | Action |
|--------------|--------|
|Will I use EDU-specific Teams templates? |To learn more about Teams for Education, see [Microsoft Education governance FAQ for admins](plan-teams-governance-edu.md).|
|Will I deploy scoped search?|To set up Teams for EDU, see [Quickstart - Teams for Education admins](teams-quick-start-edu.yml).|
|Will I integrate Teams with the School Data Sync service to provision user accounts?|[Teams resources for Education admins](resources-teams-edu.md)|

### Government - GCC considerations

The use of Office 365 for Government - GCC (Government Community Cloud) is appropriate to meet the requirements of IT pros who are driving deployments of Office 365 in US federal, state, local, tribal, or territorial government entities or other entities that handle data that's subject to government regulations and requirements.

| Ask yourself | Action |
|--------------|--------|
| Will I need to deploy Teams in an Office 365 for Government – GCC environment? | For deployment considerations, see [Plan for Office 365 Government - GCC deployments](plan-for-government-gcc.md).|

## Next steps
- [Drive adoption](adopt-microsoft-teams-landing-page.md) of chat, teams, channels, & apps.
- Include featured apps - such as Planner - in your initial Teams rollout. Add other [apps, bots, & connectors](deploy-apps-microsoft-teams-landing-page.md) as you drive Teams adoption.
- [Roll out meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md)
- [Roll out cloud voice](cloud-voice-landing-page.md)
