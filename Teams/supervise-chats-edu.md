---
title: Use supervised chats
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer: angch
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about supervised chats in Microsoft Teams meetings.
ms.collection: 
  - M365-collaboration
---

# Supervised chats in Microsoft Teams

Education institutions provide a safe and healthy digital space for students. The digital space includes emails, online meetings and calls, and messaging in Teams. To prevent inappropriate messaging behavior, many schools disable private chat in Teams. Unfortunately, disabling chat also blocks the opportunity for teachers to reach out to students privately for personalized learning. With chat disabled, students can't reach out to teachers when they prefer not to post the messages publicly in class teams.

Supervised chat allows designated educators to initiate chats with students and blocks students from starting new chats unless an appropriate educator is present. When chat supervision is enabled, supervisors aren't allowed to leave chats and other participants aren't allowed to remove them, ensuring that chats involving students are properly supervised.

These limitations are only applied to new private chats that are created after supervised chat has been fully enabled. They don't apply to existing private chats, meetings chats, or channels. To learn more about best practices for meeting chat, channel safety, and keeping students safe, view [Keeping students safe while using Teams](https://support.microsoft.com/topic/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8?ui=en-us&rs=en-us&ad=us#ID0EBBAAA=For_educators&ID0EDD=For_educators).

> [!Note]
> Supervised chat protects new chats created after the feature is enforced.  It doesn't protect existing chats.

## Review use cases for supervised chats

The following examples are descriptions of when a supervised chat is necessary.

- A 1.1 follow-up with an educator when students aren't comfortable sharing or asking questions publicly.

- Educators reaching out 1.1 to a student about an assignment, recent class interaction (or lack of), or other topic.

- Student group discussions monitored by an educator.

- Allow non-teaching staff to chat with student in a supervised environment.

## Enable supervised chat

> [!Note]
> Ensure that you set up chat permission roles and the role-based chat permission policies before enabling chat for your institution to avoid unwanted student access to unsupervised chats.

### Define chat permission roles for each user in your environment

For supervised chat to work as expected each user within your environment needs to be assigned the correct chat permission role. There are three roles that a user can have assigned:

- *Full permissions* – This role is ideal for educators who should have full access to students and other staff members. They can start chats with any user within your environment. Users with full permissions are expected to supervise the chats they participate in. They can't leave or be removed from chats that they start or chats that they're supervising in federated tenants.

- *Limited permissions* – This role is ideal for staff members who should only have supervised access to students and have full access to other staff and educators. They can start chats with any full or limited users but can't start chats with restricted users. If a user with full permissions begins a chat with a restricted user, limited users can be brought into the conversation. This access happens because a user with full permissions is present to supervise collaboration between limited and restricted users.

- *Restricted permissions* – This role is ideal for students who need to be supervised. They can only start chats with users who have full permissions. They can participate in any conversation that a user with full permissions starts and then invites them to. In federated chat cases, restricted users can only be added to chats by a user with full permissions who is from the restricted user’s tenant.

To set your users’ chat permission role, use the **Chat permissions** **role** policy found within your Messaging policy options in the Teams admin portal. You can use PowerShell to define roles using the ChatPermissionRole policy with the values Full, Limited, or Restricted. This policy is under CsTeamsMessagingPolicy.

To learn more about setting. Teams policies see Teams policies and policy packages for Education and Assign policies to large sets of users guides.

Roles can't be assigned to guests in your tenant. Guests are assigned the limited role.

### Allow supervised chat

Supervised chat is disabled by default for your tenant. After you've set chat permission roles for your users, you can enable supervised chat within your tenant by going to **Teams** &gt; **Teams settings** and setting **Role-based chat permissions** policy to *On.* You can also use PowerShell to enable Supervised Chat by setting AllowRoleBasedChatPermissions to True. This cmdlet is under CsTeamsClientConfiguration.

Supervised chat must be enabled for all users in the tenant and cannot be enabled for only a portion of your users.

### Enable chat

Enable chat for all your users using the existing Chat policy available in Teams admin center.

## Maintain supervised chats

After supervised chat is initially enabled, you'll need to do a few things to ensure that the chats in your environment remain supervised:

- Assign appropriate roles to any new users that join your tenant. By default, users will be assigned a restricted role.

- If a user with full permissions leaves or is removed from a tenant, the chats they were supervising will be left unattended. Before you remove the original user, ensure that another user with full permissions is added to these conversations so that the chat can remain supervised. Once the original supervisor is removed, new participants can't be added to the conversation, but current participants can continue to communicate.

## Related topics

[Supervised chats for Teams in education](https://support.microsoft.com/topic/supervised-chats-in-microsoft-teams-for-education-ad3aaafc-c85a-416f-95f9-d691f419cbb8?storagetype=live)
