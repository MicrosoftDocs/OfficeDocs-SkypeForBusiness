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

Information barriers (IB) are policies that an admin can configure to prevent individuals or groups from communicating with each other. IB is useful if, for example, one department is handling information that shouldn't be shared with other departments or a group needs to be prevented, or isolated, from communicating with anyone outside of that group.

> [!NOTE]
> - Information barrier groups cannot be created across tenants.
> - Using bots, AAD apps, and some APIs to add users is not supported in version 1.
> - Private channels are compliant to information barrier policies that you configure.
> - New: For Information about barriers support for SharePoint site connected to Teams, click [here](https://docs.microsoft.com/sharepoint/information-barriers#segments-associated-with-microsoft-teams-sites).

Information barrier policies also prevent lookups and discovery. If you attempt to communicate with someone you shouldn't be communicating with, you won't find that user in the people picker.

## Background

The primary driver for information barriers comes from the financial services industry. The Financial Industry Regulatory Authority ([FINRA]( http://www.finra.org)) reviews information barriers and conflicts of interest within member firms and provides guidance as to how to manage such conflicts (FINRA 2241, [Debt Research Regulatory Notice 15-31](http://www.finra.org/sites/default/files/Regulatory-Notice-15-31_0.pdf).  

However, since introducing information barriers, many other areas have found them to be useful. Other common scenarios include:

- Education: Students in one school aren't able to look up contact details for students of other schools.
- Legal: Maintaining confidentiality of data obtained by the lawyer of one client from being accessed by a lawyer for the same firm representing a different client.
- Government: Information access and control are limited across departments and groups.
- Professional services: A group of people in a company is only able to chat with a client or specific customer via guest access during a customer engagement.

For example, Enrico belongs to the Banking segment and Pradeep belongs to the Financial advisor segment. Enrico and Pradeep can't communicate with each other because the organization's IB policy blocks communication and collaboration between these two segments. However, Enrico and Pradeep can communicate with Lee in HR.

![Example showing information barriers preventing communication between segments](media/information-barriers-example.png)

## When to use information barriers

You might want to use information barriers in situations like these:

- A team must be prevented from communicating or sharing data with a specific other team.
- A team must not communicate or share data with anyone outside of the team.

The Information Barrier Policy Evaluation Service determines whether a communication complies with information barrier policies.

## Managing information barrier policies

Information barrier policies are managed in the Microsoft 365 Compliance Center (SCC) using PowerShell cmdlets. For more information, see [Define policies for information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

> [!IMPORTANT]
> Before you set up or define policies, **you must enable scoped directory search in Microsoft Teams**. Wait at least a few hours after enabling scoped directory search before you set up or define policies for information barriers. [Learn more about prerequisites for information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies#prerequisites).

## Information barriers administrator role

The IB Compliance Management role is responsible for managing information barrier policies. For more information about this role, see [Permissions in the Microsoft 365 Compliance Center](https://docs.microsoft.com/office365/securitycompliance/permissions-in-the-security-and-compliance-center).

## Information barrier triggers

Information barrier policies are activated when the following Teams events take place:

- **Members are added to a team** - Whenever you add a user to a team, the user's policy must be evaluated against the information barrier policies of other team members. After the user is successfully added, the user can perform all functions in the team without further checks. If the user's policy blocks them from being added to the team, the user will not show up in search.

    ![Screenshot showing group chat](media/information-barriers-add-members.png)

- **A new chat is requested** - Each time a new chat is requested between two or more users, the chat is evaluated to make sure that it isn't violating any information barrier policies. If the conversation violates an information barrier policy, then the conversation isn't initiated.

    Here's an example of a 1:1 chat.

     ![Screenshot showing blocked communication in 1:1 chat](media/information-barriers-one-one-chat.png)

    Here's an example of a group chat.

    ![Screenshot showing group chat](media/information-barriers-group-chat.png)

- **A user is invited to join a meeting** - When a user is invited to join a meeting, the user's policy is evaluated against the policies of other team members, and if there's a violation, the user will not be allowed to join the meeting.

    ![Screenshot showing user blocked from meeting](media/information-barriers-meeting.png)

- **A screen is shared between two or more users** - When a screen is shared between two or more users, the screen share must be evaluated to make sure that it doesn't violate the information barrier policies of other users. If an information barrier policy is violated, the screen share won't be allowed. 
 
    Here's an example of screen share before the policy is applied. 

    ![Screenshot showing a user chat](media/ib-before-screen-share-policy.png)

    Here's an example of screen share after the policy is applied. The screen share and call icons aren't visible.

    ![Screenshot showing user char with blocked settings](media/ib-after-screen-share-policy.png)

- **A user places a phone call (VOIP) in Teams** - Any time a voice call is initiated by a user to another user or group of users, the call is evaluated to make sure that it doesn't violate the information barrier policies of other team members. If there is any violation, the voice call is blocked.
- **Guest users in Teams** - Information barrier policies apply to guest users in Teams too. If guest users need to be discoverable in your organization's global address list, see [Manage guest access in Microsoft 365 Groups](https://docs.microsoft.com/microsoft-365/admin/create-groups/manage-guest-access-in-groups). Once guest users are discoverable, you can [define information barrier policies](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

## How policy changes impact existing chats

When the information barrier policy administrator makes changes to a policy, or a policy change kicks into effect because of a change to a user's profile (such as for a job change or a similar reason), the Information Barrier Policy Evaluation Service automatically searches the members to ensure that members of the Team are not violating any policies.

If there is an existing chat or other communication between users, and a new policy is set or an existing policy is changed, the service evaluates existing communications to make sure that the communications are still allowed to occur. 

- **1:1 chat** - If communication between the two users is no longer allowed (if a policy blocking communication is applied to one or both users), further communication is blocked and the chat conversation will become read-only. 

    Here's an example that shows the chat is visible.

    ![Screenshot showing user chat is available](media/ib-before-1-1chat-policy.png)

    Here's an example that shows the chat is disabled.

    ![Screenshot showing user chat is disabled](media/ib-after-1-1chat-policy.png)

- **Group chat** - If communication from one user to the group is no longer allowed (for example, if a user changes jobs), the user along with the other users who violate the policy may be removed from group chat and further communication with the group will not be allowed. The user can still see old conversations (read-only), but won't be able to see or participate in any new conversations with the group. If the new or changed policy preventing communication is applied to more than one user, the users who are affected by the policy may be removed from group chat. They can still see old conversations.

In this example, Enrico moved to a different department within the organization and is removed from the group chat.

  ![Screenshot showing group chat](media/information-barriers-user-changes-job.png)

Enrico can no longer send messages to the group chat.

  ![Screenshot showing group chat](media/information-barriers-user-changes-job-2.png)

- **Team** - Any users who have been removed from the group are removed from the team and will not be able to see or participate in existing or new conversations.

## Scenario: A user in an existing chat becomes blocked

Currently, users experience the following scenarios if an information barrier policy blocks another user:

- **People tab** - A user cannot see blocked users on the **People** tab.
- **People Picker** - Blocked users will not be visible in the people picker.

    ![Screenshot showing group chat](media/information-barriers-people-picker.png)
    
- **Activity tab** - If a user visits the **Activity** tab of a blocked user, no posts will appear. (The **Activity** tab displays channel posts only, and there would be no common channels between the two users.)

    Here's an example of the activity tab view that is blocked.

    ![Screenshot showing the activity tab that is blocked](media/ib-after-activity-tab-policy.png)


- **Org charts** - If a user accesses an org chart on which a blocked user appears, the blocked user won't appear on the org chart and an error message will appear instead.
- **People card** - If a user participates in a conversation and the user is subsequently blocked, other users will see an error message instead of the people card when they hover over the blocked user's name. Actions listed on the card (such as calling and chat) will be unavailable.
- **Suggested contacts** - Blocked users don't appear on the suggested contacts list (the initial contact list that appears for new users).
- **Chat contacts** - A user can see blocked users on the chats contact list, but the blocked users will be identified and the only action the user can perform is to delete them. The user can also click on them to view their past conversation.
- **Calls contacts** - A user can see blocked users on the calls contact list, but the blocked users will be identified and the only action the user can perform is to delete them.

    Here's an example of a blocked user in the calls contact list.

    ![Screenshot showing user user chat](media/ib-before-chat-contacts-policy.png)

    Here's an example of the chat being disabled for a user on the calls content list.

    ![Screenshot showing user blocked from chat](media/ib-after-chat-contacts-policy.png)

- **Skype to Teams migration** - During a Skype for Business to Teams migration, all users, even those blocked by information barrier policies, will be migrated to Teams and then will be handled as described above.

## Teams policies and SharePoint sites

When a team is created, a SharePoint site is provisioned and associated with Microsoft Teams for the files experience. Information barrier policies are not honored on this SharePoint site and files by default. To enable Information Barrier policies, the administrator has already filled out a form, requesting that IB policies be enabled on SharePoint and OneDrive (see the *Prerequisite* section in [Information barriers](https://docs.microsoft.com/sharepoint/information-barriers#prerequisites)). If the Information Barrier policy is turned on in SharePoint and OneDrive, then the IB policies will work on SharePoint sites provisioned when a team is created with Microsoft Teams.

**Example of IB policies on SharePoint site of a team**: In Contoso Bank corporation, user 'Sesha@contosobank.onmicrosoft.com' belongs to Investment Banking segment and user 'Nikita@contosobank.onmicrosoft.com' belongs to segment Advisory. The organization's IB policy blocks communication and collaboration between these two segments.
When user Sesha creates a team for Investment Banking segment, the team and the SharePoint site that backs it will be accessible only to Investment Banking segment users. User Nikita can't access that site even if she has the site link.

See the [Information barriers](https://docs.microsoft.com/sharepoint/information-barriers#segments-associated-with-microsoft-teams-sites) article for more details.

## Required licenses and permissions

For more information, including plans and pricing, see [Licensing Guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## Known Issues
- **Users can't join ad-hoc meetings**: If IB policies are enabled, users are not allowed to join meetings IF the meeting roster size is more than the [meeting attendance limits](limits-specifications-teams.md). The root cause is that IB checks rely on whether users can be added to a meeting chat roster and takes that signal to allow users to join meetings. Joining a meeting once will add that user to the roster, hence for recurring meetings, the roster fills up fast. Once it reaches the [meeting attendance limits](limits-specifications-teams.md), no additional users are allowed to be added to the meeting chat roster. If IB is enabled for the tenant and the chat roster is full for a meeting, new users (those not already on the roster) are not allowed to join the meeting. But if IB is not enabled for the tenant and the meeting chat roster is full, new users (those not already on the roster) are allowed to join the meeting, though they won't see the chat option in the meeting. A short term solution is to remove inactive members from the meeting chat roster to make space for new users. We will, however, be increasing the size of meeting chat rosters at a later date.

- **Users can't join channel meetings**: If IB policies are enabled, users are not allowed to join channel meetings IF they are not a member of the team. The root cause is that IB checks rely on whether users can be added to a meeting chat roster and takes that signal to allow users to join meetings. The chat thread in a channel meeting is available to Team/Channel members only, and non-members cannot see/access the chat thread. If IB is enabled for the tenant and a non-team member attempts to join a channel meeting, the user is not allowed to join the meeting. But if IB is not enabled for the tenant and a non-team member attempts to join a channel meeting, the user is allowed to join the meeting, however, they won't see the chat option in the meeting.

## More information

- To learn more about information barriers, see [Information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers).

- To set up information barrier policies, see [Define policies for information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

- To edit or remove information barrier policies, see [Edit (or remove) information barrier policies](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-edit-segments-policies).
