---
title:  Upgrade to the new Teams client using policies
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 12/14/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about how to upgrade the new Microsoft Teams client.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Upgrade to the new Teams using policies

You can upgrade to the new Teams client to your organization by setting policies in either the Teams Admin Center or by using PowerShell.

> [!TIP]
> As a companion to this article, see our [Teams setup guide](https://go.microsoft.com/fwlink/?linkid=2270204"https://go.microsoft.com/fwlink/?linkid=2270204") to review best practices and learn to configure Teams features to meet your business needs. This comprehensive guide covers key areas like managing policies, external access, and tags. For a customized experience based on your environment, you can access the [Teams automated setup guide](https://go.microsoft.com/fwlink/?linkid=2270034"https://go.microsoft.com/fwlink/?linkid=2270034") in the Microsoft 365 admin center. 
## Prerequisites

|Requirement|Version|
|:----------|:------|
|Windows| Windows 10 version 10.0.19041 or higher (excluding Windows 10 LTSC for Teams desktop app). Users of Windows N SKU need to enable [Media Feature Pack for Windows 10/11 N](https://support.microsoft.com/windows/media-feature-pack-for-windows-10-11-n-september-2022-78cfeea5-c7d9-4aa8-b38f-ee4df1392009#:~:text=Here%E2%80%99s%20how%20to%20install%20the%20Media%20Feature%20Pack%3A,select%20Settings%20%3E%20Apps%20%3E%20Optional%20features.%20)|
|Webview2|Update to the most current version. Learn more: [Enterprise management of WebView2 Runtimes](/microsoft-edge/webview2/concepts/enterprise)|
|Teams app|Version 1.6.00.4472 to see the *Try the new Teams* toggle.</br></br>If you are at a lower version, select the overflow menu **(…) > Check for updates > Update**. Then restart your app.|
|Office |Microsoft 365 Apps or Office LTSC 2021 Learn more: [Office versions and connectivity to Microsoft 365 services](/deployoffice/endofsupport/microsoft-365-services-connectivity)|
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|
|Delivery optimization (DO)|DO powers Teams automatic updates, which are required as part of the [Servicing Agreement](/microsoftteams/new-teams-automatic-upgrade-announced#servicing-agreement).</br></br>Overview: [What is Delivery Optimization?](/windows/deployment/do/waas-delivery-optimization)</br>Recommended settings: [Set up Delivery Optimization](/windows/deployment/do/waas-delivery-optimization-setup#recommended-delivery-optimization-settings)<br></br>**Note:** Download Mode 100 (Bypass) isn't supported.|

### Required Microsoft 365 Apps Security Updates

|Channel|Version & Build|
|:-----|:-----|
|Semi-Annual Enterprise Channel| Version 2302 (Build 16130.20306)</br>Version 2208 (Build 15601.20578)|
|Monthly Enterprise Channel|Version 2301 (Build 16026.20222)</br>Version 2212 (Build 15928.20294)</br> |
|Office LTSB|Version 2018 (Build 10396.20023)</br>Version 2021 (Build 14332.20481)</br>|

</br>

Learn more at [**Update History for Microsoft 365 Apps**](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions).

> [!NOTE]
> The end of availability for classic Teams client is June 30 2024. For more information see [End of availability for classic Teams client](teams-classic-client-end-of-availability.md).

## Set the policies to upgrade to the new Teams client

As an admin, you can manage how new Teams to your users.

To control which users can see the toggle, use the Teams admin setting **UseNewTeamsClient** under the **TeamsUpdateManagement** policy.

Manage this setting in the **Teams Admin Center** or using **Teams PowerShell**.</br>

## [**Teams Admin Center**](#tab/teams-admin-center)

Configure setting via Teams Admin Center.

### Policy settings for upgrade

   |Setting|Description|
   |:-----|:-----|
   |Not enabled|Use this value to hide the new Teams toggle switch. Users won't be able to opt in to the new Teams.|
   |Classic Teams as default|Use this value to have classic Teams the default version. The new Teams toggle switch displays to let users opt into the new Teams and switch back if needed. **Note:** This option was previously called *Users can choose*.|
   |Microsoft controlled| Default. The value lets Microsoft control whether the new Teams toggle switch is shown or not based on product readiness|
   |New Teams as default </br>Rollout for the feature began in early August  2023 | Use this value to make new Teams the default version. Users can switch back to classic Teams using the toggle.|
   |New Teams only (Rolling out mid-February 2024) |Use this value to make new Teams the default version and uninstall classic Teams after a fourteen-day period. Users don't have the option to switch back to classic Teams.|

> [!IMPORTANT]
> Admins should know that they can always move forward in the steps to new Teams Only from any other point in the rollout schedule, but they can't move backwards in the steps from where they currently are. Some examples:
>
> - If a customer is currently in classic Teams default mode, they can go to new Teams default mode, or new Teams Only, by assigning those policy states. However, they can't move back to the AdminDisabled state.
> - If a customer is currently in new Teams default mode, they can move forward to new Teams Only by assigning that policy state. In this case, they couldn't move back to classic Teams default or AdminDisabled.

In addition to PowerShell, you can also use Teams Admin Center to manage the visibility of the toggle on a per-user basis.

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select **Teams > Teams Update policies** from the left navigation pane.
3. Select **Add** to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown here.

   :::image type="content" source="media/new-teams-update-options.png" alt-text="update policies add a new policy":::

|Setting|Description|
|:-----|:-----|
|Not enabled|Use this value to hide the new Teams toggle switch. Users won't be able to opt in to the new Teams.|
|Classic Teams as default|Use this value to have classic Teams the default version. The new Teams toggle switch displays to let users opt into the new Teams and switch back if needed. **Note:** This option was previously called *Users can choose*.|
|New Teams as default|Sets the new Teams as default. **Note:** This option is currently being rolled out|
|**Microsoft controlled**|**Default. Use this value to let Microsoft control the following:</br>-Whether the "Try the new Teams" toggle switch is shown or not</br>- In the future, let Microsoft manage the installation of the new Teams client and </br>Allow Microsoft to determine default client behavior based on the [rollout schedule](new-teams-desktop-admin.md).**|

</br>

>[!Note]
>The option "Classic Teams as default" was previously called "Users can choose".

</br>

5.	Select new Teams as default from this setting to ensure users can get the new Teams experience when they launch

6. Once the policy is defined, you can assign it to a **user or user group** with the Group policy assignment. To assign it to a group, select **Group policy assignment** and then **Add**,  or select one of the groups listed.

:::image type="content" source="media/new-teams-update-policies-group.png" alt-text="update policies by group":::

Select a policy to assign to the group.

:::image type="content" source="media/new-teams-update-policies-group-assign.png" alt-text="update policy and assign by group":::

7. Once the policy is defined, you can assign it to a specific user under **Users> Manage users**.

:::image type="content" source="media/new-teams-update-policies-manage-users.png" alt-text="update policy per user":::

   If you update the policy setting in the Teams Admin Center, the new setting can take up to 24 hours to go into effect. The user doesn't have to restart the app.

## [**PowerShell**](#tab/powershell)

Configure the UseNewTeamsClient setting to one of the following possible values:

| Setting | Explanation |
| :----- | :----- |
| MicrosoftChoice | Default setting. This value lets Microsoft control if the Teams (preview) toggle switch is shown based on product readiness. |
|User choice| This value lets the new Teams toggle switch display to all users. Users can choose to opt in or out.|
| AdminDisabled | This value hides the new Teams toggle switch from view. Users won't be able to opt in to the new Teams.| 

Here are the steps needed to configure this setting in PowerShell:

1. Import the latest Teams PowerShell cmdlets (require version 4.9.1 or greater) by following [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams) instructions. Direct link: [PowerShell Gallery Microsoft Teams 4.9.1](https://www.powershellgallery.com/packages/MicrosoftTeams/4.9.1).
2. Connect to an admin account using this command:

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
  > Allow up to 24 hours for the **new policy assignment method** to go into effect. Users don't need to restart the app.

---

### How to uninstall the new Teams client

Any user who was using the new Teams before the policy was implemented can manually opt out by using the new Teams toggle.

After they opt out, the toggle won't appear when they relaunch Teams. To prevent users from using this client and want to uninstall the client, users can manually uninstall it from settings.

</br>

#### Remove new Teams for all users

To remove the new Teams from all users' computers, use the following PowerShell command:

```powershell

Remove-AppxPackage 
```

PowerShell cmdlet to remove new Teams from all users on all computers:

```powershell
Get-AppxPackage *MSTeams* -AllUsers |Remove-AppxPackage -AllUsers
```

PowerShell cmdlet for an individual user without administrator privilege:

```powershell
Get-AppxPackage *MSTeams*|Remove-AppxPackage
```

Command to uninstall teams machine-wide:
teamsbootstrapper.exe -x -m

> [!NOTE]
> If you've set Teams update policy to **Not enabled**, but users still received new Teams client with M365 Apps, please follow instructions in our [How to uninstall the new Teams client](new-teams-deploy-using-policies.md#how-to-uninstall-the-new-teams-client) article to uninstall it for your users.

#### User settings migration

End user settings are automatically migrated from classic Teams to new Teams during the initial switch.  

>[!Note]
>Settings are only migrated once, the first time a user updates to new Teams. After that, no incremental migrations of setting changes will occur if the user switches back and forth between classic and new Teams.

##### Migrated settings

Local settings that are automatically migrated when switching from classic Teams to new Teams:

|Area|Item|
|:----|:-----|
|General| Chat density |
||Show message previews in your chat list |
||App Language |
| |> Display > Turn off animations |
|Devices |Audio devices |
| |> Audio devices > Speaker |
| |> Audio devices > Microphone |
| |Noise suppression |
||High fidelity music mode |
||Secondary ringer |
| |Camera |
||Automatically adjust mic sensitivity |
|Files and Links| Downloads: Location |
||Downloads: Always as where to save downloaded files |
||File open preference: Always open word/ppt/excel files in... |
|Custom Background image files |On-disk image files |
|Call/Meeting Stage|Background Effects, blur |

## Related topics

- [Troubleshooting installation issues in the new Teams client](/microsoftteams/troubleshoot/teams-administration/fix-new-teams-installation-issues)
- [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md)
