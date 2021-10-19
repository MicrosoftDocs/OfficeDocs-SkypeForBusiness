---
title: Admin set-up for the EDU Microsoft Parents app
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: 
description: Microsoft Teams for EDU article document prerequisites and PowerShell set-up for the Parents app.
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

# Deploying the parents app in Microsoft Teams

[!INCLUDE [preview-feature](includes/preview-feature.md)]

Enabling the parents app in Microsoft Teams is a straightforward process for admins, delivering a secure method for educators to communicate to students and their contacts that remain in-tenant, and which will scale across your educator organization.

## Requirements

### School Data Sync

- You need School Data Sync (SDS) to populate each student's **related contact** information​.
  - [Deploy SDS](/schooldatasync/how-to-deploy-sds-using-sds-v2.1-csv-files)

- If you need assistance in setting up SDS and enabling Parent Contacts in your tenant, contact the EDU Customer Success team by:
  - Completing the RFA process at [FastTrack](https://www.microsoft.com/fasttrack?rtc=1).
  - Opening a ticket at [Support](https://aka.ms/sdssupport).

### Teams Admins Center - Policies​

- Class Owner must have Chat enabled​
- Class Owner must have External Access with **Teams accounts not managed by an organization** enabled. ​
  - This setting can be found in Org-wide settings > External Access for the tenant level, or if you’d like to enable for a certain set of users, see the PowerShell below.​

## Enabling federated chat on a per-user basis

1. Install the latest Microsoft Teams PowerShell module preview.

    ```powershell
    Install-Module -Name PowerShellGet -Force -AllowClobber​
    Install-Module -Name MicrosoftTeams -AllowPrerelease -Force –AllowClobber​
    ```
    
2. Using credentials that have admin privileges, run the following command in a command window:

    ```powershell
    $credential = Get-Credential
    Connect-MicrosoftTeams -Credential $credential
    ```

By default, the tenant-level setting which controls Teams consumer external access for the tenant (AllowTeamsConsumer) is disabled. However, the policy setting which enables Teams consumer external access at the user level (EnableTeamsConsumerAccess) is enabled by default for all user-level external access policies. Both the tenant-level setting and the user-level policy setting need to be enabled for a user to have Teams consumer external access. If you don't want everyone in your tenant to have Teams consumer external access enabled, you should update the user-level external access policies assigned to your users prior to enabling the tenant-level setting.

If you need to check which user-level external access policies exist and who they are assigned to, you can use the following steps:
    
3. Check which user-level external access policies exist​.

    ```powershell
    Get-CsExternalAccessPolicy -Include All​
    ```

4. For each policy other than the ‘Global’ policy, check which users have the policy assigned. Note: any users who do not have a specific policy assigned will fall back to the ‘Global’ policy​

    ```powershell
    Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq “<PolicyName>"} | Select-Object DisplayName,ObjectId,UserPrincipalName
    ```

### Further PowerShell options

Since all user-level external access policies have EnableTeamsConsumerAccess set to true by default, if you would like to update any of these policies to adjust the EnableTeamsConsumerAccess setting, you can create new external access policies with adjusted settings, or reassign users to new or existing policies, through the following PowerShell:

- Create a new external access policy (this creates a new external access policy and define the settings​):

    ```powershell
    New-CsExternalAccessPolicy (SkypeForBusiness) | Microsoft Docs
    ```

- Customize an existing external access policy (Modifies the settings of an existing external access policy, including the Global policy)):

    ```powershell
    Set-CsExternalAccessPolicy (SkypeForBusiness) | Microsoft Docs
    ```

> [!NOTE]
> The following subscription defaults cannot be modified: “FederationAndPICDefault”, “FederationOnly”, “NoFederationAndPIC”. If you need to change the policy settings for users who have these policies assigned, assign different policies with the correct settings to these users.​

- Assign an external access policy to a single user:

    ```powershell
    Grant-CsExternalAccessPolicy (SkypeForBusiness) | Microsoft Docs​
    ```

- Assign a policy to a set of users:

    ```powershell
    New-CsBatchPolicyAssignmentOperation (MicrosoftTeamsPowerShell) | Microsoft Docs​
    ```

Once you feel confident that your user-level external access policies are set correctly for all your users, you can enable the tenant-level setting which controls Teams consumer external access for the tenant using the following cmdlet:​

- Set the federation configuration settings for your tenant (Setting AllowTeamsConsumer to true):

    ```powershell
    Set-CsTenantFederationConfiguration (SkypeForBusiness) | Microsoft Docs​
    ```

### Disabling the Parents App

The Parents App is enabled by default, so all Class owners will see the app in their class team. The app can be disabled at the tenant level using [Allow and block apps](manage-apps.md#allow-and-block-apps) in the Microsoft Teams admin center. If this is disabled at tenant level, it'll be blocked for all users, even if user level permission is enabled.​

This can also be disabled at the user level using [Manage app permission policies in Microsoft Teams].(teams-app-permission-policies.md).

## More information

- [CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)
- [Assigning your policy to a user](/powershell/module/skype/grant-csexternalaccesspolicy)
