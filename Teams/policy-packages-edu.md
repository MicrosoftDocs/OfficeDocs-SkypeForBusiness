---
title: Microsoft Teams policies and policy packages for EDU admins
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.reviewer: prkuch
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
- Teams_ITAdmin_RemoteWorkers
- remotework
appliesto: 
- Microsoft Teams
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.policypackages.overview
localization_priority: Priority
search.appverid: MET150
description: Learn about policies in a educational or EDU setting, and how to use and manage policy packages in Microsoft Teams. 
---

# Teams Policies and Policy Packages for Education

> [!NOTE]
> For the larger story on policies in Microsoft Teams, please review [Assign policies to your users in Microsoft Teams](assign-policies.md).

## Getting started with Microsoft Teams policy management

Microsoft Teams, at its core, is about users being able to do things like go to meetings or live events, chat, make calls, and use apps. And setting the right Microsoft Teams admin policies is a critical step in creating a safe learning environment for students within Teams. As an admin, you can use policies to control the Teams features that are available to users in your educational institute.

Here's a list of the policy areas you will find in Microsoft Teams:

- Meetings
- Live events
- Calling
- Messaging
- Teams
- App permissions


SCREENSHOT SLIDE 1

You can easily manage all Teams policies in the [Microsoft Teams admin center](https://admin.teams.microsoft.com) by signing in with your admin credentials.

## Where to find Microsoft Teams policies

Once you've logged into the Teams admin center, you'll be able to go to the policy settings for any area of Teams you need to manage, by clicking on the policy option in the left hand navigation of the Teams admin center. We've included a screenshot of the location of the messaging policies.



SCREENSHOT SLIDE 2.

## How to create and update a policy definition

Before you assign policies to your users, you need to first add and create your policy definitions for each capability area with Teams.

> [!NOTE]
> We recommend that you set different policy definitions for your students and educators.

By default, every new user will be assigned the Global (Org-wide default) policy definition for each capability area. We recommend you update the Global (Org-wide default) policy definition, then assign it to your students. If you do this, you'll then need to create a custom policy definition for each Teams capability area that can then be assigned to your educators.


SCREEN SHOT SLIDE 3

To create or edit policy definitions, go to the policy area you want to work in (for example, Messaging policies). Select **Add** if you want to create a new custom policy definition. Otherwise, to change an existing policy definition, then select **Edit**.

Whether you choose to add or edit a policy definition, you're brought to a view that lists all the policy options related to this policy area. Use this list to select what values you want set in your policy definition. Don’t forget to select **Save** before you leave the page.


SCREEN SHOT SLIDE 4

## How to assign a policy definition to a user

Once your policy definition is created or updated, you can assign it to a user by selecting **Manage users** in policy page, searching for the desired user then applying the policy.


SCREEN SHOT SLIDE 5

You can also assign a policy to a user by navigating to Users, selecting the user you wish to update policies for, selecting Policies, then Edit. From there, you can select the policy definition you’d like to use assign to the user for each capability area.

If you're part of a large educational institute, using the Microsoft Teams admin portal experience to set policies for each user may be difficult. It'll be better for you to assign policies in batches via PowerShell. We have some information on how to [Assign policies to large sets of users in your educational institute](batch-policy-assignment-edu.md) if you need it, and you can also check out the section below on policy packages, which are another great way to manage policies and settings for large groups of users.


SCREEN SHOT SLIDE 6

## Policy packages in Microsoft Teams

A policy package in Teams collects predefined policies and policy settings that you created as outlined above, and assigns them to users with similar roles in your institution. Policy packages simplify, streamline, and help provide consistency when managing policies. In normal practice, you assign each of your users a policy package, and  redefine the policies in each package as needed to suit the needs of that user group. When you update settings in a package, all users assigned to that package are changed as a bulk update.

Educational institutions in general have many users with unique needs, depending partly on the age and maturity of the students. For example, you may want to grant educators and staff full access to Microsoft Teams, but want to limit Microsoft Teams capabilities for students to encourage a safe and focused learning environment. You can use policy packages to tailor settings based on the needs of different cohorts in your educational institute community.

Just like the policy list earlier in this article, policy packages predefine policies for:

- Meetings
- Live events
- Calling
- Messaging
- Teams
- App permissions

Microsoft Teams currently includes the following policy packages:

|Package name listed in Microsoft Teams Admin center |Best used for  |Description |
|:--- |:--- |:--- |
|**Education_Teacher**| Educators and staff| Use this set of policies and policy settings to grant educators and staff within your organization full access to chat, calling and meetings through Microsoft Teams. |
|**Education_PrimaryStudent**| Primary school aged students  | Younger, primary school aged students within your institution may need more limits within Microsoft Teams. Use this set of policies and policy settings to limit capabilities like meetings creation and management,  chat management, and private calling. |
|**Education_SecondaryStudent**| Secondary school aged students | Secondary school aged students within your institution may need more limits within Microsoft Teams. Use this set of policies and policy settings to limit capabilities like meetings creation and management,  chat management, and private calling. |
|**Education_HigherEducationStudent**| Higher education students | Higher education students within your intuition may need fewer limits than younger students, but some limitations may be recommended. You can use this set of policies and policy settings to give access to chat, calling, and meetings within your  organization, but limit how your students use Microsoft Teams with external participants. |
|||

Each individual policy is given the name of the policy package so you can easily identify policies linked to a policy package. For example, when you assign the Education_Teacher policy package to educators in your educational institution, a policy named Education_Teacher is created for each policy in the package.

![Screenshot of the Education_Teacher policy package](media/policy-packages-education_teacher.png)

> [!NOTE]
> If you decide that educators and administrative support staff need different policies, you can repurpose an existing package: identify a package you aren't currently using and change the settings to be appropriate for that group. You might have to make a note to yourself which group has which package, but that's the only impediment to repurposing a package.

### Why use policy packages

DO WE NEED THIS?



If your institution has hundreds, or even thousands of users, you may be asking yourself: "Why take the time to assign one package or another to all those users?"

Assigning packages to hundreds of users is an investment in administrative time, without question. An important thing about investments is that they pay off over time, rather than immediately.

In an educational environment, there are many users with the same or similar roles. You spend less effort over time when you manage their user experience the same way. Packages group a set of policies specific to the various roles in the institution. Users with the same license, but different roles, can have relevant policies assigned based on their role, which is more efficient than tweaking policies for individual users.

Once you have all users in the institution sorted into groups and have packages applied, managing them from then on is a matter of changing the package settings once for all users assigned to the package. You can choose to fine-tune the policies within a package before or after assigning users to the package.

See [Manage policy packages in Microsoft Teams](manage-policy-packages.md) for step by step guidance on assigning single users a package, assigning packages in bulk to up to 20 users, and managing and updating the policies linked to each package.

## Policy packages that should be assigned for student safety

### Meeting policies

TWO SCREENS HERE FROM SLIDE 8, PLACEMENT.




#### Turn off the ability to create and start meetings

To ensure that students can’t schedule a meeting to communicate unattended, in meeting policies set to **Off** meeting creation capabilities through these General settings:

- **Allow Meet now in channels**: Off
- **Allow the Outlook add-in**: Off
- **Allow channel meeting scheduling**: Off
- **Allow scheduling private meetings**: Off
- (And for Participants and Guests in meeting settings): **Allow Meet now in private meetings**: Off
DO WE NEED TO CALL OUT WHERE THIS IS, THE SCREEN SHOT'S ACTUAL LOCATION IS UNCLEAR.



#### Control whether or not students can share their videos during calls and meetings

In the meeting policies section, ensure that the Audio and visual values you set for your students aligns to your educational institution’s guidelines, as well as the desires of students, educators, and parents and guardians.

You can choose from:

- **Allow transcription**: Off/On
- **Allow cloud recording**: Off/On
- **Allow IP Video**: Off/On



### Live events policies

#### Turn off the ability to create and start live events

To ensure that students can’t schedule a live events to communicate unattended, disable the **Allow scheduling** policy for students by setting it to **Off**.

SCREEN FROM SLIDE 9



### Calling policies

#### Turn off the ability to make private calls

To ensure that students can’t make private calls with other students or educators, disable the **Make private calls** policy for students by setting it to **Off**.

SCREEN FROM SLIDE 10


### Messaging policies

#### Turn off the ability to delete or edit sent messages

- For students: To make sure the messages that students send aren’t deleted or altered, students should have these settings turned **Off**:
  - **Delete sent messages**
  - **Edit sent messages**
- For educators: To make sure that educators can moderate or delete inappropriate messages students sent, educators should have these settings turned **On**:
  - **Owners can delete sent messages**
  - **Delete sent messages**
  - **Edit sent messages**

#### Control whether students can chat privately

Ensure that the **Chat On/Off** value you set for students aligns to your educational institution’s guidelines as well as the desires of students and educators. This control turns on or off the ability for a user to communicate privately in 1:1 chat or group chat in Teams.

#### Control whether students can personalize their messages

Ensure that the value you set for students aligns to your educational institution’s guidelines as well as the desires of students, educators, parents, and guardians. Our recommendation is to set **Giphy for students** to **Off**, and keep **Memes and Stickers** turned **On**.

#### Control whether students can send voice messages

Ensure that the value you set for **Create voice messages** for students aligns to your educational institution’s guidelines as well as the desires of students and educators.

#### Turn off the ability to remove users from chat for students

Students should not have the ability to remove other users from any chats they're included in. The setting for **Remove users from group chats** should be set to **Off**.

SCREEN SHOT FROM SLIDE 11, PLACEMENT?



### Teams policies

#### Turn off the ability to discover and create private channels

To ensure that students can’t create a private channel as personal space to communicate without supervision, disable the **Create private channels** policy for students.

SCREEN SHOT FROM SLIDE 12



### App permission policies

#### Control whether students can add apps within Teams

Ensure the values you set for students align to your educational institution’s guidelines. For example, if you’d like the students to be exposed to the apps you approve, you can select:

- **Microsoft apps**: **Allow all apps**
- **For Third-party apps**: **Allow specific apps and block all others**
- **For Tenant apps**: **Allow specific apps and block all others**

> [!NOTE]
> This is an example, and as stated above, you should set these policies in accordance to your educational institution's guidelines.

SCREEN SHOT FROM SLIDE 13



## What educators can do to protect students

Of course, while setting policies is a great way to proactively protect students in a Teams setting, educators are the people who are interacting with the students on a regular basis, and have a vital role to play to keep students safe. Educators should review this information to ensure they have the best experience in making sure students have the best experience when using Teams safely:

Please review the [Keeping students safe while using meetings in Teams for distance learning](https://support.office.com/article/keeping-students-safe-while-using-meetings-in-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8).
