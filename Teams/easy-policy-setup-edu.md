---
title: Set up policies easily for a safe learning environment
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: angch, shajohri
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - remotework
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to use the Teams for Education easy policy setup tool to set up safe policy settings for students and educators in your school. 
f1keywords: 
ROBOTS: NOINDEX, NOFOLLOW
---

# Set up policies easily for a safe learning environment

## Overview

Policies in Teams let you control how Teams behaves in your environment and what features are available to users. For example, there are calling policies, meeting policies, and messaging policies, to name a few, and each policy area has settings that can be adjusted to control access.

To maintain a safe and focused learning environment, it's important to set policies to control what students can do in Teams. For example, you can use policies to control who can use private chat and private calling, who can schedule meetings, and what content types can be shared. You can also use policies to turn on Teams features that enrich the learning experience.

Policies must be adjusted for both students and educators to keep the learning experience safe. Students should get the most conservative settings with the tightest restrictions to reduce the risk of receiving inappropriate levels of access. Educators and staff need a separate set of policies with more permissive settings to be successful. For example, allow educators to schedule meetings and restrict students from doing so.

The Teams for Education easy policy setup tool simplifies managing policies for your students and educators. Use it to quickly set up the most important set of policies to create a safe and productive learning experience.  

This article walks you through how to run the tool and the steps you need to do after you run it.

> [!IMPORTANT]
> The policies applied by the tool will satisfy the needs of the majority of Teams for Education customers. The tool adjusts the Global (Org-wide default) definition of a core set of policies with settings that we recommend for student safety and applies it to students. The tool also creates and assigns a set of custom policies for educators and staff. Most Teams for Education customers won't need to use other policy assignment methods after running this tool. Use other policy assignment methods *only* if you want to configure policies for your students and staff on your own.

## Teams for Education easy policy setup tool

The easy setup tool applies a set of core policy definitions to students a separate set of core policy definitions to educators and staff, with settings that are appropriate for each. Here's what happens when you run the tool.

The tool sets up policies based on educational institution type (Primary-Secondary or Higher education). You select your institution type, and the tool does the following:

- **Students**: The tool adjusts the Global (Org-wide default) policy definition of each policy area covered by the tool with new default settings that are appropriate to keep your students safe. This ensures that your current students and all new students get the most restrictive set of policies.
- **Educators and staff**: The tool creates a set of custom policy definitions for each policy area covered by the tool with settings tailored to the needs of educators and staff. Then, it assigns the policy definitions to the group of educators and staff that you choose. In this way, your educators and staff get a more permissive set of policies to enable them to be successful.

