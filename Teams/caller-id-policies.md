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
description: Learn how to use and manage calling line ID policies in Microsoft Teams to change or block the caller ID of Teams users in your organization. 
---

# Manage calling line ID policies in Microsoft Teams

As an admin, you can use calling line ID policies in Microsoft Teams to change or block the calling line ID (also known as caller ID). By default, the phone number of Teams users can be seen when they make a call to a PSTN phone and the phone number of incoming calls from a PSTN caller can be seen. You can create a calling line ID policy to display an alternate phone number for Teams users in your organization or block an incoming number from being displayed.

You manage calling line ID policies in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create custom policies and assign them to users. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

[placeholder for MoPo screen shot of policy page]

You can edit the global policy or create and assign a custom policy. If a user is assigned a custom policy, that policy applies to the user. If a user isn't assigned a custom policy, the global policy applies to the user. After you edit the global policy or assign a policy, it can take up to 24 hours for changes to take effect.

## Create a custom calling ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling line ID policies**.
2. Select **New policy**.
3. Enter a descriptive name for the policy.
4. Configure the settings that you want:

- **Block incoming caller ID**: Turn this on to block the phone number of incoming calls from being displayed. 
- **
1. Specify the settings that you want, and then click **Save**.

## Edit a feedback policy

You can edit the global policy or any custom policies that you create. 

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling line ID policies**.
2. Select the policy you want to edit.
3. Change the settings that you want, and then click **Save**.

## Assign a custom calling line ID policy to users

You can use the Microsoft Teams admin center to assign a custom policy to one or more users or the Skype for Business PowerShell module to assign a custom policy to groups of users, such as a security group or distribution group.

> [!IMPORTANT]
> We recommend using PowerShell only to assign policies to users. Use the Microsoft Teams admin center to create, edit, and manage policies.

### Assign a custom calling line ID policy to a user

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. Next to **Assigned policies**, choose **Edit**.
3. Under **Teams calling line ID policies**, select the policy you want to assign, and then choose **Save**.

   <placeholder for screen shot>

### Assign a custom calling line ID policy to multiple users at a time

To assign a custom calling line Id policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. Go to **Microsoft Teams admin center** > **Voice** > **Calling line ID policies**.
2. Select the policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, select **Save**.

### Assign a custom calling line ID policy to users in a group

You may want to assign a custom  policy to multiple users that you’ve already identified. For example, you may want to assign a policy to all users in a security group. You can do this by connecting to the Azure Active Directory PowerShell for Graph module and the Skype for Business PowerShell module. For more information about using PowerShell to manage Teams, see [Teams PowerShell Overview](teams-powershell-overview.md).

In this example, we assign a custom calling line ID policy called Contoso HR to all users in the Contoso Operations group.  

> [!NOTE]
> Make sure you first connect to the Azure Active Directory PowerShell for Graph module and Skype for Business PowerShell module by following the steps in [Connect to all Office 365 services in a single Windows PowerShell window](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-all-office-365-services-in-a-single-windows-powershell-window).

Get the GroupObjectId of the particular group.
```
$group = Get-AzureADGroup -SearchString "Contoso Operations"
```
Get the members of the specified group.
```
$members = Get-AzureADGroupMember -ObjectId $group.ObjectId -All $true | Where-Object {$_.ObjectType -eq "User"}
```
Assign all users in the group to a particular feedback policy. In this example, it's Operations Updates.
```
$members | ForEach-Object { Grant-CsTeamsFeedbackPolicy -PolicyName "Operations Updates" -Identity $_.EmailAddress}
``` 
Depending on the number of members in the group, this command may take several minutes to execute.

 ## Related topics

- [New-CsCallingLineIdentity](https://docs.microsoft.com/powershell/module/skype/new-cscallinglineidentity?view=skype-ps)

