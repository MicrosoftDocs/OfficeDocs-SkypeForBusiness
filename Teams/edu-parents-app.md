---
title: Admin setup of Parents in Teams for Education
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: 
description: Microsoft Teams article documenting prerequisites and setup of Parents in Teams for Education.
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

# Set up Parent Connection in Microsoft Teams for Education

The Parent Connection in Teams for Education helps educators securely connect and engage with the parents and guardians of the students in their class teams using Teams chat, which will scale across the educator's organization. All parent and guardian data is provisioned using School Data Sync, allowing IT staff to smoothly set things up.

Once parents and guardians are set up, they can chat with their student's educators using Teams chat. For guidance on getting parents and guardians connected to educators, see [Connect with educators in Teams](https://support.microsoft.com/topic/connect-with-educators-in-teams-ec2430c3-952a-4ba4-9891-1d1cab577960).

Parents also works with Supervised Chat. Parents and guardians won’t have full Teams permissions, which means they can’t start conversations with students or remove full-permissions users (like educators) from chats. For more information about Supervised Chat, see [Use supervised chats in Microsoft Teams](supervise-chats-edu.md).

## Requirements

### School Data Sync

- You need School Data Sync (SDS) to populate each student's parent and guardian **related contact** information​.
  - [Deploy SDS](/schooldatasync/parents-and-guardians-in-sds)

