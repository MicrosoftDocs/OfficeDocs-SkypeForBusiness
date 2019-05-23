---
title: Plan for governance in Teams - Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 08/10/2018
ms.topic: reference
ms.service: msteams
ms.reviewer: rowille
description: Learn about how to plan for implementing governance capabilities in Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Plan for governance in Teams

Teams provides a rich set of tools to implement any governance capabilities your organization might require. This article guides IT pros to ask the right questions to determine their requirements for governance, and how to meet them. 

> [!Tip] 
> Watch the following session to learn about more about Governance in Microsoft Teams: [Governance, management and lifecycle in Microsoft Teams](https://aka.ms/teams-governance)

## Group and team creation, naming, classification, and guest access

Your organization might require that you implement strict controls on how teams are named and classified, whether guests can be added as team members, and who can create teams. You can configure each of these areas by using Azure Active Directory (Azure AD). 

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" alt= "An icon depicting decision points"/>  |Decision points|<ul><li>Does your organization require a specific naming convention for teams?</li><li>Do team creators need the ability to assign organization-specific classifications to teams?</li><li>Do you need to restrict the ability to add guests to teams on a per-team basis?</li><li>Does your organization require limiting who can create teams?</li></ul>|
|<img src="media/audio_conferencing_image9.png" alt= "An icon depicting the next steps"/>|Next steps|<ul><li>Document your organization’s requirements for team creation, naming, classification, and guest access.</li><li>Plan to implement these requirements as a part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

> [!TIP]
> Use the following table to capture your organization’s requirements.

|Capability |Details |Azure AD Premium <br> license required |Decision |
|---------|---------|---------|---------|
|Team naming policy | Use Prefix-Suffix–based, Custom Blocked Words. |P1 |TBD |
|Team classification |Assign classifications to teams. |P1 |TBD |
|Team guest access |Allow or prevent guests from being added to teams. |No |TBD |
|Team creation |Limit team creation to administrators. |No |TBD|
|Team creation |Limit team creation to security group members. |P1 |TBD|

> [!NOTE]
> To help you plan ahead, [learn more about setting these policies and what licenses they require](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets#template-settings).
> 
> [!NOTE]
> Limiting group and team creation can slow your users’ productivity, because many Office 365 services require that groups be created for the service to function. For additional information, navigate to and expand [Why control who creates Office 365 Groups](https://support.office.com/article/manage-who-can-create-office-365-groups-4c46c8cb-17d0-44b5-9776-005fced8e618#why).


#### Additional information

After you’ve determined your requirements, you can implement them by using Azure AD controls. For technical guidance on how to implement these settings, see:

-   [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets).

-   [Enforce a naming policy for Office 365 groups in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-naming-policy).

-   [Office 365 Groups naming policy](https://support.office.com/article/office-365-groups-naming-policy-6ceca4d3-cad1-4532-9f0f-d469dfbbb552).


## Group and team expiration, retention, and archiving

Your organization might have additional requirements for setting policies for expiration, retention, and archiving teams and teams data (channel messages and channel files). You can configure group expiration policies to automatically manage the lifecycle of the group and retention policies to preserve or delete information as needed, and you can archive teams (set them to read-only mode) to preserve a point-in-time view of a team that’s no longer active.

|           |            |
|-----------|------------|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Does your organization require specifying an expiration date for teams?</li><li>Does your organization require specific data retention policies be applied to teams?</li><li>Does your organization expect to require the ability to archive inactive teams to preserve the content in a read-only state?</li></ul>|
| ![An icon depicting the next steps](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Document your organization’s requirements for team expiration, data retention, and archiving.</li><li>Plan to implement these requirements as part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

> [!TIP]
> Use the following table to capture your organization’s requirements.

|Capability |Details |Azure AD Premium license required |Decision |
|---------|---------|---------|---------|
|Expiration policy |Manage the lifecycle of Office 365 groups by setting an expiration policy. |P1 |TBD|
|Retention policy |Retain or delete data for a specific time period by setting retention policies for Teams in the Security & compliance center. **Note**: Using this feature requires licensing of Office 365 Enterprise E3 or above. |No |TBD |
|Archive and restore |Archive a team when it’s no longer active but you want to keep it around for reference or to reactivate in the future. |No |TBD |

> [!Note]
> Group expiration is an Azure AD Premium feature. For this feature to be available, your tenant must have a subscription to Azure AD Premium and licenses for the administrator who configures the settings and the members of the affected groups.

#### Additional information

For technical guidance on how to implement these settings, see:

-   [Set up Office 365 groups expiration](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-lifecycle).

-   [Set up Teams retention policies](retention-policies.md).

-   [Archive or restore a team](https://support.office.com/article/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7).


## Teams feature management

Another important aspect of governance and lifecycle management for Teams is the ability to control what features your users will have access to. You can manage messaging, meeting, and calling features, either at the Office 365 tenant level or per-user. 


|         |         |
|---------|---------|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Does your organization require limiting Teams features for your entire tenant?</li><li>Does your organization require limiting Teams features for specific users?</li></ul>|
| ![An icon depicting the next steps](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Document your organization’s requirements for limiting Teams features at the tenant and user level.</li><li>Plan to implement your specific requirements as part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

### Teams feature management focus areas

Teams provides granular capabilities for controlling messaging, meeting, calling, and live event features and more, via policies. Different policies can be applied to all users by default or per user as required by your organization. 

For detailed lists of all settings, including technical guidance on how to implement them for your organization, see the following articles:

-   [Manage Microsoft Teams settings for your organization](enable-features-office-365.md)
-   [Manage Teams during the transition to the new Microsoft Teams admin center](manage-teams-skypeforbusiness-admin-center.md)
-   [Manage meeting policies in Teams](meeting-policies-in-teams.md)


## Security and compliance

Teams is built on the advanced security and compliance capabilities of Office 365 and supports auditing and reporting, compliance content search, e-discovery, Legal Hold, and retention policies. 

> [!Important]
> If your organization has compliance and security requirements, review the in-depth content provided about this topic in the article [Overview of security and compliance in Microsoft Teams](security-compliance-overview.md).

<!--
## Teams lifecycle management

In addition to planning for governance, your organization might also be interested in planning for Teams lifecycle management. For practical guidance on planning for teams lifecycle management, see [Plan for lifecycle management in Teams](plan-teams-lifecycle.md).
-->
