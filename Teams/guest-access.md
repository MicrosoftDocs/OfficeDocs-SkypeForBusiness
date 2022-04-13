---
title: Guest access in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: rafarhi
audience: admin
search.appverid: MET150
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.orgwidesettings.guestaccess.overview
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
appliesto: 
  - Microsoft Teams
description: Guest access in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels.
---

# Guest access in Microsoft Teams

With guest access, you can provide access to teams, documents in channels, resources, chats, and applications to people outside your organization, while maintaining control over your corporate data. See [Set up secure collaboration with Microsoft 365 and Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams). Guest access in Teams is an organization-wide setting and is turned on by default. You can control guest access to individual teams by using [sensitivity labels](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

> [!NOTE]
> If you just want to find, call, chat, and set up meetings with people in other organizations, use [external access](manage-external-access.md).

A guest is someone who doesn't have a school or work account with your organization. For example, guests may include partners, vendors, suppliers, or consultants. Anyone who is not part of your organization can be added as guest in Teams. This means that anyone with a business account (that is, an Azure Active Directory account) or consumer email account (with Outlook.com, Gmail.com or others) can participate as a guest in Teams, with access to teams and channel experiences.

When you invite a guest to Teams, a guest account is created for them in Azure Active Directory and they are covered by the same compliance and auditing protection as other Microsoft 365 users. Guest access is subject to Azure AD and Microsoft 365 service limits.

The guest experience has limitations by design. For a full list of what a guest can and can't do in Teams, see [Guest access in Microsoft Teams](guest-experience.md).

> [!IMPORTANT]
> Guests follow Teams Org-wide settings for the coexistence Upgrade mode. This can't be changed.

To compare external access (federation) with guest access (and decide which one you should use), read [Communicate with users from other organizations in Teams](communicate-with-users-from-other-organizations.md).

Shared channels offer an alternative to guest access, allowing you to invite people outside your organization without requiring a guest account in Azure AD. To compare guest access with shared channels, see [Plan external collaboration](/microsoft-365/solutions/plan-external-collaboration).

To set up guest access, see [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team). 

## Set up guest access

Guest access in Teams requires configuring other settings in Microsoft 365, including settings in Azure AD, Microsoft 365 Groups, and SharePoint. If you're ready to start inviting guests to teams, read one of the following:

- To configure guest access for Teams for general use, see [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team).
- To collaborate with a partner organization that uses Azure Active Directory and allow guests to self-enroll for team access, see [Create a B2B extranet with managed guests](/microsoft-365/solutions/b2b-extranet).

> [!NOTE]
> If you're an administrator, and you're having trouble with Guest Access in Microsoft Teams, select **Run Tests** below, which will populate the Guest Access diagnostic in the Microsoft 365 Admin Center. These tests will check your configuration and quickly recommend next steps to enable Guest Access for your tenant.
>> [!div class="nextstepaction"]
>> [Run Tests: Guest Access](https://aka.ms/TeamsGuestAccessDiagDMC)

## How a guest gets added to a team

1. A team owner or a Microsoft 365 admin [adds a guest to a team](https://support.office.com/article/add-guests-to-a-team-fccb4fa6-f864-4508-bdde-256e7384a14f).
2. The guest receives a welcome email from the team owner, with information about the team and what to expect now that they've been added.
3. The guest accepts the invitation.
  Guests who have a work or school account in Azure Active Directory can accept the invitation and authenticate directly. Other users are sent a one-time pass code to validate their identity ([One-time passcode authentication](/azure/active-directory/external-identities/one-time-passcode) required).
4. After accepting the invitation, the guest can [participate in teams and channels](https://support.office.com/article/df38ae23-8f85-46d3-b071-cb11b9de5499), receive and respond to channel messages, [access files in channels](https://support.office.com/article/access-files-in-channels-c593c78a-27c4-4661-a598-682baa30ca7e), participate in chats, join meetings, collaborate on documents, and more. 

In Teams, guests are clearly identified. A guest's name includes the label **(Guest)**, and a channel includes an icon to indicate that there are guests on the team. For more details, see [What the guest experience is like](guest-experience.md).
  
Guests can leave the team at any time from within Teams. For details, see  [How do I leave a team?](https://support.office.com/article/leave-a-team-e481005d-3ec6-4694-b300-375472ba4076)

> [!NOTE]
> Leaving the team doesn't remove the guest account from your organization's directory. This must be done by a Microsoft 365 global admin or an Azure AD admin.

## Licensing for guest access

Guest access can be used with all Microsoft 365 Business Standard, Microsoft 365 Enterprise, and Microsoft 365 Education subscriptions. No additional Microsoft 365 license is necessary. The [billing model for Azure AD External Identities](/azure/active-directory/b2b/licensing-guidance) applies to guests in Microsoft 365. Only people from outside your organization can be invited as guests.

> [!NOTE]
> Converting a guest account into an Azure AD member account or converting an Azure AD member account into a guest is not supported by Teams.

## Guest access reviews

You can use Azure AD to create an access review for users who are in groups or have been assigned to an application. Creating recurring access reviews can save you time. If you need to routinely review users who have access to an application, a team, or a group, you can define the frequency of those reviews. 

You can perform a guest access review yourself, ask guests to review their own access, or ask an application owner or business decision maker to perform the access review. Use the Azure portal to perform guest access reviews. For more information, see [Manage guest access with Azure AD access reviews](/azure/active-directory/governance/manage-guest-access-with-access-reviews).

## Related topics

[Collaborating with people outside your organization](/microsoft-365/solutions/collaborate-with-people-outside-your-organization)

[Block guests from a specific Microsoft 365 group or Microsoft Teams team](/microsoft-365/solutions/per-group-guest-access)

[Create a secure guest sharing environment](/microsoft-365/solutions/create-secure-guest-sharing-environment)

[Contact support for business products - Admin Help](/microsoft-365/admin/contact-support-for-business-products)

[Configure Teams with three tiers of protection](/microsoft-365/solutions/configure-teams-three-tiers-protection)
