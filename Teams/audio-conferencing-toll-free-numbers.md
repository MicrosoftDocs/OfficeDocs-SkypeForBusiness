---
title: "Audio Conferencing toll-free number policies"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: mshaikh
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - M365-collaboration
  - m365initiative-meetings
search.appverid: MET150
audience: admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
- CSH
ms.custom: 
  - Audio Conferencing
  - ms.teamsadmincenter.audioconferencing.overview
description: Learn about how Audio Conferencing in Microsoft 365 or Office 365 allows users call in to meetings from their phones.
---

# Audio Conferencing policy settings for toll and toll-free numbers

## Opening

Use Audio conferencing policies to manage audio conferencing toll and toll-free numbers to be displayed in meeting invites created by users within your organization. You can use one of the two automatically created policies or create and assign custom policies. The two automatically created policies are global (Org-wide default) and AllowTollFreeDialinFalse (assigned to all existing users within the organization that have set the AllowTollfreedialin policy setting to False). You manage audio conferencing policies in the Microsoft Teams admin center or by using [PowerShell](teams-powershell-overview.md).

> [!IMPORTANT]
> The Global policy cannot be modified from Teams admin center. When this feature is enabled, the setting for AllowTollFreeDialin can no longer be managed for an individual user through settings via Teams admin center nor via PowerShell. Tenant admins will only be able to manage this setting through the new audio conferencing policy.

When Teams audio conferencing policy is enabled in the tenant at that time there will be two automatically created policies that will be available in the tenant. The two automatically created policies are:

### Global (Org-wide default)

In this policy the value for **AllowTollfreedialin** will be set to ON and there will not be any phone numbers defined in the policy. This will be the default Policy for all users in the tenant who at the time of launch have **AllowTollfreedialin** set to **On**.
Since the policy doesn't have any phone numbers defined, when users of this policy create a Teams meeting, the phone numbers available in their meeting will be the same phone numbers that the users had prior to the policy. These phone numbers normally default to the user’s country/location, unless changed by the Tenant admin for individual users.

For example, if a user based out of Germany had Germany toll and toll-free phone number assigned prior to the launch of the Audio-conferencing policy, then at launch the user will be assigned the Global policy and the phone numbers they'll continue seeing in their meeting invite will be the same as before the policy was applied (That is, the German toll and toll-free numbers). An end user won't see any change when the policy is launched. If, however, a tenant admin modifies the Global Policy, and includes specific phone numbers into the policy that are different from before, then all users of the policy will only see the phone numbers that are included in the policy in any meetings they schedule.

> [!NOTE]
> If instead of Modifying the Global policy a tenant admin creates a custom policy and applies it to users, then the settings defined in the custom policy will be what the end users see in their meeting invites.

For example, if the custom policy has “AllowTollFreeDialinFalse” and has No phone numbers defined then Users of this policy will not be able to have Toll free numbers and since no phone numbers are defined in the policy the Toll phone number that will be used in meeting invites created by such users will be the same phone numbers that the users had prior to the policy. These phone numbers normally default to the user’s country/location, unless changed by the Tenant admin for individual users.

### AllowTollfreedialinFalse

In this policy the value for **AllowTollfreedialin** will be set to **Off** and there won't be any phone numbers defined in the policy. This will be the default policy for all users in the tenant who, at the time of launch, have **AllowTollfreedialin** set to **Off**.

Because the policy does not have any phone numbers defined, when users of this policy create a team meeting, the phone numbers that will be available in their meeting would be the same phone numbers that the users had prior to the policy. These phone numbers normally default to the user’s country, region, or location, unless this has been changed by the Tenant admin for individual users.

For example, If a user based out of Germany had a Germany toll phone number assigned prior to the launch of an Audio Conferencing policy, then at launch the user will be assigned the “AllowTollfreedialinFalse” policy and the phone numbers they'll continue seeing in their meeting invite will be the same as before (That is, the Germany toll number). An end user won't see any change when the policy is launched. If, however, a Tenant admin modifies the **AllowTollfreedialinFalse** policy and includes specific phone numbers into the policy then all policy users will only see the phone numbers included in the policy in any meetings they schedule.

## Create a custom audio-conferencing policy

An overview of the steps:

1. In the left navigation of the Microsoft Teams admin center, go to Meetings > Audio conferencing.
1. Select Add.
1. Enter the name and description of the policy. The name can't contain special characters or be longer than 64 characters.
1. Choose the settings that you want.
1. Select Save.

For example, you may have a group of users who regularly have meetings with participants from more than one country. In our example, the participants are from Canada, Botswana, and Singapore and they all want to join the meeting via audio conferencing by dialing a phone number. You can create a new custom policy named “Canada Botswana Singapore” and select phone numbers from these three countries to be included in the policy through the **Add a phone number** option, and save this policy. You can then assign this policy to the required users.

This ensures phone numbers that you selected for Canada, Botswana, and Singapore will be included in the meetings invites created by users of this policy.

### Step by step instructions on creating a custom policy based on the example

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Audio conferencing**.
2. Select **Add**.
3. Enter the name and description of the policy. The name can't contain special characters or be longer than 64 characters.
4. Select Add a phone number.
5. A pane will open on the right of the screen, containing the **Search by location** box.
6. Enter Canada, and select a telephone number from Canada from the results.
7. Select **Add**.
8. Repeat steps 6 and 7 in the same way to search and add telephone numbers from Botswana and Singapore.
9. Select **Add** on the bottom right-hand corner of the pane. The telephone numbers from the three countries that you selected will be listed.
10. There is a rank column that determines the order in which the telephone numbers will be displayed in meetings invites created by users of this policy. You can change the order by selecting a phone number and moving it up or down using the **Move up** and **Move down** buttons respectively.
11. Once you have put the phone numbers in the order of your preference, select **Save**.
12. Your custom policy named “Canada Botswana Singapore” is created.
13. After creation is complete, you can assign this policy to your users.

## Edit a meeting policy

You can edit any custom policies that you create. (Note the Global policy cannot be edited from the Teams admin center)

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Audio conferencing**.
1. Choose the policy you want to edit by selecting to the left of the policy name, and then selecting **Edit**.
1. Make edits.
1. Select **Save**.

> [!NOTE]
> You can't delete a policy if users are assigned to it. You'll need to assign a different policy to all affected users, and then you'l be able to delete the original policy.

## Assign a meeting policy to users

You can assign a policy directly to users or to a group that the users ar emembers of (if supported for the policy type), either individually or in larger numbers through a batch assignment (if supported for the policy type). XXX

To learn about the different ways that you can assign policies to users, see [Assign policies to users and groups](assign-policies-users-and-groups.md).

> [!NOTE]
> A user can be assigned only one audio conferencing policy at a time.
