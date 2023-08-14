---
title:  Deploy the new Teams client using policies
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 08/10/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about how to deploy the new Microsoft Teams client.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Deploy the new Teams using policies

You can deploy the new Teams client to your organization by setting policies in either the Teams Admin Center or by using PowerShell. 

## Policy settings for deployment

>[!Important]
>The new policy setting is now rolling out that lets you make the new Teams your default version.
>
>By setting the policy to **New Teams as default**, new Teams will become your default. Users can switch back to classic Teams using the toggle.

Options include:

   |Setting|Description|
   |:-----|:-----|
   |Not enabled|Use this value to hide the new Teams toggle switch. Users won't be able to opt in to the new Teams.|
   |Classic Teams as default|Use this value to have classic Teams the default version. The new Teams toggle switch displays to let users opt into the new Teams and switch back if needed. **Note:** This option was previously called *Users can choose*.|
   |Microsoft controlled| Default. The value lets Microsoft control whether the new Teams toggle switch is shown or not based on product readiness|
   |**New Teams as default </br>Rollout for the feature began in early August, 2023 | Use this value to make new Teams as the default version. Users can switch back to classic Teams using the toggle.|


## Prerequisites

|Requirement|Version|
|:-----|:-----|
|Windows| Windows 10 version 10.0.19041 or higher|
|Teams app|Version 1.6.00.4472 to see the *Try the new Teams* toggle.</br></br>If you are at a lower version, select the overflow menu **(…) > Check for updates > Update**. Then restart your app. |
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|


#### Required Microsoft 365 Apps Security Updates

|Channel|Version & Build|
|:-----|:-----|
|Semi-Annual Enterprise Channel| Version 2302 (Build 16130.20306)</br>Version 2208 (Build 15601.20578)</br>Version 2202 (Build 14931.20944)</br> |
|Monthly Enterprise Channel|Version 2301 (Build 16026.20222)</br>Version2212 (Build 15928.20294)</br> |
|Windows LTSB|Version 2018 (Build 10396.20023)</br>Version 2021 (Build 14332.20481)</br>|

</br>

Learn more at [**Update History for Microsoft 365 Apps**](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions).

## Set the policies to deploy the new Teams client

As an admin, you can manage which users in your organizations see or don't see the **Try the new Teams** toggle to use the new Teams.

:::image type="content" source="media/new-teams-toggle.png" alt-text="new teams try me toggle at the top of the screen":::

To control which users can see the toggle, use the Teams admin setting **UseNewTeamsClient** under the **TeamsUpdateManagement** policy. 

Manage this setting in the **Teams Admin Center** or using **Teams PowerShell**.</br>

# [**Teams Admin Center**](#tab/teams-admin-center)

Configure setting via Teams Admin Center

In addition to PowerShell, you can also use Teams Admin Center to manage the visibility of the toggle on a per-user basis.

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select **Teams > Teams Update** policies from the left pane, as shown below.

   :::image type="content" source="media/new-teams-update-policies.png" alt-text="step in how to update teams policies":::

3. Select Add to create a new policy or select an existing policy to open Update policy.

:::image type="content" source="media/new-teams-update-policies-2.png" alt-text="update policies add a new policy":::

