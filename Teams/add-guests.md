---
title: Add a guest to a team
author: somakbhattacharyya
ms.author: sbhatta
manager: serdars
ms.date: 01/31/2018
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
ms.reviewer: sbhatta
localization_priority: Priority
description: "Learn the tools available to an admin to add new guest users to an organization, including the Microsoft Teams desktop and web clients and the Azure Active Directory B2B collaboration portal."
appliesto: 
- Microsoft Teams
---

Add a guest to a team
=====================
> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams.

As an admin, you can add a new guest user to the organization in a couple ways: 
- Global admins who are owners of a team and owners of a team can add a guest to a team through either the Microsoft Teams desktop or the web clients. For more details, check out [Add guests to a team](https://support.office.com/article/add-guests-to-a-team-fccb4fa6-f864-4508-bdde-256e7384a14f)
> [!NOTE] 
> This does not apply when AAD admins and users in the guest inviter role can invite is enabled.

- Add guests to your organization through Azure Active Directory B2B collaboration. Azure Active Directory B2B collaboration allows a global admin to invite and authorize a set of external users by uploading a comma-separated values (CSV) file of no more than 2,000 lines to the B2B collaboration portal. For more details, check out [Azure Active Directory B2B collaboration](https://go.microsoft.com/fwlink/p/?linkid=826383).

With Azure Active Directory B2B collaboration, organizations can enforce conditional access and multi-factor authentication (MFA) policies for B2B users. These policies can be enforced at the tenant, app, or individual user level, the same way that they are enabled for full-time employees and members of the organization. Such policies are enforced at the resource organization. For more information, see  [Conditional access for B2B collaboration users](https://go.microsoft.com/fwlink/?linkid=857454). Individual guest users can't be blocked.

Guest users you have already added via Azure Active Directory B2B, Office 365 Groups, or SharePoint Online are ready to go. The Office 365 admin or a team owner can add those guests to their respective teams. If a team is already with an Office 365 group, and a guest is added to the group, the guest will get access to the team. Adding a guest via the Office 365 group doesn't generate an invitation email to the guest, so someone on the team should notify the guest.

> [!NOTE]
> Guests are subject to  [Office 365](https://go.microsoft.com/fwlink/p/?linkid=282347) and [Azure Active Directory](https://go.microsoft.com/fwlink/p/?linkid=853019) service limits.

You can track guest additions in Azure Active Directory or the Office 365 Security &amp; Compliance Center. Adding a guest in Microsoft Teams is audited and logged as an Azure AD group administration activity "Added member to group". For more details, see  [Auditing and reporting a B2B collaboration user](https://go.microsoft.com/fwlink/p/?linkid=858884) and [Search the audit log in the Office 365 Security &amp; Compliance Center](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security--Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).

## Guest access vs. external access (federation)

[!INCLUDE [guest-vs-external-access](includes/guest-vs-external-access.md)]

## More information

[Authorize guest access in Microsoft Teams](teams-dependencies.md)</br>
[Turn on or off guest access in Microsoft Teams](set-up-guests.md)</br>
[Use PowerShell to control guest access to a team](guest-access-powershell.md)
