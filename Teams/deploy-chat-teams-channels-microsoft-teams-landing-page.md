---
title: Deploy chat, teams, & channels in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 11/02/2018
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Step-by-step guidance to rolling out chat, teams, and channels in Microsoft Teams
localization_priority: Normal
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---
# Deploy chat, teams, & channels in Microsoft Teams


Teams has been designed to provide a great out-of-the-box collaboration
experience for your organization. Depending on your organization’s complexity
and business requirements, you many want to adjust the initial configuration.

This section walks you through the main service decisions that you may need to
make as part of the technical implementation to define your configuration, in
this section these decisions relate to the key collaboration components of chat,
teams, channels, apps and tabs.

We recommend that all organizations work through the core decisions and then if
your organization has additional requirements to review the following material.

## Teams Prerequisites 

Prior to scaling your Teams deployment across your organization, take time to
review and confirm your environment is ready to provide users with the best
possible Teams experience. Review the following information and make any
required changes to your environment as needed.

To get the best experience on Teams, your organization must have deployed
Exchange Online and SharePoint Online and you have a verified domain for O365
such as contoso.com.

To scale chat, teams and channels across your organisation you should ensure
that all user locations have Internet access to connect to the Office 365
Services, at a minimum you should ensure that the following common ports are
open to the Internet from your user’s locations:-

-   Open TCP ports 80 and 443 outgoing from clients that will use Teams.

-   Open UDP ports 3478 through 3481 outgoing from clients that will use Teams

| <img src="media/audio_conferencing_image7.png" /> | Is my organization ready for Teams deployment? |
|------------------------------------------|------------------------------------------------|


The following articles provide further reading related to environmental
readiness.

### Environmental Readiness

<https://docs.microsoft.com/en-us/MicrosoftTeams/environment-readiness>

### Network Readiness

<https://docs.microsoft.com/en-us/MicrosoftTeams/prepare-network>

### Office 365 URLs and IPs

<https://docs.microsoft.com/en-us/MicrosoftTeams/office-365-urls-ip-address-ranges>

### Plan for Groups

<https://docs.microsoft.com/en-us/MicrosoftTeams/plan-office-365-groups>

