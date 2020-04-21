---
title: Manage user access to Microsoft Teams (was user-access)
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
f1.keywords: ms.teamsadmincenter.signin.domainerror.nolicensedusers
ms.reviewer: ritikag
search.appverid: MET150
description: Learn how to manage user access to Teams by assigning or removing a Teams license to users. 
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Manage user access to Teams

You manage access to Teams at the user level by assigning or removing a Microsoft Teams product license. Each user in your organization must be assigned a Teams license before they can use Teams. You can assign licenses to new users when new user accounts are created or to users who have existing accounts.

By default, when a licensing plan is assigned to a user, a Teams license is automatically assigned, and the user is enabled for Teams. You can disable or enable Teams for a user by removing or assigning a license at any time.

You manage Teams licenses in the Microsoft 365 admin center or by using PowerShell. You must be a Global admin or User management admin to manage licenses.

> [!NOTE]
> We recommend that you enable Teams for all users so that teams can be formed organically for projects and other dynamic initiatives. Even if you're running a pilot, it may still be helpful to keep Teams enabled for all users, but only target communications to the pilot group of users.

## Using the Microsoft 365 admin center

Use the Microsoft 365 admin center to manage Teams licenses for individual users or small groups of users at a time. You can manage Teams licenses on the **Licenses** page (for up to 20 users at at time) or **Active users** page. If you need to manage Teams licenses for a large number of users, such as hundreds or thousands of users, use Powershell.

### Assign a Teams license

The steps are different depending on whether you use the **Licenses** page or **Active users** page. For step-by-step instructions, see [Assign licenses to users](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).

### Remove a Teams license

When you remove a Teams license from a user, Teams is disabled for that user, and they will no longer see Teams in the app launcher or homepage. For detailed steps, see [Unassign licenses from users](https://docs.microsoft.com/microsoft-365/admin/manage/remove-licenses-from-users).

## Using PowerShell

You enable and disable Teams through PowerShell in the same way that you would for any other service plan license. You'll need the identifiers for the service plans for Teams, which are as follows:

- Microsoft Teams: TEAMS1
- Microsoft Teams for GCC: TEAMS_GOV
- Microsoft Teams for DoD: TEAMS_DOD

### Assign a Teams license

For detailed steps, see [Assign licenses to user accounts with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell).

### Remove a Teams license

The following is an example of how to use the [New-MsolLicenseOptions](https://docs.microsoft.com/powershell/module/msonline/new-msollicenseoptions) and [Set-MsolUserLicense](https://docs.microsoft.com/en-us/powershell/module/msonline/set-msoluserlicense) cmdlets to disable Teams for users who have a specific licensing plan. For example, follow these steps to first disable Teams for all users who have a particular licensing plan. Then enable Teams for each individual user who should have access to Teams.

> [!IMPORTANT]
> The [New-MsolLicenseOptions](https://docs.microsoft.com/powershell/module/msonline/new-msollicenseoptions) cmdlet will enable all services that were previously disabled unless explicitly identified in your custom script. For example, if you want to leave both Exchange and Sway disabled while also disabling Teams, you'll need to include this in the script or both Exchange and Sway will be enabled for those users you identified.

Run the following command to display all available licensing plans in your organization.

      Get-MsolAccountSku

To learn more, see [View licenses and services with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

Run the following commands, where \<CompanyName:License> is your organization name and the identifier for the licensing plan that you retrieved in the earlier step. For example, ContosoSchool:ENTERPRISEPACK_STUDENT.

      $acctSKU="<CompanyName:License>
      $x = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans "TEAMS1"

Run the following command to disable Teams for all users who have an active license for the licensing plan.

      Get-MsolUser | Where-Object {$_.licenses[0].AccountSku.SkuPartNumber -eq  ($acctSKU).Substring($acctSKU.IndexOf(":")+1,  $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} |  Set-MsolUserLicense -LicenseOptions $x

For more information, see:

- [Disable access to services with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-with-office-365-powershell)
- [Disable access to services while assigning user licenses](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-while-assigning-user-licenses)

## Manage teams at the organization level

[!INCLUDE [global-switch-expiry-note](includes/global-switch-expiry-note.md)]

## Related topics

- [View licenses and services with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)
- [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)
- [Education SKU reference](sku-reference-edu.md)
