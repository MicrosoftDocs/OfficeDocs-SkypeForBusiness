---
title: Plan for governance in Teams - Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: serdars
ms.date: 08/01/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Learn about how to plan for implementing governance and lifecycle management capabilities in Teams.
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

# Plan for governance in Teams

Teams provides a rich set of tools to implement any governance and lifecycle management capabilities your organization might require. This article guides IT pros to ask the right questions to determine their requirements for governance and lifecycle management, and how to meet them. 

## Group and team creation, naming, classification, and guest access

Your organization might require that you implement strict controls on who can create teams, how those teams are named and classified, and whether guests can be added as team members. You can configure each of these areas by using Azure Active Directory (Azure AD). 

<br>
|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Does your organization require limiting who can create teams?</li><li>Does your organization require a specific naming convention for teams?</li><li>Do team creators need the ability to assign organization-specific classifications to teams?</li><li>Do you need to restrict the ability to add guests to teams on a per-team basis?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document your organization’s requirements for team creation, naming, classification, and guest access.</li><li>Plan to implement these requirements as a part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

> [!TIP]
Use the following table to capture your organization’s requirements.
|Capability |Details |Azure AD Premium P1 <br> license required |Decision |
|---------|---------|---------|---------|
|Team creation |Limit team creation to admins or security group members. |No |TBD|
|Team naming policy | Prefix-Suffix–based, Custom Blocked Words. |Yes |TBD |
|Team classification |Assign classifications to teams. |Yes |TBD |
|Team guest access |Allow or prevent guests from being added to teams. |No |TBD |


#### Additional information

After you’ve determined your requirements, you can implement them by using Azure AD controls. For technical guidance on how to implement these settings, see:

-   [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets).

-   [Enforce a naming policy for Office 365 groups in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-naming-policy).

-   [Office 365 Groups naming policy](https://support.office.com/article/office-365-groups-naming-policy-6ceca4d3-cad1-4532-9f0f-d469dfbbb552).


## Group and team expiration, retention, and archiving

Your organization might have additional requirements for setting policies for expiration, retention, and archiving teams and teams data. You can configure group expiration policies to automatically manage the lifecycle of the group and retention policies to preserve or delete information as needed, and you can archive teams (set them to read-only mode) to preserve a point-in-time view of a team that’s no longer active.

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Does your organization require specifying and expiration date for teams?</li><li>Does your organization require specific data retention policies applied to teams?</li><li>Does your organization expect to require the ability to archive inactive teams to preserve the content in a read-only state?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document your organization’s requirements for team expiration, data retention, and archiving.</li><li>Plan to implement these requirements as part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

> [!TIP]
Use the following table to capture your organization’s requirements.
|Capability |Details |Decision |
|---------|---------|---------|---------|
|Expiration policy |Manage the lifecycle of Office 365 groups by setting an expiration policy. |TBD|
|Retention policy |Retain or delete data in a specified time period. |TBD |
|Archive and restore |Archive a team when it’s no longer active but you want to keep it around for reference or to reactivate in the future. |TBD |

#### Additional information

For technical guidance on how to implement these settings, see:

-   [Set up Office 365 groups expiration](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-lifecycle).

-   [Set up Teams retention policies](security-compliance-overview.md#retention-policies).

-   [Archive or restore a team](https://support.office.com/article/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7).


## Teams feature management

Another important aspect of governance and lifecycle management for Teams is the ability to control what features your users will have access to. You can manage messaging, meeting, and calling features, either at the Office 365 tenant level or per-user. 


|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Does your organization require limiting Teams features for your entire tenant?</li><li>Does your organization require limiting Teams features for specific users?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document your organization’s requirements for limiting Teams features at the tenant and user level.</li><li>Plan to implement your specific requirements as part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

### Teams Feature Management Focus Areas

-    [Messaging Policies](tbd)
-    [Calling Policies](tbd)
-    [Meeting Policies](tbd)

For detailed information on Teams feature management capabilities, see [Plan for Teams lifecycle](plan-teams-lifecycle.md).



#### Additional information

For technical guidance on how to implement these settings, see:

-   [Manage Microsoft Teams features in your Office 365 organization](enable-features-office-365.md).

## Security and compliance

Teams is built on the advanced security and compliance capabilities of Office 365 and supports auditing and reporting, compliance content search, e-discovery, Legal Hold, and retention policies. 

> [!Important]
> If your organization has compliance and security requirements, review the in-depth content provided about this topic in the article [Overview of security and compliance in Microsoft Teams](security-compliance-overview.md).

