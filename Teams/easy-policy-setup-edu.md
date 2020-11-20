---
title: Easy policy setup for a safe learning environment
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
---

# Easy policy setup for a safe learning environment

## Overview

Policies in Teams let you control how Teams behaves in your environment and what features are available to users. For example, there are calling policies, meeting policies, and messaging policies, to name a few, and each policy area has settings that can be adjusted to control access.

To maintain a safe and focused learning environment, it's important to set policies to control what students can do in Teams. For example, you can use policies to control who can use private chat and private calling, who can schedule meetings, and what content types can be shared. You can also use policies to turn on Teams features that enrich the learning experience.

Policies must be adjusted for both students and educators to keep the learning experience safe. Students should get the most conservative settings with the tightest restrictions to reduce the risk of receiving inappropriate levels of access. Educators and staff need a separate set of policies with more permissive settings to be successful. For example, allow educators to schedule meetings and restrict students from doing so.

The Teams for Education easy policy setup tool simplifies managing policies for your students and educators. Use it to quickly set up the most important set of policies to create a safe and productive learning experience.  

This article walks you through how to run the tool and the steps you need to do after you run it.

> [!IMPORTANT]
> The policies set up by the tool will satisfy the policy needs of the majority of Teams for Education customers. It sets up global (Org-wide default) policies that we recommend for student safety and assigns a set of custom policies for educators and staff. Most Teams for Education customers don't need to use other policy assignment methods after running this tool. Use other policy assignment methods *only* if you want to configure policies for your students and staff on your own.

## Teams for Education easy policy setup tool

The easy setup tool applies a set of core policy definitions to students a separate set of core policy definitions to educators and staff, with settings that are appropriate for each. Here's what happens when you run the tool.

The tool sets up policies based on educational institution type (Primary-Secondary or Higher education). You select your institution type, and the tool does the following:

- **Students**: The tool adjusts the Global (Org-wide default) policy definition of each policy area covered by the tool with new default settings that are appropriate to keep your students safe. This ensures that your current students and all new students get the most restrictive set of policies.
- **Educators and staff**: The tool creates a set of custom policy definitions for each policy area covered by the tool with settings tailored to the needs of educators and staff. Then, it assigns the policy definitions to the group of educators and staff that you choose. In this way, your educators and staff get a more permissive set of policies to enable them to be successful.