- If you need assistance in setting up SDS and populating parent and guardian **related contacts** for the students in your tenant, contact the EDU Customer Success team by:
  - Completing the RFA process at [FastTrack](https://www.microsoft.com/fasttrack?rtc=1).
  - Opening a ticket at [Support](https://aka.ms/sdssupport).

- Currently, SDS only supports CSV-based data ingestion for Parent Contacts; however, you can use [PowerSchool API Sync](/schooldatasync/how-to-deploy-school-data-sync-by-using-powerschool-sync) or [OneRoster API Sync](/schooldatasync/how-to-deploy-school-data-sync-by-using-oneroster-sync) for all roster data, and just add Parent Contacts using CSV.
  - Create a second sync profile using the [SDS v1 CSV Sync format](/schooldatasync/school-data-sync-format-csv-files-for-sds).
  - Pull the two populated [Parent files](/schooldatasync/parent-contact-sync-file-format) with the rest of the v1 files empty (just the headers).
    - User.csv
    - Guardianrelationship.csv
  - To view a sample set of the v1 CSV files, see the [Minimum Required Attributes GitHub files](https://github.com/OfficeDev/O365-EDU-Tools/tree/master/CSV%20Samples/SDS%20Format/Min%20Required%20Attributes).
  - If you want to automate pulling in the CSV files after the initial sync, read our [CSV File Sync Automation document](/schooldatasync/csv-file-sync-automation).
  - For help with setting up your SDS data sync, reach out to [our customer success team](https://www.microsoft.com/fasttrack?rtc=1) or [open a support ticket](https://edusupport.microsoft.com/support?product_id=data_sync).

### Teams Admin Center - Policies

- Class team owners must have Teams chat turned on.
- Class team owners must have external access with **Teams accounts not managed by an organization** turned on.
  - This must be turned on at the tenant level and the user level. The tenant level setting can be found in **Users > External Access** in the Teams Admin Center. This setting can also be accessed via PowerShell. User level external access policies can only be accessed via PowerShell. See the PowerShell commands below for further guidance.

> [!NOTE]
>Parents and guardians are classified as External users in the Parents feature, meaning they don’t have full tenant rights. They only have access to the chat or chats they are added to as well as files, images, and other content shared in the chat.
>
>Also, External users can see the presence (offline, available, busy, etc.) of your organization’s users, but this can be turned off using PowerShell to protect users’ privacy. In PowerShell, use [Set-CsPrivacyConfiguration](/powershell/module/skype/set-csprivacyconfiguration?view=skype-ps) and set ``EnablePrivacyMode=true``.
>
>Even though parents and guardians are External users, their contributions to chats are discoverable. Learn how to conduct a Teams eDiscovery investigation by reading [Conduct an eDiscovery investigation of content in Microsoft Teams](ediscovery-investigation.md).

## Allow external access with Teams accounts not managed by an organization

To allow educators to communicate with parents and guardians in Teams, the education tenant's IT admin needs to update the tenant's policies to allow external access for Teams accounts outside of the tenant. For more information on managing external access, view [Manage external access in Microsoft Teams](manage-external-access.md).

Here are the steps to turn on external access for parents and guardians.

1. Install the latest Microsoft Teams PowerShell module preview.

    ```powershell
    Install-Module -Name PowerShellGet -Force -AllowClobber
    Install-Module -Name MicrosoftTeams -AllowPrerelease -Force –AllowClobber
    ```

2. Using credentials that have admin privileges, run the following commands:

    ```powershell
    $credential = Get-Credential
    Connect-MicrosoftTeams -Credential $credential
    ```

    The policy setting that turns on external access with Teams accounts not managed by an organization at the user level (`EnableTeamsConsumerAccess`) is turned on by default for all user-level external access policies. Both the tenant-level setting and the user-level policy setting need to be turned on for a user to have external access with Teams accounts not managed by an organization. If you don't want every user in your tenant to have this access turned on, you should ensure that your tenant-level setting is turned off, update the user-level external access policies assigned to your users, and then turn on the tenant-level setting.

    To check which user-level external access policies exist and who they're assigned to, you can use the following steps:

3. Check that user-level external access policies exist.

    ```powershell
    Get-CsExternalAccessPolicy
    ```

4. For each policy other than the ‘Global’ policy, check which users have the policy assigned.

   > [!NOTE]
   > Any users who do not have a specific policy assigned will fall back to the ‘Global’ policy. Any new users who are added to the tenant will have the ‘Global’ policy assigned.

    ```powershell
    Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "<PolicyName>"} | Select-Object DisplayName,ObjectId,UserPrincipalName
    ```

Since all user-level external access policies have `EnableTeamsConsumerAccess` set to true by default, if you would like to adjust the `EnableTeamsConsumerAccess` setting for specific users, you can create/modify existing external access policies with adjusted settings and/or reassign users to new or existing policies using the following PowerShell cmdlets:

- Create a new external access policy: [New-CsExternalAccessPolicy](/powershell/module/skype/new-csexternalaccesspolicy)

- Customize an existing external access policy (including the ‘Global’ policy): [Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)

> [!NOTE]
> The following subscription default policies cannot be modified: ‘FederationAndPICDefault’, ‘FederationOnly’, ‘NoFederationAndPIC’. The ‘FederationAndPICDefault’ policy used to be assigned to all users by default, however new users are now assigned the ‘Global’ policy by default. If you need to change the policy settings for users who have these subscription default policies assigned, assign different policies with the correct settings to these users.​

- Assign an external access policy to a single user: [Grant-CsExternalAccessPolicy](/powershell/module/skype/grant-csexternalaccesspolicy)

- Assign a policy to a set of users: [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation)

Once the user-level external access policies are set correctly for the users in your tenant, you can turn on the tenant-level setting (`AllowTeamsConsumer`) for the tenant using the following cmdlet:

- Set the federation configuration settings for your tenant: [Set-CsTenantFederationConfiguration](/powershell/module/skype/set-cstenantfederationconfiguration)

## Turn on the Parents app in the Teams admin center

The Parents app is turned off by default, so class team owners won't see it in their class teams until it's allowed through the Teams admin center. The Parents app is turned on in the Teams admin center using [Allow apps blocked by publishers](manage-apps.md#apps-blocked-by-publishers).

At any time, the app can be turned off at the tenant level using [Allow and block apps](manage-apps.md#allow-and-block-apps) in the Teams admin center. If it's turned off at the tenant level, it will be blocked for all users, even if user-level permissions are turned on.

The Parents app can also be turned off at the user level using [Manage app permission policies in Microsoft Teams](teams-app-permission-policies.md).

## More information

- [CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)
- [CsTenantFederationConfiguration](/powershell/module/skype/set-cstenantfederationconfiguration)
