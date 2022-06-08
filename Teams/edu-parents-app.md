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

The Parent Connection in Teams for Education helps educators securely connect and engage with the parents and guardians of the students in their class teams using Teams.

This article provides guidance to education IT professionals on requirements and setup of the Parent Connection.

## Share guardian and educator resources

Here are some resources IT admins can share with guardians and educators on how they can get started using the Parent Connection.

- For guidance on getting guardians set up, see [Connect with educators in Teams](https://support.microsoft.com/topic/connect-with-educators-in-teams-ec2430c3-952a-4ba4-9891-1d1cab577960).
- For guidance on getting educators set up, see [Communicate with guardians in Microsoft Teams](https://support.microsoft.com/topic/communicate-with-guardians-in-microsoft-teams-01471ecd-eb5d-4eda-9c5d-0064d672960e?ui=en-us&rs=en-us&ad=us).

## Benefits of Parent Connection

The Parents Connection allows educators and guardians to chat, email, and call using Teams.

- Teams guardian contact data stays current with SIS using School Data Sync (SDS).
- It works with Supervised chat. For more information, see [Use supervised chats in Microsoft Teams](supervise-chats-edu.md).
  - By default, guardians have restricted permissions, so they can't chat with students or remove users from chats.
  - This setting can be changed by the tenant admin.
- Educators can initiate chats with guardians.
  - If the guardian doesn't have a Teams consumer account, they'll receive the initial message from the educator and an email invite to go to Teams.
- Educators can click a guardian's email to email them using their native email client.
- Educators can click a guardian's phone number to call them within Teams.

> [!IMPORTANT]
> For click to call functionality in Teams, your tenant needs:
>
> - Public Branch Exchange (PBX) capabilities.
> - Connection to the PSTN.
>
> Microsoft 365 A1 and A3 plans don't include PBX capabilities nor PSTN connection. You can purchase [add-on licenses for each of these](/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing).
>
> Microsoft 365 A5 plans only include PBX capabilities using Teams Phone System. You'll still need to [purchase a Teams Calling Plan or use a third-party solution](pstn-connectivity.md) to connect to external numbers on the PSTN.
>
> For more information on all your options to get PSTN connectivity, see [PSTN connectivity options](pstn-connectivity.md).
>
> For more information on Teams calling licensing, see [Teams add-on licensing options](/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing).

## Requirements

You need to use Microsoft Graph or School Data Sync (SDS) to populate each student's parent and guardian related contact information.

### Graph API

If you already use [Microsoft Graph PowerShell SDK](/powershell/microsoftgraph/overview) to create Student identities, you can easily include [relatedContact resource type](/graph/api/resources/relatedcontact).

### School Data Sync

- You need School Data Sync (SDS) to populate each student's parent and guardian **related contact** information.
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

### Teams admin center policies

- Class team owners must have Teams chat turned on.
- Class team owners must have external access with **Teams accounts not managed by an organization** turned on.
  - This must be turned on at the tenant level and the user level. The tenant level setting can be found in **Users > External Access** in the Teams admin center. This setting can also be accessed via PowerShell. User level external access policies can only be accessed via PowerShell. See the PowerShell commands below for further guidance.

#### Parent and guardian restrictions

Parents and guardians are classified as *External users* in the Parents Connection, meaning they don't have full tenant rights. They only have access to the chat or chats they're a part of and the files, images, and other content shared in the chat.

For external chats, both internal and external users can add users to the chat. To learn more about the external chat experience, see [Manage external meetings and chat in Microsoft Teams](manage-external-access.md).

Also, external users can see the presence (offline, available, busy, etc.) of your organization's users, but this can be turned off using PowerShell to protect users' privacy. In PowerShell, use [Set-CsPrivacyConfiguration](/powershell/module/skype/set-csprivacyconfiguration) and set ``EnablePrivacyMode=true``.

Even though parents and guardians are external users, their contributions to chats are discoverable. Learn how to conduct a Teams eDiscovery investigation by reading [Conduct an eDiscovery investigation of content in Microsoft Teams](ediscovery-investigation.md).

> [!IMPORTANT]
> IT admins should educate all Class Owners on best practices for sharing student information over chat, including risks to student privacy.

#### Blocking a parent or guardian in a chat

Educators can block a guardian in chat initiated in the Parent Connection.

The class owner can:

1. Open the guardian's profile card, select the ellipse and **Block User**.
2. Then, remove the guardian from the chat.

The blocked user won't be able to start additional chats with the class owner.

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

4. For each policy other than the 'Global' policy, check which users have the policy assigned.

   > [!NOTE]
   > Any users who do not have a specific policy assigned will fall back to the 'Global' policy. Any new users who are added to the tenant will have the 'Global' policy assigned.

    ```powershell
    Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "<PolicyName>"} | Select-Object DisplayName,ObjectId,UserPrincipalName
    ```

Since all user-level external access policies have `EnableTeamsConsumerAccess` set to true by default, if you would like to adjust the `EnableTeamsConsumerAccess` setting for specific users, you can create/modify existing external access policies with adjusted settings and/or reassign users to new or existing policies using the following PowerShell cmdlets:

- Create a new external access policy: [New-CsExternalAccessPolicy](/powershell/module/skype/new-csexternalaccesspolicy)

- Customize an existing external access policy (including the 'Global' policy): [Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)

> [!NOTE]
> The following subscription default policies cannot be modified: 'FederationAndPICDefault', 'FederationOnly', 'NoFederationAndPIC'. The 'FederationAndPICDefault' policy used to be assigned to all users by default, however new users are now assigned the 'Global' policy by default. If you need to change the policy settings for users who have these subscription default policies assigned, assign different policies with the correct settings to these users.

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
