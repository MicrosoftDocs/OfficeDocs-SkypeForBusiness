---
title: Guest access in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: sbhatta
audience: admin
search.appverid: MET150
description: Guest access in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels.
localization_priority: Normal
f1keywords: ms.teamsadmincenter.orgwidesettings.guestaccess.overview
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
appliesto: 
  - Microsoft Teams
localization_priority: Priority
---

Guest access in Microsoft Teams
======================================

Guest access lets you add individual users from outside your organization to your teams and channels in Microsoft Teams. 

To compare external access (federation) with guest access (and decide which one you should use), read [Communicate with users from other organizations in Teams](communicate-with-users-from-other-organizations.md).

If you're ready to turn on guest access in your organization, start with the [Guest access checklist](guest-access-checklist.md).

## Guest access overview

Guest access allows teams in your organization to collaborate with people outside your organization by granting them access to existing teams and channels in Teams. Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams with full access to team chats, meetings, and files. As the Teams admin, you control which features guests can (and can't) use in Teams - check out [Manage guest access](manage-guests.md).

Guest access is an org-wide setting in Teams and is turned off by default. Guest access is subject to Azure AD and Office 365 service limits.

Guest access is included with many Office 365 subscriptions with no additional licensing requirement. For more information about licensing, see [Azure Active Directory B2B collaboration licensing guidance](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance).


> [!NOTE]
> Users in your organization who have standalone Office 365 subscription plans only, such as Exchange Online Plan 2, cannot be invited as guests to your organization because Teams considers these users to belong to the same organization. For these users to use Teams, they must be assigned an Office 365 Business Premium, Office 365 Enterprise, or Office 365 Education subscription. 


> [!IMPORTANT]
> Guest users follow Teams Org-wide settings for coexistence mode. This can't be changed.

## Who is a guest?

A guest is someone who isn't an employee, student, or member of your organization. They don't have a school or work account with your organization. For example, guests may include partners, vendors, suppliers, or consultants. Anyone who is not part of your organization can be added as guest in Teams. This means that anyone with a business account (that is, an Azure Active Directory account) or consumer email account (with Outlook.com, Gmail.com or others) can participate as a guest in Teams, with full access to teams and channel experiences. (You can read about guest restrictions in [Authorize guest access in Microsoft Teams](teams-dependencies.md).) All guests in Teams are covered by the same compliance and auditing protection as the rest of Office 365, and can be managed securely within Azure AD.

## Why use guest access?

With guest access, organizations that use Teams can provide access to teams, documents in channels, resources, chats, and applications to their partners, while maintaining complete control over their own corporate data. All guests in Teams are covered by the same compliance and auditing protection as the rest of Office 365, and guests can be managed securely within Azure AD.  

Teams is built on Office 365 Groups and provides a new way to access shared assets for an Office 365 group. Teams is the best solution for persistent chat among group/team members. Office 365 Groups is a service that provides cross-application membership for a set of shared team assets, like a SharePoint site or a Power BI dashboard, so that the team can collaborate effectively and securely. 

## Understand the limitations for guests

The guest experience has limitations by design. Make sure you understand the guest experience so you don't try to fix something that isn't a problem. For example, here's a list of some of the functionality that isn't available to a guest in Microsoft Teams:

- OneDrive for Business
- People search outside of Teams
- Calendar, Scheduled Meetings, or Meeting Details
- PSTN
- Organization chart
- Create or revise a team
- Browse for a team
- Upload files to a person-to-person chat
- Guests can still search and find users (outside their team) if they know the user's full email ID. To prevent this, IT admins can use patterns like [scoped directory search](https://docs.microsoft.com/en-us/MicrosoftTeams/teams-scoped-directory-search) that have the ability to restrict Guests into their own virtual GAL.

For more details, see [What the guest experience is like](guest-experience.md) and [Guest access in Office 365 Groups](https://support.office.com/article/guest-access-in-office-365-groups-bfc7a840-868f-4fd6-a390-f347bf51aff6).

## How does guest access compare to external access (federation)?

[!INCLUDE [guest-vs-external-access](includes/guest-vs-external-access.md)]

## More information

[Contact support for business products - Admin Help](https://docs.microsoft.com/office365/admin/contact-support-for-business-products?toc=/microsoftteams/toc.json&bc=/microsoftteams/breadcrumb/toc.json)  
[Guest access in Office 365 Groups](https://support.office.com/en-us/article/guest-access-in-office-365-groups-bfc7a840-868f-4fd6-a390-f347bf51aff6?ui=en-US&rs=en-US&ad=US#bkmk_usepowershell&PickTab=FAQ) 
  