See [Policies set up by the tool](#policies-set-up-by-the-tool) for a detailed list of policy definitions set up by the tool.

Now, let's get started!

ADD: 
- Only to run once.
- 

## Run the tool

1. In the left navigation of the Microsoft Teams admin center, go to **Dashboard**, and then in the **Easy policy setup for a safe learning environment** tile, select **Quick setup**.
2. Select your educational institution type (**Primary-Secondary** or **Higher education**), and then click **Next**.
3. Search for and select a group that contains your educators or staff, and then click **Next**. If you don’t have any groups set up yet for your educators and staff, create one, and then re-run the tool. <br/>Currently, you can only select one group. Educators and staff in the group you select will be assigned a set of custom policies tailored to their needs. Remember that this set of policies is separate from the policies applied to students, which the tool does automatically.
4. Review your selections.
5. Select **Apply** to apply your changes. This may take a few minutes to complete.
6. You're on your way but you're not done yet! <br/>Your students and educators or staff are now set up with policies created by the tool but there's a few more things to do. 

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

Because of this order, the policies created by the easy policy setup tool won't take effect if a user has existing direct assignments or group assignments with higher [group assignment rankings](assign-policies.md#group-assignment-ranking). This means that you'll have to remove the existing policy assignments from the user so the policy set up by the tool takes effect.

For each [policy area set up by the tool](#policies-set-up-by-the-tool), do the following:

- Remove all existing policy assignments for your students so that the Global (Org-wide default) policy definition set up by the tool takes effect.
- Remove any conflicting direct or group assignments for your educators and staff so that the custom policy definition created by the tool takes effect. Use the table to determine the scenarios that apply to you. Keep in mind that the tool assigns policies to your educators and staff using a group assignment ranking of 1, which is the highest ranking.  

[Learn more](batch-group-policy-assignment-edu.md#remove-a-policy-that-was-directly-assigned-to-users) about how to remove policies that are directly assigned to users.

For example, you assigned a meeting policy directly to educators and your students have the Global (Org-wide default) meeting policy. In this scenario, remove the meeting policy that you directly assigned to educators so that the custom policy definition for the meeting policy created by the tool will take effect. You don't have to do anything with the existing Global (Org-wide default) meeting policy for students because no other meeting policies conflict with it.

### Step 2: Check for other policies that you might need to adjust

The easy policy setup tool automatically adjusts and applies [these policies](#policies-set-up-by-the-tool). There may be additional policies that you may need to manually adjust to tailor Teams to fit the needs of your students and educators. See [Policies to manually adjust](#policies-to-manually-adjust) for a list of recommended policies that you might want to adjust to stay safe.  

See [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8#ID0EBBAAA) for our full list of safety recommendations.

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

Here's a summary of the policies set up for your students and educators and staff by the easy policy setup tool. 

#### [**Students**](#tab/Students/)

Here's a list of the Global (Org-wide default) policy definitions adjusted by the tool and applied to students.

|Policy area |Sub-area  |Policy setting  |Primary-Secondary |Higher education |
|---------|---------|---------|---------|---------|
|Teams policies   |         |Create private channels         |        |
|Meetings policies    |General         |Allow Meet now in channels         |      ||
|  |        |Allow the Outlook add-in         |       ||
|  |        |Allow channel meeting scheduling         |      ||
|  |        |Allow scheduling private meetings       |         ||
|  |Audio & video        |Allow transcription         |        ||
|  |        |Allow cloud recording         |      ||
|  |        |Mode for IP audio       |        ||
|  |        |Mode for IP video         |     ||
|  |       |Allow IP video         |         ||
|  |       |Allow NDI streaming         |         ||
|  |       |Media bit rate (Kbs)         |         ||
|  |Content sharing       |Screen sharing mode         |         ||
|  |       |Allow a participant to give or request control         |         ||
|  |       |Allow PowerPoint sharing        |         ||
|  |       |Allow whiteboard         |         ||
|  |       |Allow shared notes         |         ||
|  |Participants & guests       |Let anonymous people start a meeting       |         ||
|  |       |Roles that have presenter rights in meetings        |         ||
|  |       |Automatically admit people        |         ||
|  |       |Allow dial-in users to bypass the lobby        |         ||
|  |       |Allow Meet now in private meetings        |         ||
|  |       |Enable live captions       |         ||
|  |       |Allow chat in meetings         |         ||
|  |Video filters mode       |VideoFiltersMode         |         ||
|  |Meeting attendance report       |AllowEngagementReport         |         ||
|Live events policies  |       |Allow scheduling         |         ||
|  |       |Allow transcription for attendees          |        ||
|  |       |Who can join scheduled live events        |        ||
|  |       |Who can record an event         |         ||
|Messaging policies  |       |Owners can delete sent messages         |         ||
|  |       |Delete sent messages         |         ||
|  |       |Edit sent messages         |         ||
|  |       |Read receipts         |         ||
|  |       |Chat         |         ||
|  |       |Use Giphys in conversations         |         ||
|  |       |Giphy content rating         |         ||
|  |       |Use memes in conversations         |         ||
|  |       |Use stickers in conversations         |         ||
|  |       |Allow URL previews        |         ||
|  |       |Translate messages         |         ||
|  |       |Allow immersive reader for viewing messages        |       ||
|  |       |Send urgent messages using priority notifications  |         ||
|  |       |Create voice messages         |         ||
|  |       |On mobile devices, display favorite channels above recent chats     |         ||
|  |       |Remove users from a group chat         |         ||
|  |       |Suggested replies         |         ||
|App permission polices  |       |Microsoft apps         |         ||
|  |       |Third-party apps         |         ||
|  |       |Custom apps         |         ||
|App setup polices  |           |Upload custom apps           |         ||
|  |       |Allow user pinning |         ||
|  |       |Installed apps         |         ||
|  |       |Pinned apps         |         ||
|Calling policies  |       |Make private calls         |         ||
|  |       |Call forwarding and simultaneous ringing to people in your organization         |         ||
|  |       |Call forwarding and simultaneous ringing to external phone numbers         |         ||
|  |       |Voicemail is available for routing inbound calls         |         ||
|  |       |Inbound calls can be routed to call groups         |         ||
|  |       |Allow delegation for inbound and outbound calls         |         ||
|  |       |Prevent toll bypass and send calls through the PSTN        |         ||
|  |       |Busy on busy is available when in a call         |         ||
|  |       |Allow web PSTN calling         |         ||

#### [**Educators and staff**](#tab/educators/)

Here's a list of the custom policy definitions applied to the educators and staff group that you choose in the tool.  

|Policy area |Sub-area  |Policy setting  |Primary-Secondary |Higher education |
|---------|---------|---------|---------|---------|
|Teams policies   |         |Create private channels         |        |
|Meetings policies    |General         |Allow Meet now in channels         |      ||
|  |        |Allow the Outlook add-in         |       ||
|  |        |Allow channel meeting scheduling         |      ||
|  |        |Allow scheduling private meetings       |         ||
|  |Audio & video        |Allow transcription         |        ||
|  |        |Allow cloud recording         |      ||
|  |        |Mode for IP audio       |        ||
|  |        |Mode for IP video         |     ||
|  |       |Allow IP video         |         ||
|  |       |Allow NDI streaming         |         ||
|  |       |Media bit rate (Kbs)         |         ||
|  |Content sharing       |Screen sharing mode         |         ||
|  |       |Allow a participant to give or request control         |         ||
|  |       |Allow PowerPoint sharing        |         ||
|  |       |Allow whiteboard         |         ||
|  |       |Allow shared notes         |         ||
|  |Participants & guests       |Let anonymous people start a meeting       |         ||
|  |       |Roles that have presenter rights in meetings        |         ||
|  |       |Automatically admit people        |         ||
|  |       |Allow dial-in users to bypass the lobby        |         ||
|  |       |Allow Meet now in private meetings        |         ||
|  |       |Enable live captions       |         ||
|  |       |Allow chat in meetings         |         ||
|  |Video filters mode       |VideoFiltersMode         |         ||
|  |Meeting attendance report       |AllowEngagementReport         |         ||
|Live events policies  |       |Allow scheduling         |         ||
|  |       |Allow transcription for attendees          |        ||
|  |       |Who can join scheduled live events        |        ||
|  |       |Who can record an event         |         ||
|Messaging policies  |       |Owners can delete sent messages         |         ||
|  |       |Delete sent messages         |         ||
|  |       |Edit sent messages         |         ||
|  |       |Read receipts         |         ||
|  |       |Chat         |         ||
|  |       |Use Giphys in conversations         |         ||
|  |       |Giphy content rating         |         ||
|  |       |Use memes in conversations         |         ||
|  |       |Use stickers in conversations         |         ||
|  |       |Allow URL previews        |         ||
|  |       |Translate messages         |         ||
|  |       |Allow immersive reader for viewing messages        |       ||
|  |       |Send urgent messages using priority notifications  |         ||
|  |       |Create voice messages         |         ||
|  |       |On mobile devices, display favorite channels above recent chats     |         ||
|  |       |Remove users from a group chat         |         ||
|  |       |Suggested replies         |         ||
|App permission polices  |       |Microsoft apps         |         ||
|  |       |Third-party apps         |         ||
|  |       |Custom apps         |         ||
|App setup polices  |           |Upload custom apps           |         ||
|  |       |Allow user pinning |         ||
|  |       |Installed apps         |         ||
|  |       |Pinned apps         |         ||
|Calling policies  |       |Make private calls         |         ||
|  |       |Call forwarding and simultaneous ringing to people in your organization         |         ||
|  |       |Call forwarding and simultaneous ringing to external phone numbers         |         ||
|  |       |Voicemail is available for routing inbound calls         |         ||
|  |       |Inbound calls can be routed to call groups         |         ||
|  |       |Allow delegation for inbound and outbound calls         |         ||
|  |       |Prevent toll bypass and send calls through the PSTN        |         ||
|  |       |Busy on busy is available when in a call         |         ||
|  |       |Allow web PSTN calling         |         ||

* * *

## Policies to manually adjust

Here's a list of policies that you may want to manually adjust to keep your learning environment safe.

#### [**Students**](#tab/Students/)

Here's a list of the Global (Org-wide default) policy definitions that we recommend you manually adjust for student safety.

|Policy area |Column2  |Policy setting  |Primary-Secondary |Higher education |
|---------|---------|---------|---------|---------|
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||

#### [**Educators and staff**](#tab/educators/)

Here's a list of the recommended custom policy definitions to manually set for your educators and staff.

|Policy area |Column2  |Policy setting  |Primary-Secondary |Higher education |
|---------|---------|---------|---------|---------|
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||
||         |         |         ||

* * *

## Related topics

- [Teams policies and policy packages for Education](policy-packages-edu.md)
- [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md)
- [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8)
- [Assign policies to your users](assign-policies.md)