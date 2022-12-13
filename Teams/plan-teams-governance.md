---
title: Plan for governance in Teams - Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: reference
ms.service: msteams
ms.reviewer: rowille
audience: admin
description: In this article, you will learn about how to plan for implementing governance capabilities in Teams.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
ms.custom: seo-marvel-apr2020
appliesto: 
  - Microsoft Teams
---

# Plan for governance in Teams

Teams provides a rich set of tools to implement any governance capabilities your organization might require. This article guides IT pros to ask the right questions to determine their requirements for governance, and how to meet them. 

> [!Tip] 
> Watch the following session to learn about more about Governance in Microsoft Teams: [Governance, management and lifecycle in Microsoft Teams](https://aka.ms/teams-governance)

## Group and team creation, naming, classification, and guest access

Your organization might require that you implement strict controls on how teams are named and classified, whether guests can be added as team members, and who can create teams. You can configure these areas by using Azure Active Directory (Azure AD) and sensitivity labels. 

<br>

|-        |-        |-        |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" alt= "An icon depicting decision points"/>  |Decision points|<ul><li>Does your organization require a specific naming convention for teams?</li><li>Do team creators need the ability to assign organization-specific classifications to teams?</li><li>Do you need to restrict the ability to add guests to teams on a per-team basis?</li><li>Does your organization require limiting who can create teams?</li></ul>|
|<img src="media/audio_conferencing_image9.png" alt= "An icon depicting the next steps"/>|Next steps|<ul><li>Document your organization’s requirements for team creation, naming, classification, and guest access.</li><li>Plan to implement these requirements as a part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

> [!NOTE]
> To help you plan ahead, [learn more about setting these policies and what licenses they require](/azure/active-directory/users-groups-roles/groups-settings-cmdlets#template-settings).
> 
> [!NOTE]
> Limiting group and team creation can slow your users’ productivity, because many Microsoft 365 and Office 365 services require that groups be created for the service to function. For additional information, visit [Plan for governance in Teams](/microsoft-365/solutions/manage-creation-of-groups).


#### Additional information

After you’ve determined your requirements, you can implement them by using Azure AD controls. For technical guidance on how to implement these settings, see:

- [Azure Active Directory cmdlets for configuring group settings](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)

- [Enforce a naming policy for Microsoft 365 groups in Azure Active Directory](/azure/active-directory/users-groups-roles/groups-naming-policy)

- [Microsoft 365 Groups naming policy](https://support.office.com/article/office-365-groups-naming-policy-6ceca4d3-cad1-4532-9f0f-d469dfbbb552)

- [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)

- [End of lifecycle options for groups, teams, and Yammer](/microsoft-365/solutions/end-life-cycle-groups-teams-sites-yammer)

## Group and team expiration, retention, and archiving

Your organization might have additional requirements for setting policies for expiration, retention, and archiving teams and teams data (channel messages and channel files). You can configure group expiration policies to automatically manage the lifecycle of the group and retention policies to preserve or delete information as needed, and you can archive teams (set them to read-only mode) to preserve a point-in-time view of a team that’s no longer active. Note that teams that are archived continue to have the expiration policy applied and may be deleted unless excluded or renewed.

|-          |-           |
|-----------|------------|
| ![An icon depicting decision points.](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Does your organization require specifying an expiration date for teams?</li><li>Does your organization require specific data retention policies be applied to teams?</li><li>Does your organization expect to require the ability to archive inactive teams to preserve the content in a read-only state?</li></ul>|
| ![An icon depicting the next steps.](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Document your organization’s requirements for team expiration, data retention, and archiving.</li><li>Plan to implement these requirements as part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

> [!TIP]
> Use the following table to capture your organization’s requirements.

|Capability |Details |Azure AD Premium license required |Decision |
|---------|---------|---------|---------|
|Expiration policy |Manage the lifecycle of Microsoft 365 groups by setting an expiration policy. |P1 |TBD|
|Retention policy |Retain or delete data for a specific time period by setting retention policies for Teams in the Security & compliance center. **Note**: Using this feature requires licensing of Microsoft 365 or Office 365 Enterprise E3 or above. |No |TBD |
|Archive and restore |Archive a team when it’s no longer active but you want to keep it around for reference or to reactivate in the future. |No |TBD |

> [!Note]
> Group expiration is an Azure AD Premium feature. For this feature to be available, your tenant must have a subscription to Azure AD Premium and licenses for the administrator who configures the settings and the members of the affected groups.

#### Additional information

For technical guidance on how to implement these settings, see:

- [Set up Microsoft 365 groups expiration](/azure/active-directory/users-groups-roles/groups-lifecycle).

- [Set up Teams retention policies](retention-policies.md).

- [Archive or restore a team](https://support.office.com/article/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7).

## Group and team membership management

Consistently managing members of project based, or restricted groups are necessary for teams that require rapid onboarding and offboarding or users and guests. Your organization may also need to make sure all current members have the business justification to be in a team. Managing members can be hard because team owners can leave and users don’t usually leave groups on their own accord when a project ends or when they change roles. The best way to manage group membership that allows users to get access when needed but ensure the group doesn't have a risk of inappropriate access is through two district processes: entitlement management and access reviews.

[Entitlement management](/azure/active-directory/governance/entitlement-management-overview) allows you to delegate to someone, such as a project manager, to collect all the resources that are needed, including teams memberships, into a single package. They can also define who can make requests: either users in your tenant or from other connected organizations. The project manager will receive access requests in their email and approve or deny requests in the MyAccess portal. Administrators can configure the conditions of access to include an expiry date or period by when the user or guest will be removed from the team unless access is renewed. Administrators can also set up the groups associated with teams to take part in access reviews. For [access reviews](/azure/active-directory/governance/access-reviews-overview), the group owners will receive regular reminders to review the members of a team. Access reviews include recommendations, which makes it easier for group owners to go through their regular attestation process.

|-|-|-|
|:-|:-|:-|
|<img src="media/audio_conferencing_image7.png" alt= "An icon depicting decision points"/>  | Decision points | Does your organization require a consistent process for managing membership of one or more teams? <br> Does your organization require owners, or the members themselves, to justify their continued membership of one or more teams on a regular basis? <br> Does your organization require approval for users and guests to request access to resources including teams, groups, SharePoint sites, and apps? |
|<img src="media/audio_conferencing_image9.png" alt= "An icon depicting the next steps"/>| Next steps? | Document your organizations requirements for each team or specific teams for membership expiry.<br>Plan how your organization can bundle teams, groups, SharePoint sites, and apps together in access packages.<br>Plan which people, such as the requestor's manager, a project manager, a sponsor for a connected organization or a security officer in your organization will need to approve or deny access requests. |

> [!TIP]
> Use the following table to capture your organization’s requirements.

| Capability | Details | Azure AD Premium license required | Decision |
|:-|:-|:-|:-|
| Access reviews | Setup access reviews to recertify the membership of specific teams at regular interval | P2 | TBD |
| Entitlement management | Setup access package to allow users and guests to request access to teams | P2 | TBD |

> [!NOTE]
> To help you plan ahead, [learn more about what licenses they require](https://azure.microsoft.com/pricing/details/active-directory/).

### Additional information

For technical guidance on how to implement these settings, see:

- [Entitlement management](/azure/active-directory/governance/entitlement-management-overview)
- [Access reviews](/azure/active-directory/governance/access-reviews-overview)

## Teams feature management

Another important aspect of governance and lifecycle management for Teams is the ability to control what features your users will have access to. You can manage messaging, meeting, and calling features, either at the Microsoft 365 or Office 365 organization level or per-user.


|-        |-        |
|---------|---------|
| ![An icon depicting decision points.](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Does your organization require limiting Teams features for your entire tenant?</li><li>Does your organization require limiting Teams features for specific users?</li></ul>|
| ![An icon depicting the next steps.](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Document your organization’s requirements for limiting Teams features at the tenant and user level.</li><li>Plan to implement your specific requirements as part of your Teams rollout.</li><li>Communicate and publish your policies to inform Teams users of the behavior they can expect.</li></ul>|

### Teams feature management focus areas

Teams provides granular capabilities for controlling messaging, meeting, calling, and live event features and more, via policies. Different policies can be applied to all users by default or per user as required by your organization. 

For detailed lists of all settings, including technical guidance on how to implement them for your organization, see the following articles:

- [Manage Microsoft Teams settings for your organization](enable-features-office-365.md)
- [Manage Teams during the transition to the new Microsoft Teams admin center](manage-teams-skypeforbusiness-admin-center.md)
- [Private channels in Microsoft Teams](private-channels.md)
- [Shared channels in Microsoft Teams](shared-channels.md)
- [Manage meeting policies in Teams](meeting-policies-overview.md)
- [Manage messaging policies in Teams](messaging-policies-in-teams.md)
- [Manage your apps in the Microsoft Teams admin center](manage-apps.md)

Additionally, you can set up moderation for a channel and give moderator capabilities to certain users so that they can control who can create channel posts and respond to them. See [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md) for more information.

## Security and compliance

Teams is built on the advanced security and compliance capabilities of Microsoft 365 and Office 365 and supports auditing and reporting, compliance content search, e-discovery, Legal Hold, and retention policies.

> [!Important]
> If your organization has compliance and security requirements, review the in-depth content provided about this topic in the article [Overview of security and compliance in Microsoft Teams](security-compliance-overview.md).

## Related topics

[Governance quick start for Teams](teams-adoption-governance-quick-start.md)

[Microsoft 365 licensing guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

<!--
## Teams lifecycle management

In addition to planning for governance, your organization might also be interested in planning for Teams lifecycle management. For practical guidance on planning for teams lifecycle management, see [Plan for lifecycle management in Teams](plan-teams-lifecycle.md).
-->