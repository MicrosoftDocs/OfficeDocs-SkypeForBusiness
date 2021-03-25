---
title: Authorize guest access in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - SPO_Content
  - m365initiative-externalcollab
ms.reviewer: rafarhi
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
description: Manage Microsoft Teams guest access features and capabilities through four different levels of authorization.
---

# Authorize guest access in Microsoft Teams

To satisfy your organization's requirements, you can manage Teams guest access features and capabilities through four different levels of authorization. All the authorization levels apply to your Microsoft 365 organization. Each authorization level controls the guest experience as shown below:

- **Azure Active Directory**: Guest access in Teams relies on the Azure AD business-to-business (B2B) platform. This authorization level controls the guest experience at the directory, tenant, and application level.
- **Teams**: Controls the guest experience in Teams only.
- **Microsoft 365 Groups**: Controls the guest experience in Microsoft 365 Groups and Teams.
- **SharePoint and OneDrive**: Controls the guest experience in SharePoint, OneDrive, Microsoft 365 Groups, and Teams.

These different authorization levels provide you with flexibility in how you set up guest access for your organization. For example, if you don't want to allow guest users in Teams but want to allow it overall in your organization, just turn off guest access in Teams. Another example: You could enable guest access at the Azure AD, Teams, and Groups levels, but then [disable the addition of guest users on selected teams that match one or more criteria such as data classification equals confidential](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites). SharePoint and OneDrive have their own guest access settings that don't rely on Microsoft 365 Groups.

For end-to-end guest access configuration instructions, see [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team).

> [!NOTE]
> Guests are subject to the service limits described in [Microsoft 365 and Office 365 service descriptions](/office365/servicedescriptions/office-365-service-descriptions-technet-library) and [Limitations of Azure AD B2B collaboration](/azure/active-directory/external-identities/current-limitations). 

The following diagram shows how guest access authorization dependency is granted and integrated between Azure Active Directory, Teams, and Microsoft 365.

> [!div class="mx-imgBorder"]
> ![Diagram of authorization dependencies for guest access.](media/teams_dependencies_image1.png)

The next diagram shows, at a high level, how the user experience works with the permission model through a typical guest access invitation and redemption flow.

> [!div class="mx-imgBorder"]
> ![Diagram of invitation and redemption flows](media/authorize-guest-image1.png)

It's important to note here that apps, bots, and connectors might require their own set of permissions and/or consent specific to the user account. These might need to be granted separately. Similarly, SharePoint might impose extra external sharing boundaries for a specific user, groups of users, or even at the site level.

The previous two diagrams are also available in [Visio](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/media/teams_dependencies.vsdx?raw=true).

## Control guest access in Azure Active Directory

Use Azure AD to determine whether external collaborators can be invited into your tenant as guests, and in what ways. For more information about Azure B2B guest access, see [What is guest user access in Azure Active Directory B2B](/azure/active-directory/b2b/what-is-b2b). For information about Azure AD roles, see [Grant permissions to users from partner organizations in your Azure Active Directory tenant](/azure/active-directory/b2b/add-guest-to-role).

The settings for invitations apply at the organization level and control the guest experience at the directory and application level. You can configure these settings in [External collaboration settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/CompanyRelationshipsMenuBlade/Settings).

Azure AD includes the following settings to configure external users:

- [Guest user access restrictions](/azure/active-directory/users-groups-roles/users-restrict-guest-permissions)

- **Admins and users in the guest inviter role can invite**: **Yes** means that admins and users in the guest inviter role will be able to invite guests to the tenant. **No** means admins and users can't invite guests to the tenant.
- **Members can invite**: To allow non-admin members of your directory to invite guests, set this policy to **Yes** (recommended). If you prefer that only admins be able to add guests, you can set this policy to **No**. Keep in mind that setting **No** will limit the guest experience for non-admin teams owners; they'll only be able to add guests in Teams that have already been added in AAD by the admin.
- **Guests can invite**: **Yes** means that guests in your directory can invite other guests to collaborate on resources secured by your Azure AD, such as SharePoint sites or Azure resources. **No** means that guests can't invite other guests to collaborate with your organization. Even if set to **Yes**, guest cannot invite other guests in Teams.
 
For more information about controlling who can invite guests, see [Enable B2B external collaboration and manage who can invite guests](/azure/active-directory/b2b/delegate-invitations).

> [!NOTE]
> You can also manage which domains can be invited into your tenant as guests. See [Allow or block invitations to B2B users from specific organizations](/azure/active-directory/external-identities/allow-deny-list).

Adding the user guest account manually to Azure AD B2B is not required, as the account will be added to the directory automatically when you add the guest to Teams.

### Licensing for guest access

Guest access licensing uses Azure AD External Identities pricing and is based on monthly active guests. See [Billing model for Azure AD External Identities](/azure/active-directory/external-identities/external-identities-pricing) for details.

> [!NOTE]
> Users in your organization who have standalone Office 365 subscription plans only, such as Exchange Online Plan 2, cannot be invited as guests to your organization because Teams considers these users to belong to the same organization. For these users to use Teams, they must be assigned an Microsoft 365 Business Standard, Office 365 Enterprise, or Office 365 Education subscription. 

## External access (federation) vs. guest access

[!INCLUDE [guest-vs-external-access](includes/guest-vs-external-access.md)]

## Related topics

- [Microsoft 365 guest sharing settings reference](/Office365/Enterprise/microsoft-365-guest-settings)

[Set up secure collaboration with Microsoft 365](/microsoft-365/solutions/setup-secure-collaboration-with-teams)