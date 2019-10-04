---
title: Manage emergency call routing policies in Microsoft Teams
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
description: Learn how to use and manage emergency call routing policies for the Dynamic E911 feature in Microsoft Teams. 
f1keywords: ms.teamsadmincenter.voice.emergencycallroutingpolicies.overview
---

# Manage emergency call routing policies in Microsoft Teams

If you've deployed Phone System Direct Routing in your organization, you can use emergency call routing policies in Microsoft Teams to set up emergency numbers and specify how emergency calls are routed. An emergency call routing policy determines whether enhanced emergency services is enabled for users who are assigned the policy, the numbers used to call emergency services (for example, 911 in the United States), and how calls to emergency services are routed.

You manage emergency call routing policies by going to **Voice** > **Emergency policies** in the Microsoft Teams admin center or by using Windows PowerShell. The policies can be assigned to users and [network sites](location-based-routing-terminology.md).

For users, you can use the global (Org-wide default) policy or create and assign custom policies. Users will automatically get the global policy unless you create and assign a custom policy. Keep in mind that you can edit the settings in the global policy but you can't rename or delete it. For network sites, you create and assign custom policies.

If you assigned an emergency call routing policy to a network site and to a user and if that  user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.

## Create a custom emergency call routing policy

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Call routing policies** tab.
2. Click **Add**.
3. Enter a name and description for the policy.
4. To enable enhanced emergency services, turn on **Enhanced emergency services**. When enhanced emergency services is enabled, Teams retrieves policy and location information from the service and includes that information as part of the emergency call.
5. Define one of more emergency numbers. To do this, under **Emergency numbers**, do the following:
    1. **Emergency dial string**: Enter the emergency dial string. This dial string indicates that a call is an emergency call.
    2. **Emergency dial mask**: For each emergency number, you can specify zero or more emergency dial masks. A dial mask is the number that you want to translate into the value of the emergency dial string. This allows for alternate emergency numbers to be dialed and still have the call reach emergency services. <br>For example, you add 112 as the emergency dial mask, which is the emergency service number for most of Europe, and 911 as the emergency dial string. A Teams user from Europe who is visiting may not know that 911 is the emergency number in the United States, and when they dial 112, the call is made to 911. To define multiple dial masks, separate each value by a semicolon. For example, 112;212.
    3. **PSTN Usage**: Select the public switched telephone network (PSTN) usage. The PSTN usage is used to determine which route is used to route emergency calls from users who are authorized to use them. The route associated with this usage should point to an SIP trunk dedicated to emergency calls or to an Emergency Location Identification Number (ELIN) gateway that routes emergency calls to the nearest Public Safety Answering Point (PSAP).

    > [!NOTE]
    > Dial strings and dial masks must be unique within a policy. This means that for a policy, you can define multiple emergency numbers and you can set multiple dial masks for a dial string, but each dial string and dial mask must only be used one time.

6. Click **Save**.

### Using PowerShell

See [New-CsTeamsEmergencyCallRoutingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsemergencycallroutingpolicy).

## Edit an emergency call routing policy

### Using the Microsoft Teams admin center

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Call routing policies** tab.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Make the changes that you want, and then click **Save**.

### Using PowerShell

See [Set-CsTeamsEmergencyCallRoutingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsemergencycallroutingpolicy).

## Assign a custom emergency call routing policy to users

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. Click **Policies**, and then next to **Assigned policies**, click **Edit**.
3. Under **Emergency call routing policy**, select the policy you want to assign, and then click **Save**.

To assign a custom teams policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Call routing policies** tab.
2. Select the policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, click **Save**.

### Using PowerShell

#### Assign a custom emergency call routing policy to a user

See [Grant-CsTeamsEmergencyCallRoutingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsemergencycallroutingpolicy).

### Assign a custom emergency call routing policy to users in a group

You may want to assign a custom emergency call routing policy to multiple users that you’ve already identified. For example, you may want to assign a policy to all users in a security or distribution group. You can do this by connecting to the Azure Active Directory PowerShell for Graph module and the Skype for Business PowerShell module.

In this example, we assign a policy called HR Emergency Call Routing Policy to all users in the Contoso HR group.  

> [!NOTE]
> Make sure you first connect to the Azure Active Directory PowerShell for Graph module and Skype for Business PowerShell module by following the steps in [Connect to all Office 365 services in a single Windows PowerShell window](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-all-office-365-services-in-a-single-windows-powershell-window).

Get the GroupObjectId of the particular group.
```
$group = Get-AzureADGroup -SearchString "Contoso HR"
```
Get the members of the specified group.
```
$members = Get-AzureADGroupMember -ObjectId $group.ObjectId -All $true | Where-Object {$_.ObjectType -eq "User"}
```
Assign all users in the group to a particular teams policy. In this example, it's HR Emergency Call Routing Policy.
```
$members | ForEach-Object { Grant-CsTeamsChannelsPolicy -PolicyName "HR Emergency Call Routing Policy" -Identity $_.EmailAddress}
``` 
Depending on the number of members in the group, this command may take several minutes to execute.

## Assign a custom emergency call routing policy to a network site

Use the [Set-CsTenantNetworkSite](https://docs.microsoft.com/powershell/module/skype/set-cstenantnetworksite) cmdlet to assign an emergency calling routing policy to a network site.

This example shows how to assign a policy called Emergency Call Routing Policy 1 to the Site1 site.

```
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallRoutingPolicy "Emergency Call Routing Policy 1"
```

## Related topics

- [Manage emergency calling policies in Teams](manage-emergency-calling-policies.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
