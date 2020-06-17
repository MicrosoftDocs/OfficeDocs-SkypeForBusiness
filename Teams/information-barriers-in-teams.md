---
title: Information barriers in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
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

Information barriers (IB) are policies that an admin can configure to prevent individuals or groups from communicating with each other. This is useful if, for example, one department is handling information that shouldn't be shared with other departments or a group needs to be prevented, or isolated, from communicating with anyone outside of that group.

> [!NOTE]
> - Information barrier segments cannot be created across tenants.
> - Using bots to add users is not supported in version 1.
> - Private channels are compliant to information barrier policies that you configure.
> - Information barrier policies do not allow blocking of communication within the same segments.
> - New: Information barrier support for SharePoint site connected to Teams is now in Private Preview. Click [here](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3-O9WDTKhhDtgWfphwS9YhUM0hJNklNRkZKMlhLNDRZNzlEQlVDSjdZVi4u) to participate in the private preview.

Information barrier policies also prevent lookups and discovery. This means that if you attempt to communicate with someone you should not be communicating with, you will not find that user in the people picker.

## Background

The primary driver for information barriers comes from the financial services industry. The Financial Industry Regulatory Authority ([FINRA]( http://www.finra.org)) reviews information barriers and conflicts of interest within member firms and provides guidance as to how to manage such conflicts (FINRA 2241, [Debt Research Regulatory Notice 15-31](http://www.finra.org/sites/default/files/Regulatory-Notice-15-31_0.pdf).  

However, since introducing information barriers, many other areas have found them to be useful. Other common scenarios include:

- Education: Students in one school aren't able to look up contact details for students of other schools.
- Legal: Maintaining confidentiality of data obtained by the lawyer of one client from being accessed by a lawyer for the same firm representing a different client.
- Government: Information access and control is limited across departments and groups.
- Professional services: A group of people in a company is only able to chat with a client or specific customer via federation or guest access during a customer engagement.

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

- **A screen is shared between two or more users** - Any time a screen is shared between two or more users, the screen share must be evaluated to make sure that it doesn't violate the information barrier policies of other users. If an information barrier policy is violated, the screen share won't be allowed.
- **A user places a phone call (VOIP) in Teams** - Any time a voice call is initiated by a user to another user or group of users, the call is evaluated to make sure that it doesn't violate the information barrier policies of other team members. If there is any violation, the voice call is blocked.
- **Guest users in Teams** - Information barrier policies apply to guest users in Teams too. If guest users need to be discoverable in your organization's global address list, see [Manage guest access in Microsoft 365 Groups](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#can-i-make-guest-objects-visible-in-the-global-address-list). Once guest users are discoverable, you can [define information barrier policies](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

## How policy changes impact existing chats

When the information barrier policy administrator makes changes to a policy, or a policy change kicks into effect because of a change to a user's profile (such as for a job change or a similar reason), the Information Barrier Policy Evaluation Service automatically searches the members to ensure that members of the Team are not violating any policies.

If there is an existing chat or other communication between users, and a new policy is set or an existing policy is changed, the service evaluates existing communications to make sure that the communications are still allowed to occur.

- **1:1 chat** - If communication between the two users is no longer allowed (if a policy blocking communication is applied to one or both users), further communication is blocked and the chat conversation will become read-only.

- **Group chat** - If communication from one user to the group is no longer allowed (for example, if a user changes jobs), the user along with the other users who violate the policy may be removed from group chat and further communication with the group will not be allowed. The user can still see old conversations (which will be read-only), but will not be able to see or participate in any new conversations with the group. If the new or changed policy preventing communication is applied to more than one user, the users who are affected by the policy may be removed from group chat. They can still see old conversations.

In this example, Enrico moved to a different department within the organization and is removed from the group chat.

  ![Screenshot showing group chat](media/information-barriers-user-changes-job.png)

Enrico can no longer send messages to the group chat.

  ![Screenshot showing group chat](media/information-barriers-user-changes-job-2.png)

- **Team** - Any users who have been removed from the group are removed from the team and will not be able to see or participate in existing or new conversations.

## Scenario: A user in an existing chat becomes blocked

Currently, users experience the following if an information barrier policy blocks another user:

- **People tab** - A user cannot see blocked users on the **People** tab.
- **People Picker** - Blocked users will not be visible in the people picker.

    ![Screenshot showing group chat](media/information-barriers-people-picker.png)
    
- **Activity tab** - If a user visits the **Activity** tab of a blocked user, no posts will appear. (The **Activity** tab displays channel posts only, and there would be no common channels between the two users.)
- **Org charts** - If a user accesses an org chart on which a blocked user appears, the blocked user will not appear on the org chart and an error message will appear instead.
- **People card** - If a user participates in a conversation and the user is subsequently blocked, other users will see an error message instead of the people card when they hover over the blocked user's name. Actions listed on the card (such as calling and chat) will be unavailable.
- **Suggested contacts** - Blocked users do not appear on the suggested contacts list (the initial contact list that appears for new users).
- **Chat contacts** - A user can see blocked users on the chats contact list, but the blocked users will be identified and the only action the user can perform is to delete them. The user can also click on them to view their past conversation.
- **Calls contacts** - A user can see blocked users on the calls contact list, but the blocked users will be identified and the only action the user can perform is to delete them.
- **Skype to Teams migration** - During a Skype for Business to Teams migration, all users, even those blocked by information barrier policies, will be migrated to Teams and then will be handled as described above.

## Teams policies and SharePoint sites

When a team is created, a SharePoint site is provisioned and associated with the Team for the files experience. Access to this SharePoint site and files honors the organization's IB, i.e., only the users whose IB segment matches per IB policy are allowed access. Even at the time of file sharing, the IB policy is honored.

For example: In Contoso Bank corporation, user 'Sesha@contosobank.onmicrosoft.com' belongs to Investment Banking segment and user 'Nikita@contosobank.onmicrosoft.com' belongs to segment Advisory. The organization's IB policy blocks communication and collaboration between these two segments.
When user Sesha creates a team for Investment Banking segment, the team and the SharePoint site that backs it will be accessible only to Investment Banking segment users. User Nikita can't access that site even if she has the site link.

## Required licenses and permissions

For more details, including plans and pricing, see [Licensing Guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## More information

- To learn more about information barriers, see [Information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers).

- To set up information barrier policies, see [Define policies for information barriers](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

- To edit or remove information barrier policies, see [Edit (or remove) information barrier policies](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-edit-segments-policies).
