---
title: Information barriers in Microsoft Teams preview
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 06/13/2019
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
ms.reviewer: vikramju
description: Learn about information barriers and how they affect Teams.
appliesto: 
- Microsoft Teams
---

# Information barriers in Microsoft Teams preview

> [!INCLUDE [Preview feature](includes/preview-feature.md)]

Information barriers are policies that an admin can configure to prevent individuals or groups from communicating with each other. This is useful if, for example, one department is handling information that shouldn’t be shared with other departments or a group needs to be prevented, or isolated, from communicating with anyone outside of that group.

> [!NOTE]
> - Information barrier groups cannot be created across tenants.
> - Using bots to add users is not supported in version 1.
> - Information barriers version 1 doesn't include support for SharePoint and OneDrive for Business. We are working on enabling the feature in SharePoint and will communicate once it's available.

Information barrier policies also prevent lookups and discovery. This means that if you attempt to communicate with someone you should not be communicating with, you will not find that user in the people picker.

## Background

The primary driver for Information Barriers comes from the financial services industry. The Financial Industry Regulatory Authority ([FINRA]( http://www.finra.org)) reviews information barriers and conflicts of interest within member firms and provides guidance as to how to manage such conflicts (FINRA 2241, [Debt Research Regulatory Notice 15-31](http://www.finra.org/sites/default/files/Regulatory-Notice-15-31_0.pdf).  

## When should I use information barriers?

You might want to use information barriers in situations like these:

- A team must be prevented from communicating or sharing data with a specific other team.
- A team must not communicate or share data with anyone outside of the team.

The Information Barrier Policy Evaluation Service determines whether a communication complies with information barrier policies. 

## Managing information barrier policies

Information barrier policies are managed with Security & Compliance Center (SCC) PowerShell cmdlets. For more information about using these cmdlets, see [Define policies for information barriers (Preview)](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies).

> [!IMPORTANT]
> Before you set up or define policies, **you must enable scoped directory search in Microsoft Teams**. Wait at least 24 hours after enabling scoped directory search before you set up or define policies for information barriers.

## Information barriers administrator role

The information barriers administrator role (IB Compliance Management) is responsible for managing information barrier policies. For more information about this role, see [Permissions in the Office 365 Security & Compliance Center](https://docs.microsoft.com/office365/securitycompliance/permissions-in-the-security-and-compliance-center).

## When are information barrier policies checked?

Information barrier policies are checked when the following Teams events take place:

- **Members are added to a team** - Whenever you add a user to a team, the user’s policy must be evaluated against the information barrier policies of other team members. After the user is successfully added, the user can perform all functions in the team without further checks. If the user's policy blocks them from being added to the team, the user will not show up in search.
- **A new chat is requested** - Each time a new chat is requested between two or more users, the chat is evaluated to make sure that it isn’t violating any information barrier policies. If the conversation violates an information barrier policy, then the conversation isn’t initiated, and an error message appears.
- **A user is invited to join a meeting** - When a user is invited to join a meeting, the user's policy is evaluated against the policies of other team members, and if there’s a violation, the user will not be allowed to join the meeting and will see an error message.
- **A screen is shared between two or more users** - Any time a screen is shared between two or more users, the screen share must be evaluated to make sure that it doesn’t violate the information barrier policies of other users. If an information barrier policy is violated, the screen share won’t be allowed, and an error message will appear.
- **A user places a phone call (VOIP) in Teams** - Any time a voice call is initiated by a user to another user or group of users, the call is evaluated to make sure that it doesn’t violate the information barrier policies of other team members. If there is any violation, the voice call is blocked.

## What happens to existing chat threads when a policy is changed?

When the information barrier policy admin makes changes to a policy, or a policy change kicks into effect because of a change to a user’s profile (such as for a job change or a similar reason), the Information Barrier Policy Evaluation Service automatically searches the members to ensure that members of the Team are not violating any policies.

If there is an existing chat or other communication between users, and a new policy is set or an existing policy is changed, the service evaluates existing communications to make sure that the communications are still allowed to occur. 

- **1:1 chat** - If communication between the two users is no longer allowed (if a policy blocking communication is applied to one or both users), further communication is blocked and the chat conversation will become read-only.
- **Group chat** - If communication from one user to the group is no longer allowed (for example, if a user changes jobs), the user along with the other users who violate the policy may be removed from group chat and further communication with the group will not be allowed. The user can still see old conversations (which will be read-only), but will not be able to see or participate in any new conversations with the group. If the new or changed policy preventing communication is applied to more than one user, the users who are affected by the policy may be removed from group chat. They can still see old conversations. 
- **Team** - Any users who have been removed from the group are removed from the team and will not be able to see or participate in existing or new conversations.

## What will users see if another user is blocked?

Users will experience the following if information barrier policies block another user:

- **People tab** - On the **People** tab, a user will see only those people with whom the user is allowed to chat. Blocked users will not appear.
- **Activity tab** - If the user tries to visit the **Activity** tab of a blocked user, no posts will appear. (The **Activity** tab displays channel posts only, and there would be no common channels between the two users.)
- **Org charts** - If any user tries to access an org chart on which a blocked user appears, the blocked user will not appear on the org chart and an error message will appear.
- **People card** - If a user hovers over the profile picture of a blocked user, an error message appears stating that the person is a policy-blocked user and that they cannot view or perform any action from the people card.
- **Suggested contacts** - On the Suggested contacts list, users will see only those contacts who have not been blocked.
- **Chat contacts** - The user can see blocked users on the chat contact list; however, the blocked users will be identified and the only action that the user can perform is to delete them.
- **Calls contacts** - The user can see the blocked users on the calls contact list; however, the blocked users will be identified and the only action that the user can perform is to delete them.

If you are migrating from Skype for Business to Teams, all users, even those blocked by information barrier policies, will be migrated to Teams and then will be handled as described above.

## Required licenses and permissions

Currently, the information barrier features are in public preview. When these features are generally available, they'll be included in subscriptions, such as:

- Microsoft 365 E5
- Office 365 E5
- Office 365 Advanced Compliance
- Microsoft 365 E5 Compliance

For more details, including plans and pricing, see [Compliance Solutions](https://products.office.com/business/security-and-compliance/compliance-solutions?rtc=1).

## More information

- To learn more about information barriers, see [Information barriers (Preview)](https://docs.microsoft.com/office365/securitycompliance/information-barriers).

- To set up information barrier policies, see [Define policies for information barriers (Preview)](https://docs.microsoft.com/office365/securitycompliance/information-barriers-policies)
