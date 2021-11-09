---
title: Admin setup for the Microsoft EDU Parents app in Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: 
description: Microsoft Teams for EDU article documenting prerequisites and setup for the Parents app.
ms.localizationpriority: Normal
ROBOTS: NOINDEX, NOFOLLOW
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection:
  - M365-collaboration
appliesto:
  - Microsoft Teams
---

# Deploying the Parents app in Microsoft Teams

The Parents app helps educators securely connect and engage with the parents and guardians of the students in their class teams using Teams chat, which will scale across the educator's organization. All parent and guardian data is provisioned using School Data Sync, allowing IT staff to smoothly set things up.

## Requirements

### School Data Sync

- You need School Data Sync (SDS) to populate each student's parent and guardian **related contact** information​.
  - [Deploy SDS](/schooldatasync/how-to-deploy-sds-using-sds-v2.1-csv-files)

- If you need assistance in setting up SDS and populating parent and guardian **related contacts** for the students in your tenant, contact the EDU Customer Success team by:
  - Completing the RFA process at [FastTrack](https://www.microsoft.com/fasttrack?rtc=1).
  - Opening a ticket at [Support](https://aka.ms/sdssupport).

### Teams Admin Center - Policies​

- Class team owners must have Teams chat enabled.​
- Class team owners must have external access with **Teams accounts not managed by an organization** enabled. ​
  - This must be enabled at the tenant level and the user level. The tenant level setting can be found in **Users > External Access** in the Teams Admin Center. This setting can also be accessed via PowerShell. User level external access policies can only be accessed via PowerShell. See the PowerShell commands below for further guidance.​

## Enabling external access with Teams accounts not managed by an organization

1. Install the latest Microsoft Teams PowerShell module preview.

    ```powershell
    Install-Module -Name PowerShellGet -Force -AllowClobber​
    Install-Module -Name MicrosoftTeams -AllowPrerelease -Force –AllowClobber​
    ```
    
2. Using credentials that have admin privileges, run the following commands:

    ```powershell
    $credential = Get-Credential
    Connect-MicrosoftTeams -Credential $credential
    ```

The policy setting which enables external access with Teams accounts not managed by an organization at the user level (`EnableTeamsConsumerAccess`) is enabled by default for all user-level external access policies. Both the tenant-level setting and the user-level policy setting need to be enabled for a user to have external acces with Teams accounts not managed by an organization enabled. If you do not want every user in your tenant to have this access enabled, you should ensure that your tenant-level setting is disabled, update the user-level external access policies assigned to your users, and then enable the tenant-level setting.

To check which user-level external access policies exist and who they are assigned to, you can use the following steps:
    
3. Check which user-level external access policies exist​.

    ```powershell
    Get-CsExternalAccessPolicy -Include All​
    ```

4. For each policy other than the ‘Global’ policy, check which users have the policy assigned. Note: any users who do not have a specific policy assigned will fall back to the ‘Global’ policy. Any new users who are added to the tenant will have the ‘Global’ policy assigned.​

    ```powershell
    Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "<PolicyName>"} | Select-Object DisplayName,ObjectId,UserPrincipalName
    ```

Since all user-level external access policies have `EnableTeamsConsumerAccess` set to true by default, if you would like to to adjust the `EnableTeamsConsumerAccess` setting for specific users, you can create/modify existing external access policies with adjusted settings and/or reassign users to new or existing policies using the following PowerShell cmdlets:

- Create a new external access policy: [New-CsExternalAccessPolicy](/powershell/module/skype/new-csexternalaccesspolicy)

- Customize an existing external access policy (including the ‘Global’ policy): [Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)

> [!NOTE]
> The following subscription default policies cannot be modified: ‘FederationAndPICDefault’, ‘FederationOnly’, ‘NoFederationAndPIC’. The ‘FederationAndPICDefault’ policy used to be assigned to all users by default, however new users are now assigned the ‘Global’ policy by default. If you need to change the policy settings for users who have these subscription default policies assigned, assign different policies with the correct settings to these users.​

- Assign an external access policy to a single user: [Grant-CsExternalAccessPolicy](/powershell/module/skype/grant-csexternalaccesspolicy)

- Assign a policy to a set of users: [New-CsBatchPolicyAssignmentOperation](/powershell/module/skype/new-csbatchpolicyassignmentoperation)

Once the user-level external access policies are set correctly for the users in your tenant, you can enable the tenant-level setting (`AllowTeamsConsumer`) for the tenant using the following cmdlet:​

- Set the federation configuration settings for your tenant: [Set-CsTenantFederationConfiguration](/powershell/module/skype/set-cstenantfederationconfiguration)

## Disabling the Parents App

The Parents app is enabled by default, so all class team owners will see the app in their class teams. 

The app can be disabled at the tenant level using [Allow and block apps](manage-apps.md#allow-and-block-apps) in the Microsoft Teams admin center. If the app is disabled at tenant level, it will be blocked for all users, even if user level permissions are enabled.​

The app can also be disabled at the user level using [Manage app permission policies in Microsoft Teams](teams-app-permission-policies.md).

## More information

- [CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)
- [CsTenantFederationConfiguration](/powershell/module/skype/set-cstenantfederationconfiguration)
