---
title: Microsoft Teams policy packages for EDU admins
author: jambirk
ms.author: jambirk
manager: serdars
ms.reviewer: prkuch
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
f1keywords: ms.teamsadmincenter.policypackages.overview
localization_priority: Normal
search.appverid: MET150
description: Learn how to use and manage policy packages in Microsoft Teams. 
---

# Microsoft Teams policy packages for EDU admins

A policy package in Microsoft Teams collects predefined policies and policy settings that you can assign to users with similar roles in your institution. Policy packages simplify, streamline, and help provide consistency when managing policies. In normal practice, you assign each of your users a policy package, and as necessary redefine the policies in each package to suit the needs of that user group. When you update settings in a package, all users assigned to that package are changed as a bulk update.

Educational institutions in general have many user types with unique needs, depending partly on the age and maturity of the students. For example, you may want to grant educators and staff full access to Microsoft Teams, but want to limit Microsoft Teams capabilities for students to encourage a safe and focused learning environment. You can use policy packages to tailor settings based on the needs of different cohorts in your school community.

## What is a policy package?

Policy packages let you control Microsoft Teams features that allow or restrict Microsoft Teams use for  specific sets of people in your organization. Each policy package is designed around a user role and includes predefined policies and policy settings that support activities typical for that role.

Policy packages predefine policies for:
- Messaging
- Meetings
- App Setup
- Calling
- Live events

Microsoft Teams currently includes the following policy packages:

|Package name listed in Microsoft Teams Admin center |Best used for  |Description |
|:--- |:--- |:--- |
|Education_Teacher| Educators and staff| Use this set of policies and policy settings to grant educators and staff within your organization full access to chat, calling and meetings through Microsoft Teams. |
|Education_PrimaryStudent | Primary school aged students  | Younger, primary school aged students within your institution may need more limits within Microsoft Teams. Use this set of policies and policy settings to limit capabilities like meetings creation and management,  chat management, and private calling. |
|Education_SecondaryStudent| Secondary school aged students | Secondary school aged students within your institution may need more limits within Microsoft Teams. Use this set of policies and policy settings to limit capabilities like meetings creation and management,  chat management, and private calling. |
|Education_HigherEducationStudent | Higher education students | Higher education students within your intuition may need fewer limits than younger students, but some limitations may be recommended. You can use this set of policies and policy settings to give access to chat, calling, and meetings within your  organization, but limit how your students use Microsoft Teams with external participants. |
|||

Each individual policy is given the name of the policy package so you can easily identify policies linked to a policy package. For example, when you assign the Education_Teacher policy package to teachers in your school, a policy named Education_Teacher is created for each policy in the package.

![Screenshot of the Education_Teacher policy package](media/policy-packages-education_teacher.png)

> [!NOTE]
> If you decide that teachers and administrative support staff need different policies, you can repurpose an existing package: identify a package you aren't currently using and change the settings to be appropriate for that group. You might have to make a note to yourself which group has which package, but that's the only impediment to repurposing a package.

## Why use policy packages

If your institution has hundreds, or even thousands of users, you may be asking yourself: "Why take the time to assign one package or another to all those users?"

Assigning packages to hundreds of users is an investment in administrative time, without question. An important thing about investments is that they pay off over time, rather than immediately.

In an educational environment, there are many users with the same or similar roles. You expend less effort over time when you manage their user experience the same way. Packages group a set of policies specific to the various roles in the institution. Users with the same license, but different roles, can have relevant policies assigned based on their role, which is more efficient than tweaking policies for individual users.

Once you have all users in the institution sorted into groups and have packages applied, managing them from then on is a matter of changing the package settings once for all users assigned to the package. You can choose to fine-tune the policies within a package before or after assigning users to the package.

See [Manage policy packages in Microsoft Teams](manage-policy-packages.md) for step by step guidance on assigning single users a package, assigning packages in bulk to up to 20 users, and managing and updating the policies linked to each package.
