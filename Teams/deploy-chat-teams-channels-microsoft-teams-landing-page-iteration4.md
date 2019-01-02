---
title: Deploy chat, teams, channels, and apps in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/02/2019
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

Teams provides a great out-of-the-box collaboration experience for your organization, and you may find that the default settings work for you. But depending on your organization’s complexity and business requirements, you might want to change the configuration. We'll walk you through those changes, starting with the the changes you are more likely to make. We recommend that you work through these decisions (the core decisions outlined below), and then if your organization has additional requirements, review the additional decisions that follow.

## Teams chat, teams, channels, and app prerequisites 

Before you deploy Teams across your organization, take time to review and confirm that your environment is ready to provide users with the best
possible Teams experience. Review the following information and make any required changes to your environment.

- To get the best experience on Teams, your organization must have deployed [Exchange Online and SharePoint Online](#exchange-and-sharepoint-interoperability), and you must have a verified domain for O365 (such as *contoso.com*).

- To scale chat, teams, and channels across your organization, make sure that all user locations have internet access to connect to the Office 365 Services. At a minimum you should make sure that the following common ports are open to the internet from your users’ locations:

    - Open TCP ports 80 and 443 for outgoing traffic from clients that will use Teams.

    - Open UDP ports 3478 through 3481 for outgoing traffic from clients that will use Teams.


Find out more about preparing for Microsoft Teams in these articles:


|Ask yourself|Action |
|------------|-------|
Is my organization ready for Teams deployment?|To determine readiness, see <br>&nbsp;&nbsp;&bull;&nbsp; [Check your environment's readiness for Microsoft Teams](environment-readiness)<br>&nbsp;&nbsp;&bull;&nbsp;  [Prepare your organization's network for Microsoft Teams](prepare-network.md)<br>&nbsp;&nbsp;&bull;&nbsp; [Office 365 URLs and IP address ranges](office-365-urls-ip-address-ranges.md)<br>&nbsp;&nbsp;&bull;&nbsp; [Plan for Office 365 Groups when creating teams in Microsoft Teams](plan-office-365-groups.md)|
|||

## Core chat, teams, channels, and apps decisions

### Teams administrators

Teams provides a set of custom administrator roles for managing different aspects of Teams in your organization. The Teams Service Administrator manages the Teams service and creates and manages Office 365 Groups. See [Teams roles and capabilities](using-admin-roles.md#teams-roles-and-capabilities).

|Ask yourself|Action |
|------------|-------|
| Who will be assigned the Teams Service Administrator role? | To assign the Teams Servie Admin role, see [Assign administrator and non-administrator roles to users with Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal)
|||

### Messaging policies

Messaging policies are used to control what chat and channel messaging features are available to users in Teams. For example, who can edit and delete sent messages, chat availability, who can use memes in conversations, and more. By default, users are assigned the global messaging policy and all features are **On**. You can use the default global policy or create one or more custom messaging policies for people in your organization. 

|Ask yourself|Action |
|------------|-------|
|Will you customize the global messaging policy?<br> Do you require multiple messaging policies?<br>How will you determine which groups of users get which messaging policy?| To change or add a policy, see [What are Messaging policies in Teams?](https://docs.microsoft.com/microsoftteams/messaging-policies-in-teams)<br>To create and assign a messaging policy in PowerShell, see [PowerShell script sample - Create and assign a messaging policy](https://docs.microsoft.com/microsoftteams/scripts/powershell-script-teams-messaging-policy-edu).
|||

### External access

External access lets your Teams and Skype for Business users communicate with users who are outside of your organization. By turning this on and adding domains to the allowed list, your users can communicate with other users in other domains and organizations. External access is not configured by default.

|Ask yourself|Action |
|------------|-------|
| Will you enable external access for your organization?<br> If enabled, will you limit which domains your organization can communicate with? | To enable external access, see  [Let your Teams users chat and communicate with users in another Teams organization](https://docs.microsoft.com/MicrosoftTeams/let-your-teams-users-communicate-with-other-people).
|||

### Guest access

Guest access in Teams lets people outside your organization access teams and channels. You can use the settings below to control which features guest users can or can’t use. Guest access is turned off by default. For more information see [Guest Access in Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access).

|Ask yourself|Action |
|------------|-------|
| Will you enable guest access for your organization? <br> If enabled, will you customize the features available to guests in your organization?|To enable guest access, see [Turn on or off guest access in Teams](set-up-guests.md).<br>To customize the guest access features available, see [Authorize guest access in Teams](teams-dependencies.md).|
|||

### Teams settings

Teams settings let you set up your teams for features such as email integration, cloud storage options, and device set up. When you make changes to the settings
here, they will be applied to all the teams in your organization. For more information, see [Teams settings](enable-features-office-365.md#teams-settings). <<Need default settings>>

|Ask yourself|Action |
|------------|-------|
|Will you customize Teams settings for your organization? | To customize Teams settings, see [Teams settings](enable-features-office-365.md#teams-settings).
|||

### Teams clients

Teams supports a number of clients from web to desktop to mobile, and the default configuration lets users choose whichever client they want to. For more information, see [Get clients for Teams](get-clients.md).

|Ask yourself|Action |
|------------|-------|
| Will you customize Teams client availability for your organization?<br>Will you customize Teams client settings for your organization?|
<<There isn't anything to configure here - consider deleting this section.>>
|||

### Teams usage reporting

The Global Admin in Office 365, Teams Service Admin, and Reports Readers roles can view Teams usage reports. For more information, see the [Microsoft 365 usage analytics articles](https://docs.microsoft.com/en-gb/office365/admin/usage-analytics/usage-analytics?redirectSourcePath=%252farticle%252fMicrosoft-365-usage-analytics-77ff780d-ab19-4553-adea-09cb65ad0f1f&view=o365-worldwide).

|Ask yourself|Action |
|------------|-------|
| Will you grant the Reports Reader role to your adoption team members, so they can track usage? | To assign the Reports Reader role, see [Administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)
|||

### Teams default apps 

Teams provides a number of Microsoft provided and third-party apps via the Teams Store to engage your users and provide additional productivity capabilities and integration of commonly used business services into Teams. The default configuration is that the these apps are enabled for users to explore and use, for example users can use the Planner app to build and manage team tasks in a very effective manner. The out-of-the-box configuration enables the teams default apps and external apps that have been submitted via the [Teams Store approval process.](https://docs.microsoft.com/en-us/microsoftteams/platform/publishing/apps-publish#microsoft-teams-app-approval-process),


|Ask yourself|Action |
|------------|-------|
| Will you change the default teams apps settings? | See the [Admin settings for apps in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/admin-settings).|
|||


## Additional service decisions that may apply based on your organizational profile

Customers with additional complexity or compliance requirements may also want to consider the following in addition to the core service decisions outlined above.

### Teams licensing

Teams is provided as a component of a number of Office 365 licensing scenarios. To learn more about Teams licensing, see [Office 365 licensing for Microsoft Teams](office-365-licensing.md).

|Ask yourself|Action |
|------------|-------|
|Are your users correctly licensed for Teams capabilities that you are deploying? | See [Office 365 licensing for Microsoft Teams](office-365-licensing.md).
|||

### Exchange and SharePoint interoperability 

For the full Microsoft Teams experience, every user should be enabled for Exchange Online, SharePoint Online, and Office 365 Group creation. The following
articles outline information related to Exchange mailboxes hosted in various environments, how Exchange and Microsoft Teams interact, and similar
considerations for SharePoint and OneDrive for Business. 

|Ask yourself|Action |
|------------|-------|
| Will you be able to deploy the Teams features that you require with your current Exchange and SharePoint deployments? |See [How Exchange and Microsoft Teams interact](exchange-teams-interact.md) and [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).
|||


### Teams limits and specifications 

When planning an enterprise deployment of Teams, you should take into account any relevant limitations and specifications, such as the maximum number
of members in a team, the maximum number of teams a user can create, and so on.

|Ask yourself|Action |
|------------|-------|
| Are there any limits that you are likely to hit with your deployment that you need to take into consideration? | See [Limits and specifications for Microsoft Teams](limit-specifications-teams.md)|
|||

### Office 365 URLs and ports

Organisations that maintain fine grained control of their internet traffic should go to the [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) for a detailed and up-to-date list of the URLs, IP addresses, ports, and protocols that must be correctly configured for Teams. Microsoft is continuously improving the Office 365 service and adding new functionality, which means the required ports, URLs, and IP addresses may change over time. We recommend that you subscribe via RSS to receive notifications when this information is updated or changed.

|Ask yourself|Action |
|------------|-------|
| Do you require internet access rules to enable users to use Teams or can you simply open TCP ports 80 and 443 outgoing from clients that will use Teams and open UDP ports 3478 through 3481 outgoing from clients that will use Teams? | See [Office 365 URLs and IP address ranges](office-365-urls-ip-address-ranges.md)|
|||


### Governance (naming conventions, who can create teams)<to here>

Your organization might require that you implement controls on how teams are
named and classified, who can create teams, and team expiration, retention, and
archiving. You can use Azure Active Directory (Azure AD) to configure each of these areas.

The [Plan for governance in Teams article](https://docs.microsoft.com/en-us/microsoftteams/plan-teams-governance)
provides more information on this.

| <img src="media/audio_conferencing_image7.png" /> | Will you need to implement controls on how teams are named? |
|------------------------------------------|-------------------------------------------------------------|


-   Will you need to implement controls on who can create teams?

-   Will you need to configure team expiration?

### Team application policy (side rail control)

The Teams application policy will allow you to pre-configure sets of pinned
Teams applications for groups of users to provide a more personal and targeted
experience.

| <img src="media/audio_conferencing_image7.png" /> | Will you create pre-configure sets of pinned Teams applications? |
|------------------------------------------|------------------------------------------------------------------|


-   How will you decide on which groups receive these app groupings?

### Archiving and compliance 

Your organization might require that you implement controls on how teams are
archived and the types of data that are held in certain types of teams, the
[Overview of security and compliance in Microsoft
Teams](https://docs.microsoft.com/en-us/microsoftteams/security-compliance-overview)
articles will provide you information to help in this process.

| <img src="media/audio_conferencing_image7.png" /> | Will you need to configure team retention? |
|------------------------------------------|--------------------------------------------|


-   Will you need to configure team archiving?

-   Will you need to configure additional compliance settings?

### Conditional access 

Microsoft Teams relies heavily on Exchange Online, SharePoint Online, and Skype
for Business Online for core productivity scenarios, like meetings, calendars,
interop chats, and file sharing. Conditional access policies that are set for
these cloud apps apply to Microsoft Teams when a user directly signs in to
Microsoft Teams - on any client. Conditional access policies that are set for
the Microsoft Teams cloud app apply to Microsoft Teams when a user signs in and
can control aspects such as whether users can access Teams services from certain
networks.

The [How do Conditional Access policies work for
Teams](https://docs.microsoft.com/en-us/MicrosoftTeams/security-compliance-overview#how-do-conditional-access-policies-work-for-teams)
article provides further information.

| <img src="media/audio_conferencing_image7.png" /> | Will you need to configure Conditional Access for Teams? |
|------------------------------------------|----------------------------------------------------------|


### Education (EDU) 

IT Pros working in Education can take advantage of Teams for Education which
comes with a number of capabilities that have been tailored to meet Education
specific scenarios for students, faculty and the wider business.

The [Microsoft Education governance FAQ for
admins](https://docs.microsoft.com/en-us/microsoftteams/plan-teams-governance-edu)
article provides a good overview of the additional considerations and the [Quick
start - Microsoft Teams for Education
admins](https://docs.microsoft.com/en-us/microsoftteams/teams-quick-start-edu)
articles provides Education specific onboarding information.

| <img src="media/audio_conferencing_image7.png" /> | Will you integrate Teams with the School Data Sync service to provision user accounts? |
|------------------------------------------|----------------------------------------------------------------------------------------|


-   Will you leverage EDU specific Team templates?

-   Will you deploy scoped search?

### Government - GCC considerations

The use of Microsoft 365 Government - GCC is appropriate to meet the
requirements of

IT pros who are driving deployments of Office 365 in US federal, state, local,
tribal, or territorial government entities or other entities that handle data
that’s subject to government regulations and requirements.

The [Plan for Microsoft 365 Government - GCC
deployments](https://docs.microsoft.com/en-us/microsoftteams/plan-for-government-gcc)
article provides further information.

| <img src="media/audio_conferencing_image7.png" /> | Will you need be deploying Teams in a Microsoft 365 Government – GCC environment? |
|------------------------------------------|-----------------------------------------------------------------------------------|

