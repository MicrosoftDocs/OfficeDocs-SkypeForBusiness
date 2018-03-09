---
title: Manage user access to Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
ms.reviewer: ritikag
description: Learn how to enable or disable user-level access on a per-user basis.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---

Manage user access to Microsoft Teams
=====================================
> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

At the user-level, access to Microsoft Teams can be enabled of disabled on a per-user basis by assigning or removing the Microsoft Teams product license.

Currently, there are no policy options for turning Microsoft Teams, or a subset of Microsoft Teams features on or off at an individual user level outside of licensing.



> [!NOTE]
>Microsoft recommends that Microsoft Teams is enabled for all users in a company so that teams can be formed organically for projects and other dynamic initiatives. Even if you are deciding to pilot, it may still be helpful to keep Microsoft Teams enabled for all users, but only target communications to the pilot group of users.

Microsoft Teams user-level licenses are managed directly through the Office 365 admin center user management interfaces. An administrator can assign licenses to new users when new user accounts are created, or to users with existing accounts. The administrator must have Office 365 Global Administrator or User Management Administrator privileges to manage Microsoft Teams licenses.

When a license SKU like E3 or E5 is assigned to a user, a Microsoft Teams license is automatically assigned, and the user is enabled for Microsoft Teams. Administrators can have a granular control over all the Office 365 services and licenses, and the Microsoft Teams license for a specific user or a group of users can be enabled or disabled.

![Screenshot of Product licenses section in Office 365 admin center.](media/Manage_user_access_to_Microsoft_Teams_image2.png) 

A Microsoft Teams user license can be disabled at any time. Once the license is disabled, the users access to Microsoft Teams will be prevented and the user will no longer be able to see Microsoft Teams in the Office 365 app launcher and homepage.

![Screenshot of Product licenses section in Office 365 admin center, showing Microsoft Teams selected.](media/Manage_user_access_to_Microsoft_Teams_image4.png)

In addition to using the Office 365 admin center, Office 365 admins can also use Office 365 PowerShell to assign and remove licenses. To assign a license to a user, use the following syntax:

```
Set-MsolUserLicense -UserPrincipalName "\<Account\>" -AddLicenses "\<AccountSkuId\>"
```

The following example assigns a license from the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan to the unlicensed user belindan@litwareinc.com.

```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

For more details and examples, see [Assign licenses to user accounts with Office 365 PowerShell](https://go.microsoft.com/fwlink/?linkid=855755).

To remove licenses from an existing user account, use the following syntax:

```
Set-MsolUserLicense -UserPrincipalName \<Account\> -RemoveLicenses "\<AccountSkuId1\>", "\<AccountSkuId2\>"
```

The following example removes the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.

```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

For more details and examples, see [Remove licenses from user accounts with office 365 PowerShell](https://go.microsoft.com/fwlink/?linkid=855756).

| | | |
|---------|---------|---------|
|![Decision Point icon.](media/Manage_user_access_to_Microsoft_Teams_image5.png)     |Decision Point         |<ul><li>What is your organization’s plan for Microsoft Teams onboarding across the organization?  (Pilot or Open)</li></ul>         |
|![Next Steps icon.](media/Manage_user_access_to_Microsoft_Teams_image6.png)     |Next Steps         |<ul><li>If onboarding via a closed Pilot, decide if you would like to do so via licensing, or targetted communication.</li><li>Depending on decision, take steps to make sure only Pilot users who are allowed to access Microsoft Teams (if needed).</li><li>Document the guidelines for which users who will (or will not) have access to Microsoft Teams.</li></ul>         |