4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown below.

   |Setting|Description|
   |:-----|:-----|
   |Not enabled|Use this value to hide the new Teams toggle switch. Users won't be able to opt in to the new Teams.|
   |Classic Teams as default|Use this value to have classic Teams the default version. The new Teams toggle switch displays to let users opt into the new Teams and switch back if needed. **Note:** This option was previously called *Users can choose*.|
   |Microsoft controlled|Default. Based on product readiness, use this value to let Microsoft control the following:</br>-Whether the "Try the new Teams" toggle switch is shown or not</br>- In the future, let Microsoft manage the installation of the new Teams client and </br>Allow Microsof to determine default client behavior based on the [rollout schedule](new-teams-desktop-admin.md#new-teams-rollout-schedule-for-windows-clients).|

</br>

>[!Note]
>The option "Classic Teams as default" was previously called "Users can choose".

</br>

5. Once the policy is defined, you can assign it to a **user or user group** with the Group policy assignment. To assign it to a group, select **Group policy assignment** and then **Add**,  or select one of the groups listed.

:::image type="content" source="media/new-teams-update-policies-group.png" alt-text="update policies by group":::

Select a policy to assign to the group.


:::image type="content" source="media/new-teams-update-policies-group-assign.png" alt-text="update policy and assign by group":::

6. Once the policy is defined, you can assign it to a specific user under **Users> Manage users**.

:::image type="content" source="media/new-teams-update-policies-manage-users.png" alt-text="update policy per user":::

   If you update the policy setting in the Teams Admin Center, the new setting goes into effect within one minute. The user doesn't have to restart the app.

# [**PowerShell**](#tab/powershell)

Configure the UseNewTeamsClient setting to one of the following possible values:

| Setting | Explanation |
| :----- | :----- |
| MicrosoftChoice | Default setting. This value lets Microsoft control if the Teams (preview) toggle switch is shown based on product readiness. |
|User choice| This value lets the new Teams toggle switch display to all users. Users can choose to opt in or out.|
| AdminDisabled | This value hides the new Teams toggle switch from view. Users won't be able to opt in to the new Teams.| 

Here are the steps needed to configure this setting in PowerShell:

1. Import the latest Teams PowerShell cmdlets (require version 4.9.1 or greater) by following [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams) instructions. Direct link: [PowerShell Gallery Microsoft Teams 4.9.1](https://www.powershellgallery.com/packages/MicrosoftTeams/4.9.1).
1. Connect to an admin account using this command:

```powershell
Connect-MicrosoftTeams
```

3. Once connected and logged in via PowerShell, you can explore the list of related commands:
Enter *-CsTeamsUpdateManagementPolicy and tab through the commands (tab key).

4. Use the following commands to change the existing Update Management policy to opt in the assigned users to allow them to try the new Teams:

```powershell
Set-CsTeamsUpdateManagementPolicy -identity <new_policy_name> -UseNewTeamsClient 
```

UserChoice

Example:
```powershell 

Set-CsTeamsUpdateManagementPolicy -identity MySetting -UseNewTeamsClient UserChoice

```

   > [!NOTE]
   > This method for **existing policy modification** doesn't take effect immediately. Allow up to 24 hours for the change to propagate to users. Users don't need to restart the app, but specifically for opt-in, they'll need one restart following a fresh install to see the toggle.

5. Use the following commands to deploy a **new policy** to opt-out a specific user from seeing the toggle:

```powershell

New-CsTeamsUpdateManagementPolicy -identity <new_policy_name> -UseNewTeamsClient AdminDisabled

Grant-CsTeamsUpdateManagementPolicy -identity <user> -PolicyName <new_policy_name>

```

**Example:**

```powershell
New-CsTeamsUpdateManagementPolicy -identity MySetting -UseNewTeamsClient AdminDisabled
Grant-CsTeamsUpdateManagementPolicy -identity admin@contoso.org -PolicyName MySetting
```

  > [!NOTE]
  > This **new policy assignment method** should take effect within one minute. Users don't need to restart the app.

---

### How to uninstall the new Teams client

Any user who was using the new Teams before the policy was implemented can manually opt out by using the new Teams toggle. 

After they opt out, the toggle won't appear when they relaunch Teams. To prevent users from using this client and want to uninstall the client, users can manually uninstall it from settings.

</br>

### Remove new Teams for all users

To remove the new Teams from all users' computers, use the following PowerShell command:

```powershell

Remove-AppxPackage 
```

PowerShell cmdlet to remove new Teams from all users on all computers:

Get-AppxPackage *MSTeams* -AllUsers |Remove-AppxPackage -AllUsers
For an individual user without administrator privilege, use this command:
Get-AppxPackage *MSTeams*|Remove-AppxPackage
