---
title: Guest access in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: rafarhi
ms.date: 08/21/2023
audience: admin
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.orgwidesettings.guestaccess.overview
  - chat-teams-channels-revamp
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
appliesto: 
  - Microsoft Teams
description: Guest access in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels.
---

# Guest access in Microsoft Teams

With guest access, you can provide access to teams, documents in channels, resources, chats, and applications to people outside your organization, while maintaining control over your corporate data. Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams.

When you invite a guest to Teams, a guest account is created for them in Azure Active Directory and they are covered by the same compliance and auditing protection as other Microsoft 365 users. Guest access is subject to Azure AD and Microsoft 365 service limits.

If you haven't set up guest access yet, go through the steps in the [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team).

> [!NOTE]
> If you just want to find, call, chat, and set up meetings with people in other Microsoft 365 organizations, use [external access](trusted-organizations-external-meetings-chat.md).

Global administrators or Teams administrators and team owners can add a new guest to the organization in a couple of ways:

- Add a guest to a team in the Teams clients or in the Teams admin center. To learn more, read [Add guests to a team](https://support.office.com/article/fccb4fa6-f864-4508-bdde-256e7384a14f).

- Add guests to your organization without adding them to a team through Azure Active Directory (Azure AD) B2B collaboration. (For details, check out [Quickstart: Add a guest and send an invitation](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).) Teams Administrators and team owners can then add the guests to individual teams.

Admins can also delegate permissions to add guests to others in their organization by assigning the Guest Inviter role. For more information, see [Limit who can invite guests](/microsoft-365/solutions/limit-who-can-invite-guests).

With Azure AD B2B collaboration, organizations can enforce conditional access and multi-factor authentication (MFA) policies for B2B users. These policies can be enforced at the organization, app, or individual user level, the same way that they are enabled for people inside your organization. For more information, see  [Authentication and Conditional Access for External Identities](/azure/active-directory/external-identities/authentication-conditional-access). Individual guests can't be blocked.

Guests you have already added via Azure AD B2B, Microsoft 365 Groups, or SharePoint are ready to go. Team owners can add those guests to their teams. If you add a guest directly to the Microsoft 365 group associated with a team, the guest will get access to the team but the Microsoft 365 group doesn't generate an invitation email to the guest, so someone on the team should notify the guest.

### Shared channels

Shared channels offer an alternative to guest access, allowing you to invite people outside your organization without requiring a guest account in Azure AD. To compare guest access with shared channels, see [Plan external collaboration](/microsoft-365/solutions/plan-external-collaboration).

## Set up guest access

Guest access in Teams is an organization-wide setting and is turned on by default. You can control guest access to individual teams by using [sensitivity labels](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

Guest access in Teams requires configuring other settings in Microsoft 365, including settings in Azure AD, Microsoft 365 Groups, and SharePoint. If you're ready to start inviting guests to teams, read one of the following:

- To configure guest access for Teams for general use, see [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team).
- To collaborate with a partner organization that uses Azure Active Directory and allow guests to self-enroll for team access, see [Create a B2B extranet with managed guests](/microsoft-365/solutions/b2b-extranet).

See [Set up secure collaboration with Microsoft 365 and Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams) for overall information about secure collaboration using Teams.

## Guest invitation process from Teams

1. A team owner [adds a guest to a team](https://support.office.com/article/fccb4fa6-f864-4508-bdde-256e7384a14f).
1. The guest receives a welcome email from the team owner, with information about the team and what to expect now that they've been added.
1. The guest accepts the invitation.
  Guests who have a work or school account in Azure Active Directory can accept the invitation and authenticate directly. Other users are sent a one-time pass code to validate their identity ([One-time passcode authentication](/azure/active-directory/external-identities/one-time-passcode) required).
1. After accepting the invitation, the guest can participate in teams and channels, receive and respond to channel messages, [access files in channels](https://support.office.com/article/c593c78a-27c4-4661-a598-682baa30ca7e), participate in chats, join meetings, collaborate on documents, and more.

In Teams, guests are clearly identified. A guest's name includes the label **(Guest)**, and a channel includes an icon to indicate that there are guests on the team. For more details, see [What the guest experience is like](guest-experience.md).
  
Guests can leave the team at any time from within Teams. For details, see  [How do I leave a team?](https://support.office.com/article/leave-a-team-e481005d-3ec6-4694-b300-375472ba4076). (Leaving the team doesn't remove the guest account from your organization's directory. This must be done by a Microsoft 365 global admin or an Azure AD admin.)

The guest experience has limitations by design. For a full list of what a guest can and can't do in Teams, see [Guest experience in Microsoft Teams](guest-experience.md).

## Licensing for guest access

Guest access can be used with all Microsoft 365 Business Standard, Microsoft 365 Enterprise, and Microsoft 365 Education subscriptions. No additional Microsoft 365 license is necessary. The [billing model for Azure AD External Identities](/azure/active-directory/b2b/licensing-guidance) applies to guests in Microsoft 365. Only people from outside your organization can be invited as guests.

Guests are subject to  [Microsoft 365 or Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library) and [Azure Active Directory](/office365/servicedescriptions/azure-active-directory) service limits.

> [!NOTE]
> Converting a guest account into an Azure AD member account or converting an Azure AD member account into a guest is not supported by Teams.

## Diagnosing issues with Guest Access

To troubleshoot issues with inviting guests in Teams, administrators can run a diagnostic tool in the Microsoft 365 admin center to validate that guest access is correctly configured for use in Teams. 

1. Select **Run Tests** below to populate the diagnostic in the Microsoft 365 admin center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Guest Access](https://aka.ms/TeamsGuestAccessDiag)

2. The test results tell you if the tenant is configured correctly for guest access. If the tenant isn't configured correctly, the diagnostic provides information on what steps to take to address issues with the configuration.

## Tracking guests in your organization

You can track guest additions in Azure AD or the Microsoft 365 security center. Adding a guest in Teams is audited and logged as an Azure AD group administration activity "Added member to group". For more details, see [Auditing and reporting a B2B collaboration user](/azure/active-directory/external-identities/auditing-and-reporting) and [Search the audit log](/purview/audit-new-search).

### Guest access reviews

You can use Azure AD to create an access review for users who are in groups or teams or have been assigned to an application. Creating recurring access reviews can save you time. If you need to routinely review users who have access to an application, a team, or a group, you can define the frequency of those reviews.

You can perform a guest access review yourself, ask guests to review their own access, or ask an application owner or business decision maker to perform the access review. Reviews are done in Azure AD. For more information, see [Manage guest access with Azure AD access reviews](/azure/active-directory/governance/manage-guest-access-with-access-reviews).

## Related topics

[Collaborating with people outside your organization](/microsoft-365/solutions/collaborate-with-people-outside-your-organization)

[Block guests from a specific Microsoft 365 group or Microsoft Teams team](/microsoft-365/solutions/per-group-guest-access)

[Create a secure guest sharing environment](/microsoft-365/solutions/create-secure-guest-sharing-environment)

[Configure Teams with three tiers of protection](/microsoft-365/solutions/configure-teams-three-tiers-protection)

[Use guest access and external access to collaborate with people outside your organization](communicate-with-users-from-other-organizations.md)
