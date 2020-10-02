---
title: Guest access in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: sbhatta
audience: admin
search.appverid: MET150
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.orgwidesettings.guestaccess.overview
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
appliesto: 
  - Microsoft Teams
description: Guest access in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels.
---

# Guest access in Microsoft Teams

With guest access, you can provide access to teams, documents in channels, resources, chats, and applications to people outside your organization, while maintaining control over your corporate data.

A guest is someone who isn't an employee, student, or member of your organization. They don't have a school or work account with your organization. For example, guests may include partners, vendors, suppliers, or consultants. Anyone who is not part of your organization can be added as guest in Teams. This means that anyone with a business account (that is, an Azure Active Directory account) or consumer email account (with Outlook.com, Gmail.com or others) can participate as a guest in Teams, with access to teams and channel experiences.

As the Teams admin, you [control which features guests can (and can't) use in Teams](manage-guests.md). Guests in Teams are covered by the same compliance and auditing protection as the rest of Microsoft 365, and can be managed within Azure AD. Guest access is subject to Azure AD and Microsoft 365 or Office 365 service limits.

The guest experience has limitations by design. For a full list of what a guest can and can't do in Teams, see[comparison of team member and guest capabilities](guest-experience.md#comparison-of-team-member-and-guest-capabilities).

> [!IMPORTANT]
> Guest users follow Teams Org-wide settings for the coexistence Upgrade mode. This can't be changed.

To compare external access (federation) with guest access (and decide which one you should use), read [Communicate with users from other organizations in Teams](communicate-with-users-from-other-organizations.md).

## Set up guest access

Guest access in Teams requires configuring other settings in Microsoft 365, including settings in Azure AD, Microsoft 365 Groups, and SharePoint. If you're ready to start inviting guests to teams, read one of the following:

- To configure guest access for Teams for general use, see [Collaborate with guests in a team](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team).
- To collaborate with a partner organization that uses Azure Active Directory and allow guests to self-enroll for team access, see [Create a B2B extranet with managed guests](https://docs.microsoft.com/microsoft-365/solutions/b2b-extranet).

Guest access in Teams is an organization-wide setting and is turned off by default. You can control guest access to individual teams by using [sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

## Licensing for guest access

Guest access is included with all Microsoft 365 Business Standard, Microsoft 365 Enterprise, and Microsoft 365 Education subscriptions. No additional Microsoft 365 license is necessary. Teams doesn't restrict the number of guests you can add. However, the total number of guests that can be added to your tenant may be restricted by the paid features of Azure AD. For more information, see [Azure AD B2B collaboration licensing](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance).

> [!NOTE]
> Users in your organization who have standalone Microsoft 365 subscription plans only, such as Exchange Online Plan 2, cannot be invited as guests to your organization because Teams considers these users to belong to the same organization. For these users to use Teams, they must be assigned an Microsoft 365 Business Standard, Office 365 Enterprise, or Office 365 Education subscription. 

## Related topics

[Collaborating with people outside your organization](https://docs.microsoft.com/microsoft-365/solutions/collaborate-with-people-outside-your-organization)

[Block guest users from a specific Microsoft 365 group or Microsoft Teams team](https://docs.microsoft.com/microsoft-365/solutions/per-group-guest-access)

[Create a secure guest sharing environment](https://docs.microsoft.com/microsoft-365/solutions/create-secure-guest-sharing-environment)

[Contact support for business products - Admin Help](https://docs.microsoft.com/microsoft-365/admin/contact-support-for-business-products)

[Configure Teams with three tiers of protection](https://docs.microsoft.com/microsoft-365/solutions/configure-teams-three-tiers-protection)