## Core service decisions

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage
Teams for your organization. The roles provide various capabilities to
administrators. To learn more about Teams administrator roles see [Use Microsoft
Teams admin roles to manage
Teams](https://docs.microsoft.com/en-us/MicrosoftTeams/using-admin-roles).

| <img src="media/audio_conferencing_image7.png" /> | Who will be assigned the Teams Service Administrator role? |
|------------------------------------------|------------------------------------------------------------|


### Messaging policies

Messaging policies are used to control what chat and channel messaging features
are available to users in Teams. You can use the default policy that is created
or create one or more custom messaging policies for people in your
organization. For more information see [What are Messaging policies in
Teams?](https://docs.microsoft.com/microsoftteams/messaging-policies-in-teams)

| <img src="media/audio_conferencing_image7.png" /> | Will you customize the global messaging policy? |
|------------------------------------------|-------------------------------------------------|


-   Do you require multiple messaging policies?

-   How will you determine which groups of users get which messaging policy
    applied?

### External access

External access lets your Teams and Skype for Business users communicate with
users that are outside of your organization. By turning this on and adding
domains to the allowed list, your users can communicate with other users in
other domains and organizations. For more information see [Let your Teams users
chat and communicate with users in another Teams
organization](https://docs.microsoft.com/MicrosoftTeams/let-your-teams-users-communicate-with-other-people).

| <img src="media/audio_conferencing_image7.png" /> | Will you enable external access for your organization? |
|------------------------------------------|--------------------------------------------------------|


-   If enabled, will you limit what domains your organization and communicate
    with?

### Guest Access

Guest access in Teams lets people outside your organization access teams and
channels. You can use the settings below to control which features guest users
can or can’t use. For more information see [Guest Access in Microsoft
Teams](https://docs.microsoft.com/microsoftteams/guest-access).

| <img src="media/audio_conferencing_image7.png" /> | Will you enable guest access for your organization? |
|------------------------------------------|-----------------------------------------------------|


-   If enabled, will you customize the features available to guests in your
    organization?

### Teams Settings

Teams settings let you set up your teams for features such as email integration,
cloud storage options, and device set up. When you make changes to the settings
here, they will be applied to all of the teams within your organization. For
more information see \<need a better link\>.

| <img src="media/audio_conferencing_image7.png" /> | Will you customize Teams settings for your organization? |
|------------------------------------------|----------------------------------------------------------|


### Teams Clients

Teams supports a number of clients from web to desktop to mobile, the default
configuration of these enables users to leverage whichever client they want
to. For more information see \<need a better link\>.

| <img src="media/audio_conferencing_image7.png" /> | Will you customize Teams client availability for your organization? |
|------------------------------------------|---------------------------------------------------------------------|


-   Will you customize Teams client settings for your organization?

### Teams Usage Reporting

The following roles enable holders to view Teams usage reports, a global admin
in Office 365, Teams service admin, or Reports Reader.

For more information see the [Microsoft 365 usage analytics
articles](https://docs.microsoft.com/en-gb/office365/admin/usage-analytics/usage-analytics?redirectSourcePath=%252farticle%252fMicrosoft-365-usage-analytics-77ff780d-ab19-4553-adea-09cb65ad0f1f&view=o365-worldwide).

| <img src="media/audio_conferencing_image7.png" /> | Will you grant the Reports Reader role to your adoption team members, so they can track usage? |
|------------------------------------------|------------------------------------------------------------------------------------------------|


### Teams Default Apps 

Teams provides a number of Microsoft provided and 3rd party apps via the Teams
Store to engage your users and provide additional productivity capabilities and
integration of commonly used business services into Teams. The default
configuration is that the these apps are enabled for users to explore and use,
for example users can make use of the Planner app to build and manage team tasks
in a very effective manner. The out of the box configuration enables the teams
default apps as well as external apps that have been submitted via the [Teams
Store approval
process.](https://docs.microsoft.com/en-us/microsoftteams/platform/publishing/apps-publish#microsoft-teams-app-approval-process)

For more information see the [Admin settings for apps in Microsoft
Teams.](https://docs.microsoft.com/en-us/microsoftteams/admin-settings)

| <img src="media/audio_conferencing_image7.png" /> | Will you change the default teams apps settings? |
|------------------------------------------|--------------------------------------------------|


## Additional service decisions that may apply based on organizational profile

Customers with additional complexity or compliance requirements may also want to
consider the following in addition to the Core service decisions outlined above.

### Teams Licensing

Teams is provided as component of a number of Office 365 licensing scenarios, To
learn more about Teams licensing roles see \<Add link to Licensing articles\>.

| <img src="media/audio_conferencing_image7.png" /> | Are your users are correctly licensed for Teams capabilities that you are deploying? |
|------------------------------------------|--------------------------------------------------------------------------------------|


### Exchange and SharePoint interoperability 

For the full Microsoft Teams experience, every user should be enabled for
Exchange Online, SharePoint Online, and Office 365 Group creation. The following
articles outlines information related to Exchange mailboxes hosted in various
environments, \<How Exchange and Microsoft Teams interact? and similar
considerations for SharePoint and OneDrive for Business, \<How SharePoint Online
and OneDrive for Business interact with Microsoft Teams\>

| <img src="media/audio_conferencing_image7.png" /> | Will you be able to deploy the Teams features that you require with your current Exchange and SharePoint deployments ? |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------|


### Teams Limits and Specifications 

When planning an Enterprise deployment of Teams it is important to take into
account any relevant limitations and specifications such as the maximum number
of members in a team, the \<Limits and specifications for Microsoft Teams\>
article covers this off.

| <img src="media/audio_conferencing_image7.png" /> | Are there any limits that you are likely to hit with your deployment that you need to take into consideration? |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------|


### O365 URL’s and Ports

Organisations that maintain fine grained control of their internet traffic
should go to the [Office 365 URLs and IP address
ranges](https://docs.microsoft.com/en-gb/office365/enterprise/urls-and-ip-address-ranges)
for a detailed and up-to-date list of the URLs, IP addresses, ports, and
protocols that must be correctly configured for Teams. Microsoft is continuously
improving the Office 365 service and adding new functionality, which means the
required ports, URLs, and IP addresses may change over time. We recommend that
you subscribe via RSS to receive notifications when this information is updated
or changed.

| <img src="media/audio_conferencing_image7.png" /> | Do you require to implement internet access rules to enable users to use Teams or can you simply open TCP ports 80 and 443 outgoing from clients that will use Teams and open UDP ports 3478 through 3481 outgoing from clients that will use Teams? |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|


### Governance (Naming conventions and determine who can create Teams)

Your organization might require that you implement controls on how teams are
named and classified, who can create teams and team expiration, retention and
archiving. You can configure each of these areas by using Azure Active Directory
(Azure AD).

The [Plan for governance in Teams
article](https://docs.microsoft.com/en-us/microsoftteams/plan-teams-governance)
provides more information on this.

| <img src="media/audio_conferencing_image7.png" /> | Will you need to implement controls on how teams are named? |
|------------------------------------------|-------------------------------------------------------------|


-   Will you need to implement controls on who can create teams?

-   Will you need to configure team expiration?

### Team Application Policy (side rail control)

The Teams application policy will allow you to pre-configure sets of pinned
Teams applications for groups of users to provide a more personal and targeted
experience.

| <img src="media/audio_conferencing_image7.png" /> | Will you create pre-configure sets of pinned Teams applications? |
|------------------------------------------|------------------------------------------------------------------|


-   How will you decide on which groups receive these app groupings?

### Archiving and Compliance 

Your organization might require that you implement controls on how teams are
archived and the types of data that are held in certain types of teams, the
[Overview of security and compliance in Microsoft
Teams](https://docs.microsoft.com/en-us/microsoftteams/security-compliance-overview)
articles will provide you information to help in this process.

| <img src="media/audio_conferencing_image7.png" /> | Will you need to configure team retention? |
|------------------------------------------|--------------------------------------------|


-   Will you need to configure team archiving?

-   Will you need to configure additional compliance settings?

### Conditional Access 

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


### EDU 

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

### GCC Considerations

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

