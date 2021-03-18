---
title: Information barriers in Microsoft Teams
author: chrfox
ms.author: chrfox
manager: laurawi
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
search.appverid: MET150
ms.reviewer: vikramju
f1.keywords:
- NOCSH
description: This article explains what are information barriers in Microsoft Teams and how can they affect Teams.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Information barriers in Microsoft Teams

Information barriers (IBs) are policies that an admin can configure to prevent individuals or groups from communicating with each other. IBs are useful if, for example, one department is handling information that shouldn't be shared with other departments. IBs are also useful when a group needs to be isolated or prevented from communicating with anyone outside of that group.

> [!NOTE]
> - Information barrier (IB) groups cannot be created across tenants.
> - Using bots, Azure Active Directory (Azure AD) apps, and some APIs to add users is not supported in version 1.
> - Private channels are compliant to IB policies that you configure.
> - New: For information about support for barriers for SharePoint sites that are connected to Teams, see [Segments associated with Microsoft Teams sites](https://docs.microsoft.com/sharepoint/information-barriers#segments-associated-with-microsoft-teams-sites).

IB policies also prevent lookups and discovery. If you attempt to communicate with someone you shouldn't be communicating with, you won't find that user in the people picker.

## Background

The primary driver for IBs comes from the financial services industry. The Financial Industry Regulatory Authority ([FINRA]( https://www.finra.org)) reviews IBs and conflicts of interest within member firms and provides guidance about managing such conflicts (FINRA 2241, [Debt Research Regulatory Notice 15-31](https://www.finra.org/sites/default/files/Regulatory-Notice-15-31_0.pdf).


However, since introducing IBs, many other areas have found them to be useful. Other common scenarios include:

- Education: Students in one school aren't able to look up contact details for students of other schools.

- Legal: Maintaining the confidentiality of data that is obtained by the lawyer of one client and preventing it from being accessed by a lawyer for the same firm who represents a different client.

- Government: Information access and control are limited across departments and groups.

- Professional services: A group of people in a company is only able to chat with a client or a specific customer via guest access during a customer engagement.

For example, Enrico belongs to the Banking segment and Pradeep belongs to the Financial advisor segment. Enrico and Pradeep can't communicate with each other because the organization's IB policy blocks communication and collaboration between these two segments. However, Enrico and Pradeep can communicate with Lee in HR.

![Example showing information barriers preventing communication between segments](media/information-barriers-example.png)

## When to use information barriers

You might want to use IBs in situations like these:

- A team must be prevented from communicating or sharing data with a specific other team.
- A team must not communicate or share data with anyone outside of the team.

The Information Barrier Policy Evaluation Service determines whether a communication complies with IB policies.

## Managing information barrier policies

IB policies are managed in the Microsoft 365 Compliance Center (SCC) using PowerShell cmdlets. For more information, see [Define policies for information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

> [!IMPORTANT]
> Before you set up or define policies, you must enable scoped directory search in Microsoft Teams. Wait at least a few hours after enabling scoped directory search before you set up or define policies for information barriers. For more information, see [Define information barrier policies](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies#prerequisites).

## Information barriers administrator role

The IB Compliance Management role is responsible for managing IB policies. For more information about this role, see [Permissions in the Microsoft 365 Compliance Center](https://docs.microsoft.com/office365/securitycompliance/permissions-in-the-security-and-compliance-center).

## Information barrier triggers

IB policies are activated when the following Teams events take place:

- **Members are added to a team** - Whenever you add a user to a team, the user's policy must be evaluated against the IB policies of other team members. After the user is successfully added, the user can perform all functions in the team without further checks. If the user's policy blocks them from being added to the team, the user won't show up in search.

    ![Screenshot of searching for a new member to add to a team and finding no matches](media/information-barriers-add-members.png)

- **A new chat is requested** - Each time that a user requests a new chat with one or more other users, the chat is evaluated to make sure that it isn't violating any IB policies. If the conversation violates an IB policy, then the conversation isn't started.

    Here's an example of a 1:1 chat.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing blocked communication in 1:1 chat](media/information-barriers-one-one-chat.png)

    Here's an example of a group chat.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing group chat](media/information-barriers-group-chat.png)

- **A user is invited to join a meeting** - When a user is invited to join a meeting, the IB policy that applies to the user is evaluated against the IB policies that apply to the other team members. If there's a violation, the user won't be allowed to join the meeting.

    ![Screenshot showing user blocked from meeting](media/information-barriers-meeting.png)

- **A screen is shared between two or more users** - When a user shares a screen with other users, the sharing must be evaluated to make sure that it doesn't violate the IB policies of other users. If an IB policy is violated, the screen share won't be allowed. 
 
    Here's an example of screen share before the policy is applied. 

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing a user chat](media/ib-before-screen-share-policy.png)

    Here's an example of screen share after the policy is applied. The screen share and call icons aren't visible.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing user char with blocked settings](media/ib-after-screen-share-policy.png)

- **A user places a phone call in Teams** - Whenever a user initiates a voice call (via VOIP) to another user or group of users, the call is evaluated to make sure that it doesn't violate the IB policies of other team members. If there's any violation, the voice call is blocked.

- **Guests in Teams** - IB policies apply to guests in Teams, too. If guests need to be discoverable in your organization's global address list, see [Manage guest access in Microsoft 365 Groups](https://docs.microsoft.com/microsoft-365/admin/create-groups/manage-guest-access-in-groups). Once guests are discoverable, you can [define IB policies](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

## How policy changes impact existing chats

When the IB policy administrator makes changes to a policy, or when a policy change is activated because of a change to a user's profile (such as for a job change), the Information Barrier Policy Evaluation Service automatically searches the members to ensure that their membership in the team doesn't violate any policies.

If there's an existing chat or other communication between users, and a new policy is set or an existing policy is changed, the service evaluates existing communications to make sure that the communications are still allowed to occur. 

- **1:1 chat** - If communication between two users is no longer allowed (because of application to one or both users of a policy that blocks communication), further communication is blocked. Their existing chat conversations become read-only. 

    Here's an example that shows the chat is visible.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing user chat is available](media/ib-before-1-1chat-policy.png)

    Here's an example that shows the chat is disabled.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing user chat is disabled](media/ib-after-1-1chat-policy.png)

- **Group chat** - If communication from one user to a group is no longer allowed (for example, because a user changed jobs), the user—along with the other users whose participation violates the policy—may be removed from group chat, and further communication with the group won't be allowed. The user can still see old conversations, but won't be able to see or participate in any new conversations with the group. If the new or changed policy that prevents communication is applied to more than one user, the users who are affected by the policy may be removed from group chat. They can still see old conversations.

  In this example, Enrico moved to a different department within the organization and is removed from the group chat.

  ![Screenshot of a group chat from which a user has been removed](media/information-barriers-user-changes-job.png)

  Enrico can no longer send messages to the group chat.

  ![Screenshot of not being able to send messages to group chat because the user was removed from the group](media/information-barriers-user-changes-job-2.png)

- **Team** - Any users who have been removed from the group are removed from the team and won't be able to see or participate in existing or new conversations.

## Scenario: A user in an existing chat becomes blocked

Currently, users experience the following scenarios if an IB policy blocks another user:

- **People tab** - A user can't see blocked users on the **People** tab.

- **People Picker** - Blocked users won't be visible in the people picker.

    ![Screenshot of Teams alerting the user that policy prevents display of another user's information](media/information-barriers-people-picker.png)
    
- **Activity tab** - If a user visits the **Activity** tab of a blocked user, no posts will appear. (The **Activity** tab displays channel posts only, and there would be no common channels between the two users.)

    Here's an example of the activity tab view that is blocked.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing the activity tab that is blocked](media/ib-after-activity-tab-policy.png)


- **Org charts** - If a user accesses an org chart on which a blocked user appears, the blocked user won't appear on the org chart. Instead, an error message will appear.

- **People card** - If a user participates in a conversation and the user is later blocked, other users will see an error message instead of the people card when they hover over the blocked user's name. Actions listed on the card (such as calling and chat) will be unavailable.

- **Suggested contacts** - Blocked users don't appear on the suggested contacts list (the initial contact list that appears for new users).

- **Chat contacts** - A user can see blocked users on the chats contact list, but the blocked users will be identified. The only action that the user can perform on the blocked users is to delete them. The user can also click on them to view their past conversation.

- **Calls contacts** - A user can see blocked users on the calls contact list, but the blocked users will be identified. The only action that the user can perform on the block users is to delete them.

    Here's an example of a blocked user in the calls contact list.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing user user chat](media/ib-before-chat-contacts-policy.png)

    Here's an example of the chat being disabled for a user on the calls content list.

    > [!div class="mx-imgBorder"]
    > ![Screenshot showing user blocked from chat](media/ib-after-chat-contacts-policy.png)

- **Skype to Teams migration** - During a migration from Skype for Business to Teams, all users—even those users who are blocked by IB policies—will be migrated to Teams. Those users are then handled as described above.

## Teams policies and SharePoint sites

When a team is created, a SharePoint site is provisioned and associated with Microsoft Teams for the files experience. IB policies aren't honored on this SharePoint site and files by default. To enable IB policies, the administrator has already filled out a form, requesting that IB policies be enabled on SharePoint and OneDrive (see the *Prerequisites* section in [Information barriers](https://docs.microsoft.com/sharepoint/information-barriers#prerequisites)). If the IB policy is turned on in SharePoint and OneDrive, then the IB policies will work on SharePoint sites that are provisioned when a team is created with Microsoft Teams.

**Example of IB policies on SharePoint site of a team**: In Contoso Bank corporation, user 'Sesha@contosobank.onmicrosoft.com' belongs to the Investment Banking segment and user 'Nikita@contosobank.onmicrosoft.com' belongs to the Advisory segment. The organization's IB policy blocks communication and collaboration between these two segments.
When user Sesha creates a team for the Investment Banking segment, the team and the SharePoint site that backs it will be accessible only to Investment Banking users. User Nikita can't access that site even if she has the site link.

For more information, see [Use information barriers with SharePoint](https://docs.microsoft.com/sharepoint/information-barriers#segments-associated-with-microsoft-teams-sites).

## Required licenses and permissions

For more information on licenses and permissions, including plans and pricing, see [Microsoft 365 licensing guidance for security & compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## Known Issues
- **Users can't join ad-hoc meetings**: If IB policies are enabled, users aren't allowed to join meetings if the size of the meeting roster is greater than the [meeting attendance limits](limits-specifications-teams.md). The root cause is that IB checks rely on whether users can be added to a meeting chat roster, and only when they can be added to the roster are they allowed to join the meeting. A user joining a meeting once adds that user to the roster; hence for recurring meetings, the roster can fill up fast. Once the chat roster reaches the [meeting attendance limits](limits-specifications-teams.md), no additional users are allowed to be added to the meeting. If IB is enabled for the tenant and the chat roster is full for a meeting, new users (those users who aren't already on the roster) aren't allowed to join the meeting. But if IB isn't enabled for the tenant and the meeting chat roster is full, new users (those users who aren't already on the roster) are allowed to join the meeting, though they won't see the chat option in the meeting. A short-term solution is to remove inactive members from the meeting chat roster to make space for new users. We will, however, be increasing the size of meeting chat rosters at a later date.

- **Users can't join channel meetings**: If IB policies are enabled, users aren't allowed to join channel meetings if they're not a member of the team. The root cause is that IB checks rely on whether users can be added to a meeting chat roster, and only when they can be added to the roster are they allowed to join the meeting. The chat thread in a channel meeting is available to Team/Channel members only, and non-members can't see or access the chat thread. If IB is enabled for the tenant and a non-team member attempts to join a channel meeting, that user isn't allowed to join the meeting. However, if IB is _not_ enabled for the tenant and a non-team member attempts to join a channel meeting, the user is allowed to join the meeting—but they won't see the chat option in the meeting.

- **Team owners are not removed**: If a new IB policy is applied that results in two or more conflicting segments present in a Teams channel, the segments with team owners are given higher preference and other segment users are removed. Also, at this time, team owners are not getting removed, even if they are in conflict with other owners/users. Tenant admins and other channel owners will have to remove conflicting owners manually. We are working on a fix.

## More information

- To learn more about IBs, see [Information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers).

- To set up IB policies, see [Define policies for information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

- To edit or remove IB policies, see [Edit (or remove) information barrier policies](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-edit-segments-policies).

## Availability
- The feature is available in our public cloud; in January 2021, we rolled out Information Barriers in the GCC cloud.
- The feature is not yet available in the GCCH and DOD clouds.
