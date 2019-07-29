---
title: Manage caller ID policies in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to use and manage caller ID policies in Microsoft Teams to change or block the caller ID of Teams users in your organization. 
---

# Manage caller ID policies in Microsoft Teams

As an admin, you can use caller ID policies in Microsoft Teams to change or block the caller ID (also known as calling line ID). By default, the phone number of Teams users can be seen when they make a call to a PSTN phone and the phone number of PSTN callers can be seen when they call a Teams user. You can use caller ID policies to display an alternate phone number for Teams users in your organization or block an incoming number from being displayed.

For example, when users make a call, you can change the caller ID to display your organization's main phone number instead of users' phone numbers.

You manage caller ID policies in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create custom policies and assign them to users. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

You can edit the global policy or create and assign a custom policy. If a user is assigned a custom policy, that policy applies to the user. If a user isn't assigned a custom policy, the global policy applies to the user. After you edit the global policy or assign a policy, it can take up to 24 hours for changes to take effect.

## Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.
2. Click **Add**.
3. Enter a name and description for the policy.
4. From here, choose the settings that you want:

- **Block incoming Caller ID**: Turn on this setting to block the caller ID of incoming calls from being displayed.
- **Users can override the Caller ID policy**: Turn on this setting to let users override the settings in the policy. This means that users can choose whether to display their caller ID or block the caller ID of an incoming call.
- **Replace Caller ID**: Set an alternate caller ID to be displayed for users by selecting one of the following:

    - **User's number**: Displays the user's number. This is the default setting.
    - **Service number**: Lets you set a service phone number to display as the caller ID.
    - **Anonymous**: Displays the caller ID as Anonymous.

- **Service number to use to replace the Caller ID**: Choose a service number to use to replace the caller ID of users. This option is available if you selected **Service number** in **Replace Caller ID**.

5. Click **Save**.

## Edit a caller ID policy

You can edit the global policy or any custom policies that you create. 

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Change the settings that you want, and then click **Save**.

## Assign a custom caller ID policy to users

You can use the Microsoft Teams admin center to assign a custom policy to one or more users or the Skype for Business PowerShell module to assign a custom policy to groups of users, such as a security group or distribution group.

### Assign a custom caller line ID policy to a user

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. Click **Policies**, and then next to **Assigned policies**, click **Edit**.
3. Under **Caller ID policy**, select the policy you want to assign, and then choose **Save**.

### Assign a custom calling line ID policy to multiple users at a time

To assign a custom calling line Id policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. Go to **Microsoft Teams admin center** > **Voice** > **Caller ID policies**.
2. Select the policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, select **Save**.

### Assign a custom caller ID policy to users in a group

You may want to assign a custom  policy to multiple users that you’ve already identified. For example, you may want to assign a policy to all users in a security group. You can do this by connecting to the Azure Active Directory PowerShell for Graph module and the Skype for Business PowerShell module. For more information about using PowerShell to manage Teams, see [Teams PowerShell Overview](teams-powershell-overview.md).

In this example, we assign a custom caller lID policy called Support Caller ID Policy to all users in the Contoso Support group.  

> [!NOTE]
> Make sure you first connect to the Azure Active Directory PowerShell for Graph module and Skype for Business PowerShell module by following the steps in [Connect to all Office 365 services in a single Windows PowerShell window](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-all-office-365-services-in-a-single-windows-powershell-window).

Get the GroupObjectId of the particular group.
```
$group = Get-AzureADGroup -SearchString "Contoso Support"
```
Get the members of the specified group.
```
$members = Get-AzureADGroupMember -ObjectId $group.ObjectId -All $true | Where-Object {$_.ObjectType -eq "User"}
```
Assign all users in the group to a particular caller ID policy. In this example, it's Support Caller ID Policy.
```
$members | ForEach-Object { Grant-CsCallingLineIdentity -PolicyName "Support Caller ID Policy" -Identity $_.EmailAddress}
``` 
Depending on the number of members in the group, this command may take several minutes to execute.

 ## Related topics

- [New-CsCallingLineIdentity](https://docs.microsoft.com/powershell/module/skype/new-cscallinglineidentity?view=skype-ps)

