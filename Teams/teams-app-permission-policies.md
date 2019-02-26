---
title: Manage app permission policies in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 3/01/2019
ms.reviewer: larryjin
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.audience: Admin
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn about app permission policies in Microsoft Teams and how to use them to control what apps are available for users in your organization. 
ROBOTS: NOINDEX, NOFOLLOW
---

# Manage app permission policies in Microsoft Teams

> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

As an admin, you can use app permission policies to control what apps are available to Microsoft Teams users in your organization. You can allow or block all apps or specific apps published by Microsoft, third-parties, and your organization. When you block an app, users are unable to install it from the Teams App store. 

You manage app permission policies in the Microsoft Teams admin center. You can use the global policy (Org-wide default) or create custom policies and assign them to users. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

You can edit the settings in the global policy to block or allow the apps that you want. If you want to control the apps that are available for different groups of users in your organization, create and assign one or more custom policies.

![app-setup-policies.png](media/app-setup-policies.png)

> [!NOTE]
> If a user is assigned a custom policy, that policy applies to the user. If a user isn't assigned a custom policy, the global policy applies to the user.

## Manage org-wide app settings

Org-wide app settings

## Create a custom app permission policy

You can use the Microsoft Teams admin center or Windows PowerShell to create a custom policy.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams app** > **App permission policies**.
2. Select **New policy**.
3. Enter a descriptive name for the policy.
4. Specify the apps that you want to make available for users.
    a. Under **Microsoft apps**, **Third-party apps**, and **Tenant apps**, choose one of the following:
- **Allow all apps**
- **Allow specific apps and block all others**
- **Block specific apps and allow all others**
- **Block all apps**

## Edit an app permission policy

You can use the Microsoft Teams admin center or Windows PowerShell to edit a policy, including the global (Org-wide default) policy and custom policies that you create. 

1. In the left navigation of the Microsoft Teams admin center, go to **Teams app** > **App permission policies**.
2. Select the policy you want to edit. 
3. From here, make the changes that you want. 
4. Click **Save**. 

## Assign a custom app permission policy to users

You can use the Microsoft Teams admin center to assign a custom policy to individual users or Windows PowerShell to assign a custom policy to groups of users, such as a security group or distribution group.

### Assign a custom app setup policy to individual users

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click       the user.
2. Next to **Assigned policies**, choose **Edit**.
3. Under **Teams App Setup policy**, select the app setup policy you want to assign, and then choose **Save**.

    ![app-setup-policies-assign-policy.png](media/app-setup-policies-assign-policy.png)

### Assign a custom app permission policy to users in a group

You may want to assign a custom app setup policy to multiple users that you’ve already identified. For example, you may want to assign a policy to all users in a security group. You can do this by connecting to the Azure Active Directory PowerShell for Graph module and the Skype for Business PowerShell module. For more information about using PowerShell to manage Teams, see [Teams PowerShell Overview](teams-powershell-overview.md).

In this example, we assign a custom app setup policy called HR App Setup Policy to all users in the Contoso Pharmaceuticals HR Project group.  

> [!NOTE]
> Make sure you first connect to the Azure Active Directory PowerShell for Graph module and Skype for Business PowerShell module by following the steps in [Connect to all Office 365 services in a single Windows PowerShell window](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-all-office-365-services-in-a-single-windows-powershell-window).

Get the GroupObjectId of the particular group.
```
$group = Get-AzureADGroup -SearchString "Contoso Pharmaceuticals HR Project"
```
Get the members of the specified group.
```
$members = Get-AzureADGroupMember -ObjectId $group.ObjectId -All $true | Where-Object {$_.ObjectType -eq "User"}
```
Assign all users in the group to a particular app setup policy. In this example, it's HR App Setup Policy.
```
$members | ForEach-Object { Grant-CsTeamsAppSetupPolicy -PolicyName "HR App Setup Policy" -Identity $_.EmailAddress}
``` 
Depending on the number of members in the group, this command may take several minutes to execute.

## FAQ

### Working with app permission policies

#### What built-in app setup policies are included in the Microsoft Teams admin center?

- **Global (Org-wide default)**: This default policy applies to all users in your organization unless you assign another policy. Edit the global policy to pin apps that are most important for your users.
- **FirstLineWorker**: This policy is for firstline workers. You can assign it to firstline workers in your organization. It's important to know that like custom policies that you create, you have to assign the policy to users for the settings to be active. For more information, go to the [Assign a custom app setup policy to users](#assign-a-custom-app-setup-policy-to-users) section of this article.

#### Why can't I find an app in the Add pinned apps pane?

Not all apps can be pinned to Teams through an app setup policy. Some apps may not support this functionality. To find apps that can be pinned, search for the app in the **Add pinned apps** pane. Tabs that have a personal scope (static tabs) and bots can be pinned to the Teams desktop client and these apps are available in the **Add pinned apps** pane.

Keep in mind that the Teams app store lists all Teams apps whereas the **Add pinned apps** pane includes only apps that can be pinned to Teams through a policy. 

#### I'm a Teams for Education admin. What do I need to know about app setup policies in Teams for Education?

The Calling app isn't available in Teams for Education. When you create a new custom app setup policy, the Calling app is displayed in the list of apps. However, the app isn't pinned to Teams clients and Teams for Education users won't see the Calls app in Teams. 

#### How many apps can be added to a policy?

A minimum of two apps must be pinned to the Teams mobile clients (iOS and Android). If a policy has less than two apps, the mobile clients won't reflect the policy settings and instead will continue to use the existing configuration.

#### How long does it take for policy changes to take effect?

After you edit the global policy or assign a policy, it can take up to 24 hours for changes to take effect.

### User experience

#### How can users see all their pinned apps in Teams?

To view all apps that are pinned for a user, users may have to do the following depending on the number of installed apps and the size of their Teams client window.

|Teams desktop client |Teams mobile client |
|---------|---------|
|In the app bar on the side of Teams, click **... More apps**.| In the app bar near the bottom of Teams, swipe up.|
|![app-setup-policies-desktop-more-apps.png](media/app-setup-policies-desktop-more-apps.png)<br>   |![app-setup-policies-mobile-more-apps.png](media/app-setup-policies-mobile-more-apps.png)  

#### What do I need to know about the Teams mobile experience?

The Teams mobile clients (iOS and Android) currently don't support personal apps with static tabs. Depending on the apps set in the policy, apps pinned to the Teams desktop client might not appear in the Teams mobile clients. Personal bots will still appear in Chat on mobile clients.

With the Teams mobile clients, users will see core Teams apps such as Activity, Chat, and Teams, and you can pin some first-party apps from Microsoft, such as Shifts.

#### Can users change the order of apps pinned through a policy?

Currently, users can change the order of their pinned apps on Teams mobile clients but not on the Teams desktop or web clients. 

### Custom Teams apps

#### My organization built a custom Teams app and published it through AppSource but the app icon isn't displayed as expected when the app is pinned to the app bar in Teams. How do I fix it? 

Make sure that you follow the logo guidelines before you submit the app. To learn more, see [Checklist for Seller Dashboard submission](https://docs.microsoft.com/microsoftteams/platform/publishing/office-store-checklist). 

 ## Related topics
- 
