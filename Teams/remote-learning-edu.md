---
title: Microsoft Teams resources for Education admins
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.reviewer: 
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: Remote learning startup guidance for Microsoft Teams for EDU.
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
# Get started with Microsoft Teams for remote learning

Microsoft Teams is a platform that brings conversations, content, assignments, and apps together in one place. Build collaborative classrooms, connect in professional learning communities, and connect with colleagues – all from a single experience.

Use the best practices in this article to start using Microsoft Teams for your educational needs to enable remote learning capabilities. Microsoft Teams can be used to enable class collaboration engaging students in conversations, providing a virtual meeting platform, and distributing assignments. School administrators and staff can stay up-to-date and collaborate using Teams for announcements and topical conversations. Educators can share instructional material using Professional Learning Communities.

Microsoft Teams has [clients](get-clients.md) available for desktop (Windows, Mac, and Linux), web, and mobile (Android and iOS) to make sure all your staff and students can stay connected.

## User accounts, licenses, and identity security

Microsoft Teams leverages Microsoft 365 capabilities to authenticate users and provide services. Staff, instructors, and students should have identities established to facilitate collaboration. If identities do not already exist, follow this process to establish them.

[Teams licenses need to be enabled for users](user-access.md) before they can start using Teams capabilities. Teams relies on additional Microsoft 365 capabilities such as [Office 365 groups](Office-365-groups.md), [Exchange](Exchange-Teams-interact.md), [SharePoint and OneDrive](SharePoint-OneDrive-interact.md) to enable collaborative scenarios. Users receive the best Teams experience if all these services are also enabled. [Teams is supported for users who have email hosted by Google](https://docs.microsoft.com/en-us/microsoft-365/education/deploy/enabling-teams-for-education-for-google-users).

## Easily set up Microsoft Teams

### 1. Allow users to create teams

Students and educators will get the most out of Teams when they can use it with minimal barriers and have the flexibility to tailor it to their needs. One way users can tailor their Teams experience is by having the ability to create teams that meet their needs. **By default, everyone can create Office 365 groups and Teams**. There are times when this capability may not be appropriate; for example, some customers may want to restrict primary-secondary students from creating Teams. If needed, Office 365 group and Team creation can be restricted to certain security groups within your environment.

Higher education customers benefit when you let everyone, including students, create teams for classes, research, group projects, and study groups. Primary-secondary educators may want to restrict students from creating Teams to make sure that all student to student communications are happening within a forum that include an adult. In this case, Office 365 group and Team creation can be restricted to all instructors and staff.

### 2. Configure user experiences using policies

[Teams policies](teams-policies.md) provide the ability to control the options available for specific users or groups of users. Policies can be applied to define who should be allowed to use private chat, private calling, meeting scheduling, content types that can be shared, and more.

Higher education staff, educators, and students benefit from the capabilities included with the default (global) policies. Some additional policy settings can be enabled to add more functionality to Microsoft Teams, including enabling translate capabilities in the messaging policy and allowing for automatic meeting transcription in the meeting policy.

Primary school students may need restricted capabilities provided to students. Policies set boundaries on what the students can do. Because the student population is often the largest set of users and they often receive the most restrictive settings, it is recommended that student policy changes be made to the ‘Global (Org-wide default) polices.

Here’s a set of common non-default policy configurations that would be assigned to primary-secondary students to limit unmoderated communication between students:

#### Messaging policy

- Change set to 'off'
- Giphy content rating set to 'strict'
- Translate messages set to 'on'
- Send urgent messages using priority notifications set to 'off'
- Remove users from group chats set to 'off'

#### Meeting policy

- Allow Meet now in channels set to 'off'
- Allow the Outlook add-in set to 'off'
- Allow channel meeting scheduling set to 'off'
- Allow scheduling of private meetings set to 'off'
- Allow Meet now in private meetings set to 'off'

#### Live events policy

- Allow scheduling set to 'off'

#### Calling policy

- Make private calls set to 'off'

#### Teams policy

- Create private channels set to 'off'

When restricting capabilities, primary school staff and educators should be assigned policies that give access to those core capabilities students do not have. Create new policies that allow the for private chat and meeting scheduling (the default settings for a new policy). Assign these policies to your staff and educators via security group membership.


