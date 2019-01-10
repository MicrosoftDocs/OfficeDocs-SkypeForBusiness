---
title: Deploy chat, teams, channels, and apps in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/07/2019
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Step-by-step guidance to rolling out chat, teams, and channels in Microsoft Teams
localization_priority: Normal
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---

# Deploy chat, teams, channels, and apps in Microsoft Teams

Teams provides a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether you need to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups starting with the core set of [changes you are more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

## Deployment prerequisites 

Before you deploy Teams across your organization, take time to review and confirm that your environment is ready to provide users with the best
possible Teams experience. Review the following information and make any required changes to your environment.

- To get the best experience on Teams, your organization must have deployed [Exchange Online and SharePoint Online](#exchange-and-sharepoint-interoperability), and you must have a verified domain for O365 (such as *contoso.com*).

- To scale chat, teams, and channels across your organization, make sure that all user locations have internet access to connect to the Office 365 Services. At a minimum you should make sure that the following common ports are open to the internet from your users’ locations:

    - Open TCP ports 80 and 443 for outgoing traffic from clients that will use Teams.

    - Open UDP ports 3478 through 3481 for outgoing traffic from clients that will use Teams.

|Ask yourself|Action |
|------------|-------|
Is my organization ready for Teams deployment?|To determine readiness, see: <ul><li> e[Check your environment's readiness for Microsoft Teams](environment-readiness.md)</li><li>[Prepare your organization's network for Microsoft Teams](prepare-network.md)</li><li>[Office 365 URLs and IP address ranges](office-365-urls-ip-address-ranges.md)</li><li>[Plan for Office 365 Groups when creating teams in Microsoft Teams](plan-office-365-groups.md)|
|||

## Core deployment decisions

These are the settings that most organizations want to change (if the Teams default settings don't work for the organization).

### Teams administrators

Teams provides a set of custom administrator roles for managing different aspects of Teams in your organization. The Teams Service Administrator manages the Teams service and creates and manages Office 365 Groups. See [Teams roles and capabilities](using-admin-roles.md#teams-roles-and-capabilities).

|Ask yourself|Action |
|------------|-------|
| Who will be assigned the Teams Service Administrator role? | To assign the Teams Service Admin role, see [Assign administrator and non-administrator roles to users with Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).|
|||

### Messaging policies

Messaging policies control what chat and channel messaging features are available to users in Teams. For example, who can edit and delete sent messages, chat availability, who can use memes in conversations, and more. By default, users are assigned the global messaging policy and all features are **On**. You can use the default global policy or create one or more custom messaging policies for people in your organization. 

|Ask yourself|Action |
|------------|-------|
|<ul><li>Will I customize the global messaging policy?</li><li>Do I require multiple messaging policies?</li><li>How will I determine which groups of users get which messaging policy?</li></ul>|<ul><li> To change or add a policy, see [What are Messaging policies in Teams?](https://docs.microsoft.com/microsoftteams/messaging-policies-in-teams)</li><li>To create and assign a messaging policy in PowerShell, see [PowerShell script sample - Create and assign a messaging policy](https://docs.microsoft.com/microsoftteams/scripts/powershell-script-teams-messaging-policy-edu).</li></ul>|
|||

### External access

External access (formerly known as federation) lets your Teams and Skype for Business users communicate with users who are outside of your organization. By turning this on and adding domains to the allowed list, your users can communicate with other users in other domains and organizations. External access is not configured by default.

|Ask yourself|Action |
|------------|-------|
|<ul><li>Will I enable external access for my organization?</li><li>If enabled, will I limit which domains my organization can communicate with?</li></ul> |To enable external access, see  [Let your Teams users chat and communicate with users in another Teams organization](https://docs.microsoft.com/MicrosoftTeams/let-your-teams-users-communicate-with-other-people).|
|||

### Guest access

Guest access in Teams lets people outside your organization access teams and channels. You can use the guest access settings to control which features guest users can or can’t use. Guest access is turned off by default. For more information see [Guest Access in Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access).

|Ask yourself|Action |
|------------|-------|
|<ul><li>Will I enable guest access for my organization?</li><li>If enabled, will I customize the features available to guests in my organization?</li></ul>|<ul><li>To enable guest access, see [Turn on or off guest access in Teams](set-up-guests.md).</li><li>To customize the guest access features available, see [Authorize guest access in Teams](teams-dependencies.md).</li></ul>|
|||

### Teams settings

Teams settings let you set up your teams for features such as email integration, cloud storage options, and device set up. When you make changes to the settings here, they will be applied to all the teams in your organization. For more information, see [Teams settings](enable-features-office-365.md#teams-settings). <<Need default settings>>

|Ask yourself|Action |
|------------|-------|
|Will I customize Teams settings for my organization? | To customize Teams settings, see [Teams settings](enable-features-office-365.md#teams-settings).|
|||

### Teams clients

Teams supports a number of clients from web to desktop to mobile, and the default configuration lets users choose whichever client they want to. For more information, see [Get clients for Teams](get-clients.md).

<<There isn't anything to configure here - consider deleting this section.>>

|Ask yourself|Action |
|------------|-------|
|<ul><li>Will I customize Teams client availability for my organization?</li><li>Will I customize Teams client settings for my organization?</li></ul>| |
|||

### Teams usage reporting

The Global Admin in Office 365, Teams Service Admin, and Reports Readers roles can view Teams usage reports. For more information, see the [Microsoft 365 usage analytics articles](https://docs.microsoft.com/en-gb/office365/admin/usage-analytics/usage-analytics?redirectSourcePath=%252farticle%252fMicrosoft-365-usage-analytics-77ff780d-ab19-4553-adea-09cb65ad0f1f&view=o365-worldwide).

|Ask yourself|Action |
|------------|-------|
| Will I grant the Reports Reader role to my adoption team members so they can track usage? | To assign the Reports Reader role, see [Administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).|
|||

### Teams default apps 

Teams provides a number of Microsoft-provided and third-party apps via the Teams Store to engage your users and provide additional productivity capabilities and integration of commonly used business services into Teams. The default configuration is that the these apps are enabled for users to explore and use; for example, users can use the Planner app to build and manage team tasks. The out-of-the-box configuration enables the teams default apps and external apps that have been submitted via the [Teams Store approval process.](https://docs.microsoft.com/en-us/microsoftteams/platform/publishing/apps-publish#microsoft-teams-app-approval-process),


|Ask yourself|Action |
|------------|-------|
| Will I change the default teams apps? | To change the defaults, see [Admin settings for apps in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/admin-settings).|
|||


## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Teams licensing

Teams is provided as a component of a number of Office 365 licensing scenarios. To learn more about Teams licensing, see [Office 365 licensing for Microsoft Teams](office-365-licensing.md).

|Ask yourself|Action |
|------------|-------|
|Are my users correctly licensed for all the Teams capabilities that I want to deploy? | To determine licensing requiremengs, see [Office 365 licensing for Microsoft Teams](office-365-licensing.md).|
|||

### Exchange and SharePoint interoperability 

For the full Microsoft Teams experience, every user should be enabled for Exchange Online, SharePoint Online, and Office 365 Group creation. The following articles outline information related to Exchange mailboxes hosted in various environments, how Exchange and Microsoft Team interact, and similar considerations for SharePoint and OneDrive for Business. 

|Ask yourself|Action |
|------------|-------|
| Will I be able to deploy the Teams features that I require with the current Exchange and SharePoint deployments? |For more information about Exchange and SharePoint interop with Teams, see:<ul><li> [How Exchange and Microsoft Teams interact](exchange-teams-interact.md)</li><li>[How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md)|
|||

### Teams limits and specifications 

When planning an enterprise deployment of Teams, you should take into account any relevant limitations and specifications, such as the maximum number of members in a team, the maximum number of teams a user can create, and so on.

|Ask yourself|Action |
|------------|-------|
| Are there any limits that I am likely to hit with my deployment? | For limit details, see [Limits and specifications for Microsoft Teams](limits-specifications-teams.md). |
|||

### Office 365 URLs and ports

Organisations that maintain fine grained control of their internet traffic should go to the [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) for a detailed and up-to-date list of the URLs, IP addresses, ports, and protocols that must be correctly configured for Teams. Microsoft is continuously improving the Office 365 service and adding new functionality, which means the required ports, URLs, and IP addresses may change over time. We recommend that you subscribe via RSS to receive notifications when this information is updated or changed.

|Ask yourself|Action |
|------------|-------|
| Do I require internet access rules to enable users to use Teams or can I simply open TCP ports 80 and 443 outgoing from clients that will use Teams and open UDP ports 3478 through 3481 outgoing from clients that will use Teams? | For details, see [Office 365 URLs and IP address ranges](office-365-urls-ip-address-ranges.md).|
|||

### Governance (naming conventions, who can create teams)

Your organization might require that you implement controls on how teams are named and classified, who can create teams, and team expiration, retention, and archiving. You can use Azure Active Directory (Azure AD) to configure each of these areas.


| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I need to implement controls on how teams are named?</li><li>Will I need to implement controls on who can create teams?</li><li>Will I need to configure team expiration and retention?</li></ul>| To plan and implement governance controls, see:<ul><li> [Plan for governance in Teams](https://docs.microsoft.com/en-us/microsoftteams/plan-teams-governance)</li><li>[Enforce a naming policy for Office 365 groups in Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-naming-policy)</li><li>[Set up Office 365 groups expiration](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-lifecycle)</li></ul>|
|||

### Teams application policy (side rail control)

The Teams application policy lets you pre-configure sets of pinned Teams applications for groups of users to provide a more personal and targeted experience. By default, the **Allow external apps in Microsoft Teams** setting is turned on.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Should I create pre-configured sets of pinned Teams applications?</li><li>How will I decide which groups receive these app groupings?</li></ul> | To learn more about admin settings in Teams, see:<ul><li>[Admin settings for apps in Microsoft Teams](admin-settings.md)</li><li>[Microsoft Teams apps permissions and considerations](app-permissions.md)</li></ul>|
|||

### Archiving and compliance 

Your organization might require that you implement controls on how teams are archived and the types of data that are held in certain types of teams. See [Overview of security and compliance in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/security-compliance-overview) to learn which settings are enabled by default.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I need to configure team retention?</li><li>Will I need to configure team archiving?</li><li>Will I need to configure additional compliance settings?</li></ul>|<ul><li> To set up retention policies, see [Set up Teams retention policies](retention-policies.md).</li><li>To archive or restore a team, see [Archive or restore a team](https://support.office.com/article/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7).</li><li>For more information about security and compliance, see [Overview of security and compliance in Microsoft Teams](security-compliance-overview.md).</li></ul> |
|||

### Conditional access 

Microsoft Teams relies heavily on Exchange Online, SharePoint Online, and Skype for Business Online for core productivity scenarios, like meetings, calendars,interop chats, and file sharing. Conditional access policies that are set for these cloud apps apply to Microsoft Teams when a user directly signs in to Microsoft Teams - on any client. Conditional access policies that are set for the Microsoft Teams cloud app apply to Microsoft Teams when a user signs in and can control aspects such as whether users can access Teams services from certain networks.

| Ask yourself | Action |
|--------------|--------|
|Will I need to configure conditional access for Teams?|<ul><li>To understand how access policies work, see [How do conditional access policies work for Teams?](security-compliance-overview.md#how-do-conditional-access-policies-work-for-teams).</li><li>To set up multifactor authentication (MFA) for Teams, see:<ul><li>[Quickstart: Require MFA for specific apps with Azure Active Directory conditional access](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/app-based-mfa)</li><li>[Azure Active Directory conditional access settings reference](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/technical-reference)</li></ul></ul>|
|||


### Education (EDU) 

IT Pros working in education can take advantage of Teams for Education, which comes with a number of capabilities that have been tailored to meet education-specific scenarios for students, faculty, and the wider business.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I use EDU-specific Teams templates?</li><li>Will I deploy scoped search?</li><li>Will I integrate Teams with the School Data Sync service to provision user accounts?</li></ul> |<ul><li> To learn more about Teams EDU, see [Microsoft Education governance FAQ for admins](plan-teams-governance-edu.md).</li><li>To set up Teams EDU, see [Quickstart - Microsoft Teams for Education admins](teams-quick-start-edu.md).|
|||

### Government - GCC considerations

The use of Microsoft 365 Government - GCC is appropriate to meet the requirements of IT pros who are driving deployments of Office 365 in US federal, state, local, tribal, or territorial government entities or other entities that handle data that’s subject to government regulations and requirements.

| Ask yourself | Action |
|--------------|--------|
| Will I need to deploy Teams in a Microsoft 365 Government – GCC environment? | For deployment considerations, see [Plan for Microsoft 365 Government - GCC deployments](plan-for-government-gcc.md).|
|||
