---
title: Manage emergency call policies in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: jastark, roykuntz
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
description: Learn how to use and manage emergency call policies for the Dynamic E911 feature in Microsoft Teams. 
f1keywords: ms.teamsadmincenter.voice.emergencycallingpolicies.overview
---

# Manage emergency calling policies in Microsoft Teams

If your organization uses Calling Plans or deployed Phone System Direct Routing, you can use emergency calling policies in Microsoft Teams to define what happens when a Teams user in your organization makes an emergency call. You can set who to notify and how they are notified when a user who is assigned the policy calls emergency services. For example, you can configure policy settings to automatically notify your organization's security desk and have them listen in emergency calls.  

You manage emergency calling policies by going to **Voice** > **Emergency policies** in the Microsoft Teams admin center or by using Windows PowerShell. The policies can be assigned to users and [network sites](location-based-routing-terminology.md).

For users, you can use the global (Org-wide default) policy or create and assign custom policies. Users will automatically get the global policy unless you create and assign a custom policy. Keep in mind that you can edit the settings in the global policy but you can't rename or delete it. For network sites, you create and assign custom policies.

If you assigned an emergency calling policy to a network site and to a user and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.

## Create a custom emergency calling policy

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Calling policies** tab.
2. Click **Add**.
3. Enter a name and description for the policy.
4. Set how you want to notify people in your organization, typically the security desk, when an emergency call is made. To do this, under **Notification mode**, select one of the following:
    - **Notification only**: A Teams chat message is sent to the users and groups that you specify.
    - **Conferenced in but are muted**: A Teams chat message is sent to the users and groups that you specify and they can listen (but not participate) in the conversation between the caller and the PSAP operator.
5.  If you selected the **Conferenced in but are muted** notification mode, in the **Dial-out number for notifications** box, you can enter a PSTN phone number of a user or group to call and join the emergency call. For example, enter the number of your organization's security desk, who will receive a call when an emergency call is made and can then listen in or participate in the call.
6. Search for and select one or more users or groups, such as your organization's security desk, to notify when an emergency call is made.  The notification can be sent to email addresses of users, distribution groups, and security groups. A maximum of 50 users can be notified.
7. Click **Save**.

### Using PowerShell

See [New-CsTeamsEmergencyCallingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsemergencycallingpolicy).

## Edit an emergency calling policy

### Using the Microsoft Teams admin center

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Calling policies** tab.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Make the changes that you want, and then click **Save**.

### Using PowerShell

See [Set-CsTeamsEmergencyCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsemergencycallingpolicy).

## Assign a custom emergency calling policy to users

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. Click **Policies**, and then next to **Assigned policies**, click **Edit**.
3. Under **Emergency calling policy**, select the policy you want to assign, and then click **Save**.

To assign a custom teams policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Calling policies** tab.
2. Select the policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, click **Save**.

### Using PowerShell

#### Assign a custom emergency calling policy to a user

See [Grant-CsTeamsEmergencyCallingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsemergencycallingpolicy).

#### Assign a custom emergency calling policy to users in a group

You may want to assign a custom emergency calling policy to multiple users that you’ve already identified. For example, you may want to assign a policy to all users in a security group. You can do this by connecting to the Azure Active Directory PowerShell for Graph module and the Skype for Business PowerShell module.

In this example, we assign a policy called Operations Emergency Calling Policy to all users in the Contoso Operations group.  

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
Assign all users in the group to a particular teams policy. In this example, it's Operations Emergency Call Routing Policy.
```
$members | ForEach-Object { Grant-CsTeamsChannelsPolicy -PolicyName "Operations Emergency Calling Policy" -Identity $_.EmailAddress}
``` 
Depending on the number of members in the group, this command may take several minutes to execute.

## Assign a custom emergency calling policy to a network site

Use the [Set-CsTenantNetworkSite](https://docs.microsoft.com/powershell/module/skype/set-cstenantnetworksite) cmdlet to assign an emergency calling policy to a network site.

The following example shows how to assign a policy called Contoso Emergency Calling Policy 1 to the Site1 site.

    ```
    Set-CsTenantNetworkSite -identity "site1" -EmergencyCallingPolicy "Contoso Emergency Calling Policy 1"
    ```

## Related topics

- [Manage emergency call routing policies in Teams](manage-emergency-call-routing-policies.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
