---
title: Audio Conferencing toll-free number policies
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: mshaikh
ms.date: 02/21/2024
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
ms.collection: 
  - m365initiative-meetings
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
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
description: Learn about how Audio Conferencing in Microsoft 365 or Office 365 allows users to call in to meetings from their phones.
---

# Audio Conferencing policy settings for toll and toll-free numbers

## Teams Audio Conferencing policy

Use Audio conferencing policies to manage audio conferencing toll and toll-free numbers to be displayed in meeting invites created by users within your organization. You can use one of the two automatically created policies or create and assign custom policies. The two automatically created policies are global (Org-wide default) and **`-AllowTollFreeDialInFalse`** (assigned to all existing users within the organization that aren't enabled for toll-free dial-in numbers). You manage audio conferencing policies in the Microsoft Teams admin center or by using [PowerShell](teams-powershell-overview.md).

- You can no longer manage the **`-AllowTollFreeDialIn`** setting for individual users in the Teams admin center or PowerShell. As an admin, you can only manage this setting through the new audio conferencing policy.
- The Global policy can't be modified from the Teams admin center.

> [!NOTE]
> Custom Audio Conferencing policies are not supported for customers enabled for Skype for Business Regionally Hosted Meetings. Customers enabled for Regionally Hosted Meetings can manage the Audio Conferencing settings of users via their default settings. The Audio Conferencing default settings of users can be changed in the Teams Admin Center by navigating to **Users** -> **Manage Users** -> **Select User** -> **Account**.

When a Teams audio conferencing policy is enabled in the tenant, there are two automatically created policies available in the tenant. The two automatically created policies and their default settings are:

### Global (Org-wide default)

In this policy, the value for **`-AllowTollFreeDialIn`** is set to **On** and there aren't any phone numbers defined in the policy. This is the default policy for all users in the tenant who have **`-AllowTollFreeDialIn`** set to **On**.
The policy doesn't have any phone numbers defined, so when users with this policy create a Teams meeting, the available phone numbers remain unchanged from their prior settings. These phone numbers normally default to the user’s country/region, unless changed by the Tenant admin for individual users.

For example, if a user in Germany already has German toll and toll-free numbers assigned before the Audio-conferencing policy launch, they retain these numbers after the policy is applied. Users don't notice any changes upon policy launch. However, if an admin modifies the Global Policy to include new phone numbers, all users with the assigned policy see these new numbers in their scheduled meetings.

> [!NOTE]
> If instead of Modifying the Global policy a tenant admin creates a custom policy and applies it to users, then the settings defined in the custom policy will be what the end users see in their meeting invites.

For example, if a custom policy with **`-AllowTollFreeDialInFalse`** has no defined phone numbers, users under this policy don't have toll-free numbers. Meeting invites that these users with this policy create have the same toll numbers as before the policy.
These phone numbers normally default to the user’s country/region, unless the admin makes changes for individual users.

### AllowTollFreeDialInFalse

In this policy, the value for **`-AllowTollFreeDialIn`** is set to **Off** and there aren't any phone numbers defined in the policy. This is the default policy for all users in the tenant who, at the time of launch, have **`-AllowTollFreeDialIn`** set to **Off**.

Because the policy doesn't have any phone numbers defined, when users under this policy create a Teams meeting, the available phone numbers remain unchanged from their prior settings. These phone numbers normally default to the user’s country/region, or location, unless the admin makes changes for individual users.

If a user in Germany already has a German toll phone number before an Audio Conferencing policy launch, they maintain this number under the **`-AllowTollFreeDialInFalse`** policy. Users don't notice any changes at policy launch. However, if an admin modifies the **`-AllowTollFreeDialInFalse`** policy to include specific numbers, all policy users only see those numbers in their scheduled meetings."

## Create a custom audio-conferencing policy

An overview of the steps:

1. Navigate to the Microsoft Teams admin center and  go to **Meetings** > **Audio conferencing**.
1. Select **Add**
1. Enter the name and description of the policy. The name can't contain special characters or be longer than 64 characters.
1. Choose the settings that you want.
1. Select **Save**

For example, you might have a group of users who regularly have meetings with participants from more than one country/region. In our example, the participants are from Canada, Botswana, and Singapore and they all want to join the meeting via audio conferencing by dialing a phone number. You can create a new custom policy named "Canada Botswana Singapore" and select phone numbers from these three countries/regions to be included in the policy through the **Add a phone number** option, and save this policy. You can then assign this policy to the required users.

This ensures phone numbers that you selected for Canada, Botswana, and Singapore are included in the meetings invites created by users of this policy.

### Step by step instructions on creating a custom policy based on the example

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Audio conferencing**.
2. Select **Add**.
3. Enter the name and description of the policy. The name can't contain special characters or be longer than 64 characters.
4. Choose whether or not to Include toll-free numbers in meetings created by users of this policy. Setting this to **On** lets you add toll-free phone numbers in this policy.
5. Select Add a phone number.
6. A pane opens on the right of the screen, containing the **Search by location** box.
7. Enter Canada, and select a telephone number from Canada from the results.
8. Select **Add**.
9. Repeat steps 6 and 7 in the same way to search and add telephone numbers from Botswana and Singapore.
10. Select toll-free numbers if you turned on the setting to **Include toll-free numbers in meetings created by users of this policy** in step 4.
11. Select **Add** on the bottom right-hand corner of the pane. The telephone numbers from the three countries/regions that you selected are listed.
12. There's a rank column that determines the order in which the telephone numbers are displayed in meetings invites created by users of this policy. You can change the order by selecting a phone number and moving it up or down using the **Move up** and **Move down** buttons respectively.
13. Once you put the phone numbers in the order of your preference, select **Save**.
14. Your custom policy named 'Canada Botswana Singapore' is created.
15. After creation is complete, you can assign this policy to your users.

## Edit a meeting policy

You can edit any custom policies that you create. (Note the Global policy can't be edited from the Teams admin center)

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Audio conferencing**.
1. Choose the policy you want to edit by selecting to the left of the policy name, and then selecting **Edit**.
1. Make edits.
1. Select **Save**.

> [!NOTE]
> You can't delete a policy if users are assigned to it. You'll need to assign a different policy to all affected users, and then you'l be able to delete the original policy.

## Assign a meeting policy to users

> [!IMPORTANT]
> Once a new Audio-conferencing policy is applied to a user, the phone numbers defined in the policy will only be available in new meetings created by the user with this policy. Any old and recurring meetings scheduled prior to the policy will continue to show the old settings, for example one toll and one toll-free number (if toll-free was enabled for that user). A scenario here could be that a user had **Allow Toll-Free** turned on and had a toll-free number assigned, and they created recurring meetings for future. In this scenario, if you create a custom policy with AllowTollfreeDialIn turned **Off** and apply it to this user, any new meetings created by this user won't include toll-free numbers, but the old and recurring meetings will still show toll-free numbers. So if callers dial this toll-free number to join the meeting, the call will fail because toll-free is now disabled for this user due to the policy. To prevent this, you can migrate users' old meetings after assigning them the new audio-conferencing policy. Please review [Using the Meeting Migration Service (MMS)](/SkypeForBusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).

You can assign a policy directly to users or to a group that the users are members of (if supported for the policy type), either individually or in larger numbers through a batch assignment (if supported for the policy type).

To learn about the different ways that you can assign policies to users, see [Assign policies to users and groups](assign-policies-users-and-groups.md).

> [!NOTE]
> A user can be assigned only one audio conferencing policy at a time.

> [!IMPORTANT]
> It can take up to 24 hours for the assigned phone numbers to show up on your meeting invite. If you aren't seeing updated numbers appear, please wait at least 24 hours before contacting support.

### Known issue

When you start a meeting using the **Meet now** option from **Microsoft Teams** > **Calendar** > **Meet Mow**, if you then select the ellipsis menu option, and then **Meeting Info**, there's an issue with the lower portion of the section under **Or call in (audio only)**. All phone numbers defined in the policy are shown, but the alignment of the numbers makes it difficult to read.
