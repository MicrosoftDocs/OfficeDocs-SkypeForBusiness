---
title: Add a guest to a team
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
search.appverid: MET150
ms.reviewer: rafarhi
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.custom: seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
description: Admins can learn how to add new guests to an organization in Microsoft Teams desktop and web clients and Azure Active Directory B2B collaboration portal.
---

# Add a guest to a team

Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams.

As an admin, you can add a new guest to the organization in a couple of ways:

- Global admins or Teams admins and team owners add a guest to a team in the Teams clients or in the Teams admin center. To learn more, read [Add guests to a team](https://support.office.com/article/add-guests-to-a-team-fccb4fa6-f864-4508-bdde-256e7384a14f). If you haven't set up guest access yet, go through the steps in the [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team).

- Add guests to your organization through Azure Active Directory (Azure AD) B2B collaboration. For details, check out [Quickstart: Add guests to your directory in the Azure portal](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

Admins can also delegate permissions to add guests to others in their organization by assigning the Guest Inviter role. For more information, see [Enable B2B external collaboration and manage who can invite guests](/azure/active-directory/external-identities/delegate-invitations).

With Azure AD B2B collaboration, organizations can enforce conditional access and multi-factor authentication (MFA) policies for B2B users. These policies can be enforced at the tenant, app, or individual user level, the same way that they are enabled for full-time employees and members of the organization. Such policies are enforced at the resource organization. For more information, see  [Conditional access for B2B collaboration users](/azure/active-directory/external-identities/conditional-access). Individual guests can't be blocked.

Guests you have already added via Azure AD B2B, Microsoft 365 Groups, or SharePoint are ready to go. The Microsoft 365 admin or a team owner can add those guests to their respective teams. If you add a guest directly to the Microsoft 365 group associated with a team, the guest will get access to the team but the Microsoft 365 group doesn't generate an invitation email to the guest, so someone on the team should notify the guest.

> [!NOTE]
> Guests are subject to  [Microsoft 365 or Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library) and [Azure Active Directory](/azure/active-directory/external-identities/current-limitations) service limits.

You can track guest additions in Azure AD or the Microsoft 365 security center. Adding a guest in Microsoft Teams is audited and logged as an Azure AD group administration activity "Added member to group". For more details, see [Auditing and reporting a B2B collaboration user](/azure/active-directory/external-identities/auditing-and-reporting) and [Search the audit log in the compliance Center](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).


## Related topics

[Authorize guest access in Microsoft Teams](teams-dependencies.md)

[Turn on or off guest access in Microsoft Teams](set-up-guests.md)