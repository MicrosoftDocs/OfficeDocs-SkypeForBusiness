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

Guest access allows teams in your organization to collaborate with people outside your organization by granting them access to existing teams and channels in Teams. Anyone with a business or consumer email account, such as Microsoft 365, Outlook, Gmail, or others, can participate as a guest in Teams with full access to team chats, meetings, and files. As the Teams admin, you control which features guests can (and can't) use in Teams - check out [Manage guest access](manage-guests.md).

To compare external access (federation) with guest access (and decide which one you should use), read [Communicate with users from other organizations in Teams](communicate-with-users-from-other-organizations.md).

Guest access is an org-wide setting in Teams and is turned off by default. (You can control guest access to individual teams by using [sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).)

If you're ready to start inviting guests to teams, read one of the following:

- To configure guest access for Teams for general use, see [Collaborate with guests in a team](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team).
- To collaborate with a partner organization that uses Azure Active Directory and allow guests to self-enroll for team access, see [Create a B2B extranet with managed guests](https://docs.microsoft.com/microsoft-365/solutions/b2b-extranet).

Guest access is subject to Azure AD and Microsoft 365 or Office 365 service limits.

> [!IMPORTANT]
> Guest users follow Teams Org-wide settings for the coexistence Upgrade mode. This can't be changed.

## Licensing for guest access

Guest access is included with all Microsoft 365 Business Standard, Office 365 Enterprise, and Office 365 Education subscriptions. No additional Microsoft 365 or Office 365 license is necessary. Teams doesn't restrict the number of guests you can add. However, the total number of guests that can be added to your tenant may be restricted by the paid features of Azure AD. For more information, see [Azure AD B2B collaboration licensing](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance).


> [!NOTE]
> Users in your organization who have standalone Microsoft 365 or Office 365 subscription plans only, such as Exchange Online Plan 2, cannot be invited as guests to your organization because Teams considers these users to belong to the same organization. For these users to use Teams, they must be assigned an Microsoft 365 Business Standard, Office 365 Enterprise, or Office 365 Education subscription. 

## Who is a guest?

A guest is someone who isn't an employee, student, or member of your organization. They don't have a school or work account with your organization. For example, guests may include partners, vendors, suppliers, or consultants. Anyone who is not part of your organization can be added as guest in Teams. This means that anyone with a business account (that is, an Azure Active Directory account) or consumer email account (with Outlook.com, Gmail.com or others) can participate as a guest in Teams, with full access to teams and channel experiences.

To learn more about what a guest can and can't do, read [Authorize guest access in Microsoft Teams](teams-dependencies.md). Or check out the [comparison of team member and guest capabilities](guest-experience.md#comparison-of-team-member-and-guest-capabilities) table. 

Finally, all guests in Teams are covered by the same compliance and auditing protection as the rest of Microsoft 365, and can be managed within Azure AD.

## Why use guest access?

With guest access, organizations that use Teams can provide access to teams, documents in channels, resources, chats, and applications to their partners, while maintaining complete control over their own corporate data. 

## Understand the limitations for guests

The guest experience has limitations by design. Make sure you understand the guest experience so you don't try to fix something that isn't a problem. Here's a list of some of the functionality that isn't available to a guest in Microsoft Teams:

- OneDrive
- People search outside of Teams
- Calendar, Scheduled Meetings, or Meeting Details
- PSTN
- Organization chart
- Create or revise a team
- Browse for a team
- Upload files to a person-to-person chat
- Currently, Teams supports only [State 1 and State 2 types of guest users](https://docs.microsoft.com/azure/active-directory/b2b/user-properties)

For a full list of what a guest can and can't do in Teams, see the [comparison of team member and guest capabilities](guest-experience.md#comparison-of-team-member-and-guest-capabilities) table. To learn more about guest access at the Microsoft 365 level, read [Collaborating with people outside your organization](https://docs.microsoft.com/microsoft-365/solutions/collaborate-with-people-outside-your-organization).


## Related topics

[Contact support for business products - Admin Help](https://docs.microsoft.com/microsoft-365/admin/contact-support-for-business-products)

[Configure Teams with three tiers of protection](https://docs.microsoft.com/microsoft-365/solutions/configure-teams-three-tiers-protection)
