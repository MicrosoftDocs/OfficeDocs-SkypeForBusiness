---
title: Plan for governance in Teams - Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: serdars
ms.date: 07/30/2018
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

Teams provides a rich set of tools to implement governance and lifecycle management capabilities should your organization require it. This article guides IT Pros to ask the right questions to determine their requirements for governance and lifeceyle management, and how to meet them. 

## Group creation, naming, classification and guest access
For some organizations, it may be a requirement to implement strict controls on who can create teams, how those teams are named, applying a classification and whether or not guests can be added as a team member. Microsoft provides capabilities to control each of these configuration areas via Azure Active Directory (AAD). 

<br>
|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Does your organization require limiting who can create teams?</li><li>Does your organization require a specific naming convention for teams?</li><li>Do team creators need the ability to specific organization specific classifications to teams?</li><li>Do you need to restrict the ability to add guests to teams on a per team basis?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document your organizations requirements for team creation, naming, classification and guest access.</li><li>Plan to implement your specific requirements as a part of your Teams rollout.</li><li>Communicate/publish your policies to inform Teams users of expected behavior.</li></ul>|

> [!TIP]
Use the following table to capture your organizations requirements.
|Capability |Details |AAD Premium P1 <br> license required |Decision |
|---------|---------|---------|---------|
|Team Creation |Limit team creation to admins or security group members |No |TBD|
|Team Naming Policy | Prefix-Suffix based, Custom Blocked Words |Yes |TBD |
|Team Classification |Assign specified classification to team |Yes |TBD |
|Team Guest Access |Allow or prevent guests from being added to teams |No |TBD |


#### Additional Information
Once you have determined your requirements, you can implement them using Azure Active Directory (AAD) controls. For technical guidance on how to implement these settings, see: <br>
[Azure Active Directory cmdlets for configuring group settings.](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-settings-cmdlets) <br>
[Enforce a naming policy for Office 365 groups in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-naming-policy) <br>
[Office 365 Groups naming policy](https://support.office.com/article/office-365-groups-naming-policy-6ceca4d3-cad1-4532-9f0f-d469dfbbb552) <br>


## Group expiration, retention and archiving
Another area that some organizations may require additional controls is around expiring, retaining and archiving teams and teams data. Administrators can configure group expiration policies to automatically manage the lifecycle of the group, retention policies to preserve or delete information as desired and teams can be archived (set to read only mode) to preserve a point in time view of a team that is no longer active.

> [!TIP]
Use the following table to capture your organizations requirements.
|Capability |Details |Decision |
|---------|---------|---------|---------|
|Expiration policy |Manage the lifecycle of Office 365 groups by setting an expiration policy |TBD|
|Retention policy |Retain or delete data in a specified time period |TBD |
|Archive and restore |Archive a team when it’s no longer active, but you want to keep it around for reference or to reactivate in the future |TBD |

#### Additional Information
For technical guidance on how to implement these settings, see: <br>
[Set up Office 365 groups expiration](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-lifecycle) <br>
[Set up Teams retention policies](https://docs.microsoft.com/en-us/MicrosoftTeams/security-compliance-overview#retention-policies) <br>
[Archive or restore a team](https://support.office.com/en-us/article/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7?ui=en-US&rs=en-001&ad=US) <br>


## Teams feature management
Another important aspect of governance and lifecylce management for Teams is the ability to control what features your users will have access to. Messaging, meeting an calling features can all be managed by an Administrator and these features can be controlled at either a Office 365 tenant level, or a user level. 


|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Does your organization require limiting Teams features for your entire tenant?</li><li>Does your organization require limiting Teams features for specific users?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document your organizations requirements for limiting Teams features at the tenant and user level.</li><li>Plan to implement your specific requirements as a part of your Teams rollout.</li><li>Communicate/publish your policies to inform Teams users of expected behavior.</li></ul>|

#### Do we add a table for example policy settings ot leave that to the following pages?

## Feature Management Focus Area
<ul>[Messaging Policies](tbd)</ul>
<ul>[Calling Policies](tbd)</ul>
<ul>[Meeting Policies](tbd)</ul>

#### Additional Information
For technical guidance on how to implement these settings, see: <br>
[Manage Microsoft Teams features in your Office 365 organization](https://docs.microsoft.com/en-us/MicrosoftTeams/enable-features-office-365) <br>

## Security and compliance
Teams is built on the advanced security and compliance capabilities of Office 365 and supports auditing and reporting, compliance content search, eDiscovery, Legal Hold and retention policies. 

If your organization have compliance and security requirements, please review the in depth content provided on this topic in the [Overview of security and compliance in Microsoft Teams](https://docs.microsoft.com/en-us/MicrosoftTeams/security-compliance-overview) article.