See [Policies set up by the tool](#policies-set-up-by-the-tool) for a detailed list of policy definitions set up by the tool.

Now, let's get started!

## Run the tool

Follow these steps to run the tool. You only need to run the tool one time. 

1. In the left navigation of the Microsoft Teams admin center, go to **Dashboard**, and then in the **Easy policy setup for a safe learning environment** tile, select **Quick setup**.
2. Select your educational institution type (**Primary-Secondary** or **Higher education**), and then click **Next**.
3. Search for and select a group that contains your educators or staff, and then click **Next**. If you don’t have any groups set up yet for your educators and staff, [create a group](https://docs.microsoft.com/microsoft-365/admin/create-groups/create-groups), and then re-run the tool. <br/>Currently, you can only select one group. Educators and staff in the group you select will be assigned a set of custom policies tailored to their needs. Remember that this set of policies is separate from the policies applied to students, which the tool does automatically.
4. Review your selections.
5. Select **Apply** to apply your changes. This may take a few minutes to complete.<br/><br/>The Global (Org-wide default) policy definitions are immediately applied to students. For your educators and staff, it could take up to 48 hours for the custom policies to be assigned to each member of the group you selected, depending on the size of the group. This happens in the background, after you finish running the tool.
6. You're on your way but you're not done yet! <br/>There's a few more things to do.

    Next, make sure you follow the steps in the [What to do after running the tool](#what-to-do-after-running-the-tool) section.

## What to do after running the tool

### Step 1: Remove existing policy assignments that conflict with policies set up by the tool

> [!IMPORTANT]
> Complete this step only if you have existing policies set up *before* you ran the tool. If you're new to Teams and don't have any existing policies other than the policies created by the tool, skip this and go to step 2.

In Teams, for a given policy area, a policy can be applied to a user in the following ways:

- Direct assignment to the user
- Assignment to a group the user is a member of
- If the user isn't directly assigned a policy or isn't a member of any groups that are assigned a policy, the user automatically gets the Global (Org-wide default) policy

If more than one of these policy assignments exist for a user, Teams uses the following order to determine which policy assignment takes effect. For more info, see [Which policy takes precedence?](assign-policies.md#which-policy-takes-precedence) and [Precedence rules](assign-policies.md#precedence-rules).

|Policy assignments of a user|Policy that takes effect |
|---------|---------|
|Policy assigned to group: No<br/>Policy assigned directly to user: No    |Global (Org-wide) default policy      |
|Policy assigned to group: No<br/>Policy assigned directly to user: Yes    |Policy assigned directly to user         |
|Policy assigned to group: Yes<br/>Policy assigned directly to user: Yes     |Policy assigned directly to user         |
|Policy assigned to group: Yes<br/>Policy assigned directly to user: No     |Policy assigned to group<br/><br/>If the user is a member of multiple groups and each group is assigned a policy of the same policy area, the policy that has the highest [group assignment ranking](assign-policies.md#group-assignment-ranking) takes effect.       |

Because of this order, the policies created by the easy policy setup tool won't take effect if a user has existing direct assignments or group assignments. This means that you'll have to remove the existing policy assignments from the user so the policy set up by the tool takes effect.

For each [policy area set up by the tool](#policies-set-up-by-the-tool), do the following:

- Remove all existing direct assignments and group assignments from your students so that the Global (Org-wide default) policy definition set up by the tool takes effect.
- Remove any conflicting direct assignments for your educators and staff so that the custom policy definition created by the tool takes effect. Use the table to determine the scenarios that apply to you. <br/><br/>Keep in mind that the tool assigns policies to your educators and staff group using a [group assignment ranking](assign-policies.md#group-assignment-ranking) of 1, which is the highest ranking. If your educators and staff group has an existing policy of the same policy area assigned to it, that existing policy is moved to a lower ranking and the policy assigned by the tool takes effect. 

[Learn more](batch-group-policy-assignment-edu.md#remove-a-policy-that-was-directly-assigned-to-users) about how to remove policies that are directly assigned to users.

For example, you assigned a meeting policy directly to educators and your students have the Global (Org-wide default) meeting policy. In this scenario, remove the meeting policy that you directly assigned to educators so that the custom policy definition for the meeting policy created by the tool will take effect. You don't have to do anything with the existing Global (Org-wide default) meeting policy for students because no other meeting policies conflict with it.

### Step 2: Check for additional measures that you can take for student safety

The easy policy setup tool automatically adjusts and applies [these policies](#policies-set-up-by-the-tool). There are few additional measures which you may want to take based on the needs of your institution to stay safe.

See [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8#ID0EBBAAA) for additional safety recommendations.

### Step 3: Check Message Center for policy updates

Currently, the easy policy setup tool applies our recommended policies when you run it. It's important to know that as new policies  become available in Teams, the Global (Org-wide default) settings for student safety aren't automatically added by the tool. This capability will be available in a future release.

Until this capability is available, check [Message Center](https://admin.microsoft.com/AdminPortal/Home?#/MessageCenter) (in the Microsoft 365 admin center) frequently to stay up-to-date on new policies and policy settings in Teams. As new features become available, you may have to manually update your policies to keep your learning environment safe.

## Make changes in the tool

If you need to make changes after you run the tool, you can re-run it and change your selections. 

1. In the left navigation of the Microsoft Teams admin center, go to **Dashboard**, and then in the **Easy policy setup for a safe learning environment** tile, select **Change**.
2. From here, continue through each page of the tool to make your changes. You can change your institution type, the group of educators and staff to which you want to assign policies, or both.

The following table summarizes what happens when you make a change in the tool.

|Type of change  |Policy behavior  |
|---------|---------|
|Change the educational institution type and the educators and staff group    |<ul><li>**Students**: The Global (Org-wide default) policy definitions based on the new educational institution type are applied to students.</li><li>**Educators and staff**: A set of custom policy definitions based on the new educational institution type is created and assigned to the new educator and staff group. The previous custom policy definitions are removed from the previous educators and staff group.</li></ul>    |
|Change the educational institution type    |<ul><li>**Students**: The Global (Org-wide default) policy definitions based on the new educational institution type are applied to students.</li><li>**Educators and staff**: A set of custom policy definitions based on the new educational institution type is created and assigned to the educators and staff group. The previous custom policy definitions are removed from the  educators and staff group.</li></ul>         |
|Change the educators and staff group   |<ul><li>**Students**: No change to the Global (Org-wide default) policy definitions applied to students.</li><li>**Educators and staff**: The set of custom policy definitions is assigned to the new educators and staff group and removed from the previous educators and staff group.</li></ul>         |

## Policies set up by the tool

### Policy areas

Here's the policy areas and corresponding policy names covered by the easy policy setup tool.

#### [**Students**](#tab/Students/)

|Policy area  |Primary-Secondary policy name |Higher education policy name  |
|---------|---------|---------|
|Teams policy    |Global (Org-wide default)         |Global (Org-wide default)           |
|Meeting policy    |Global (Org-wide default)           |Global (Org-wide default)           |
|Live events policy     |Global (Org-wide default)          |  Global (Org-wide default)          |
|App setup policy     |Global (Org-wide default)           |Global (Org-wide default)           |
|App permission policy    |Global (Org-wide default)           |Global (Org-wide default)           |
|Messaging policy     |Global (Org-wide default)           |Global (Org-wide default)           |
|Calling policy    |Global (Org-wide default)           |Global (Org-wide default)           |

#### [**Educators and staff**](#tab/educators/)

|Policy area  |Primary-Secondary policy name |Higher education policy name |
|---------|---------|---------|
|Teams policy   |Primary or Secondary Educators and Staff - Teams         |Higher Education Educators and Staff - Teams         |
|Meeting policy    |Primary or Secondary Educators and Staff - Meeting         |Higher Education Educators and Staff - Meeting         |
|Live events policy   | Primary or Secondary Educators and Staff - Live events         |Higher Education Educators and Staff - Live events         |
|Messaging policy    |Primary or Secondary Educators and Staff - Messaging         | Higher Education Educators and Staff - Messaging         |
|Calling policy    |Primary or Secondary Educators and Staff - Calling         |Higher Education Educators and Staff - Calling         |

* * *

### Policy settings

Here's a summary of the settings applied by the easy policy setup tool for each policy area. 

#### [**Students**](#tab/Students/)

Here's a list of the Global (Org-wide default) policy definitions adjusted by the tool and applied to students.

|Policy area |Sub-area  |Policy setting  |Primary-Secondary |Higher education |
|---------|---------|---------|---------|---------|
|Teams policy   |         |Create private channels         |Off       |On|
|Meetings policy    |General         |Allow Meet now in channels         |Off      |On|
|  |        |Allow the Outlook add-in         |Off       |On|
|  |        |Allow channel meeting scheduling        |Off      |On|
|  |        |Allow scheduling private meetings       |Off      |On|
|  |Audio & video        |Allow transcription        |On       |On|
|  |        |Allow cloud recording         |Off      |On|
|  |        |Mode for IP audio       |Outgoing and incoming audio enabled        |Outgoing and incoming audio enabled|
|  |        |Mode for IP video         |Outgoing and incoming video enabled     |Outgoing and incoming video enabled|
|  |       |Allow IP video         |On         |On|
|  |       |Allow NDI streaming         |Off         |Off|
|  |       |Media bit rate (Kbs)         |50,000         |50,000|
|  |Content sharing       |Screen sharing mode         |Entire screen         |Entire screen|
|  |       |Allow a participant to give or request control         |On         |On|
|  |       |Allow an external participant to give or request control         |On         |On|
|  |       |Allow PowerPoint sharing        |On         |On|
|  |       |Allow whiteboard         |On         |On|
|  |       |Allow shared notes         |On        |On|
|  |Participants & guests       |Let anonymous people start a meeting       |Off         |On|
|  |       |Roles that have presenter rights in meetings        |EveryoneUserOverride         |EveryoneUserOverride|
|  |       |Automatically admit people        |EveryoneInCompany|EveryoneInCompany|
|  |       |Allow dial-in users to bypass the lobby        |Off         |Off|
|  |       |Allow Meet now in private meetings        |Off         |On|
|  |       |Enable live captions       |Disabled but user can override         |Disabled but user can override|
|  |       |Allow chat in meetings         |On         |On|
|  |Video filters mode       |VideoFiltersMode         |BlurandDefaultBackgrounds|AllFilters|
|  |Meeting attendance report       |AllowEngagementReport         |Off         |On|
|Live events policy  |       |Allow scheduling         |Off         |Off|
|  |       |Allow transcription for attendees          |On       |On|
|  |       |Who can join scheduled live events        |Everyone in organization        |Everyone in organization|
|  |       |Who can record an event         |Always         |Always|
|Messaging policy  |       |Owners can delete sent messages         |Off|On|
|  |       |Delete sent messages         |Off         |On|
|  |       |Edit sent messages         |Off         |On|
|  |       |Read receipts         |User controlled         |User controlled|
|  |       |Chat         |Off         |On|
|  |       |Use Giphys in conversations         |Off         |On|
|  |       |Giphy content rating         |Strict        |Strict|
|  |       |Use Memes in conversations         |On         |On|
|  |       |Use Stickers in conversations         |On         |On|
|  |       |Allow URL previews        |On         |On|
|  |       |Translate messages         |On         |On|
|  |       |Allow immersive reader for viewing messages        |On      |On|
|  |       |Send urgent messages using priority notifications  |Off         |On|
|  |       |Create voice messages         |Allowed in chats and channels         |Allowed in chats and channels|
|  |       |On mobile devices, display favorite channels above recent chats     |Enabled         |Enabled|
|  |       |Remove users from group chats         |Off         |On|
|  |       |Suggested replies         |???         |???|
|App permission policys  |       |Microsoft apps         |Block specific apps and allow all others > Walkie Talkie blocked         |Allow all apps|
|  |       |Third-party apps         |Allow all apps         |Allow all apps|
|  |       |Custom apps         |Allow all apps         |Allow all apps|
|App setup policy  |           |Upload custom apps           |Off         |Off|
|  |       |Allow user pinning |On         |On|
|  |       |Installed apps         |None         |None|
|  |       |Pinned apps         |Activity, Calendar, Teams         |Activity, Chats, Teams, Calendar, Calling, File
|Calling policy  |       |Make private calls         |Off        |On|
|  |       |Call forwarding and simultaneous ringing to people in your organization         |Off         |On|
|  |       |Call forwarding and simultaneous ringing to external phone numbers         |Off         |On|
|  |       |Voicemail is available for routing inbound calls         |User controlled         |User controlled|
|  |       |Inbound calls can be routed to call groups         |Off        |On|
|  |       |Allow delegation for inbound and outbound calls         |Off         |On|
|  |       |Prevent toll bypass and send calls through the PSTN        |Off         |Off|
|  |       |Busy on busy is available when in a call         |Off         |Off|
|  |       |Allow web PSTN calling         |Off         |On|

#### [**Educators and staff**](#tab/educators/)

Here's a list of the custom policy definitions applied to the educators and staff group that you choose in the tool.  

|Policy area |Sub-area  |Policy setting  |Primary-Secondary |Higher education |
|---------|---------|---------|---------|---------|
|Teams policy   |         |Create private channels         |On       |On|
|Meetings policy    |General         |Allow Meet now in channels         |On      |On|
|  |        |Allow the Outlook add-in         |On       |On|
|  |        |Allow channel meeting scheduling        |On      |On|
|  |        |Allow scheduling private meetings       |On      |On|
|  |Audio & video        |Allow transcription        |On       |On|
|  |        |Allow cloud recording         |On      |On|
|  |        |Mode for IP audio       |Outgoing and incoming audio enabled        |Outgoing and incoming audio enabled|
|  |        |Mode for IP video         |Outgoing and incoming video enabled     |Outgoing and incoming video enabled|
|  |       |Allow IP video         |On         |On|
|  |       |Allow NDI streaming         |Off         |Off|
|  |       |Media bit rate (Kbs)         |50,000         |50,000|
|  |Content sharing       |Screen sharing mode         |Entire screen         |Entire screen|
|  |       |Allow a participant to give or request control         |On         |On|
|  |       |Allow an external participant to give or request control         |On         |On|
|  |       |Allow PowerPoint sharing        |On         |On|
|  |       |Allow whiteboard         |On         |On|
|  |       |Allow shared notes         |On        |On|
|  |Participants & guests       |Let anonymous people start a meeting       |On        |On|
|  |       |Roles that have presenter rights in meetings        |OrganizerOnlyUserOverride         |OrganizerOnlyUserOverride|
|  |       |Automatically admit people        |OrganizerOnly|OrganizerOnly|
|  |       |Allow dial-in users to bypass the lobby        |Off         |Off|
|  |       |Allow Meet now in private meetings        |On         |On|
|  |       |Enable live captions       |Disabled but user can override         |Disabled but user can override|
|  |       |Allow chat in meetings         |On         |On|
|  |Video filters mode       |VideoFiltersMode         |AllFilters|AllFilters|
|  |Meeting attendance report       |AllowEngagementReport         |On         |On|
|Live events policy  |       |Allow scheduling         |On         |On|
|  |       |Allow transcription for attendees          |On       |On|
|  |       |Who can join scheduled live events        |Everyone in organization        |Everyone in organization|
|  |       |Who can record an event         |Always record         |Always record|
|Messaging policy  |       |Owners can delete sent messages         |On|On|
|  |       |Delete sent messages         |On         |On|
|  |       |Edit sent messages         |On         |On|
|  |       |Read receipts         |User controlled         |User controlled|
|  |       |Chat         |On         |On
|  |       |Use Giphys in conversations         |On        |On|
|  |       |Giphy content rating         |Strict        |Strict|
|  |       |Use Memes in conversations         |On         |On|
|  |       |Use Stickers in conversations         |On         |On|
|  |       |Allow URL previews        |On         |On|
|  |       |Translate messages         |On         |On|
|  |       |Allow immersive reader for viewing messages        |On      |On|
|  |       |Send urgent messages using priority notifications  |On         |On|
|  |       |Create voice messages         |Allowed in chats and channels         |Allowed in chats and channels|
|  |       |On mobile devices, display favorite channels above recent chats     |Enabled         |Enabled|
|  |       |Remove users from group chats         |On        |On|
|  |       |Suggested replies         |???         |???|
|Calling policy  |       |Make private calls         |On       |On|
|  |       |Call forwarding and simultaneous ringing to people in your organization         |On        |On|
|  |       |Call forwarding and simultaneous ringing to external phone numbers         |On        |On|
|  |       |Voicemail is available for routing inbound calls         |User controlled         |User controlled|
|  |       |Inbound calls can be routed to call groups         |On        |On|
|  |       |Allow delegation for inbound and outbound calls         |On         |On|
|  |       |Prevent toll bypass and send calls through the PSTN        |Off         |Off|
|  |       |Busy on busy is available when in a call         |Off         |Off|
|  |       |Allow web PSTN calling         |On      |On|

* * *

## Related topics

- [Teams policies and policy packages for Education](policy-packages-edu.md)
- [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md)
- [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8)
- [Assign policies to your users](assign-policies.md)