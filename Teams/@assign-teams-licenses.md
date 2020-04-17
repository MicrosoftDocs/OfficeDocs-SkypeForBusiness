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

By default, when a licensing plan is assigned to a user, a Teams license is automatically assigned, and the user is enabled for Teams. You can remove or re-assign a Teams license to a user at any time.

You can manage Teams licenses in the Microsoft 365 admin center or by using PowerShell. You must be a Global admin or User management admin to manage licenses.

> [!NOTE]
> We recommend that you enable Teams for all users so that teams can be formed organically for projects and other dynamic initiatives. Even if you're running a pilot, it may still be helpful to keep Teams enabled for all users, but only target communications to the pilot group of users.

## Using the Microsoft 365 admin center

You manage Teams licenses on the **Active users** page of the Microsoft 365 admin center. Use this method to manage Teams licenses for individual users or small groups of users at a time. If you need to manage Teams licenses for a large number of users, such as hundreds or thousands of users, use Powershell.

- To enable Teams for one or more users, select the **Microsoft Teams** check box or switch the toggle to **On**.
- To disable Teams for one or more users, clear the **Microsoft Teams** check box or switch the toggle to **Off**. When the Teams license is disabled, the user will no longer see Teams in the app launcher or homepage.

For detailed steps, see [Assign licenses to users](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).

### Using PowerShell

You enable and disable Teams through PowerShell as you would for any other service plan. Here are the service plan names for Teams:

- Microsoft Teams: TEAMS1
- Microsoft Teams for GCC: TEAMS_GOV
- Microsoft Teams for DoD: TEAMS_DOD

#### Example

> [!IMPORTANT]
> The [New-MsolLicenseOptions](https://docs.microsoft.com/powershell/module/msonline/new-msollicenseoptions) cmdlet will enable all services that were previously disabled unless explicitly identified in your custom script. For example, if you want to leave both Exchange and Sway disabled while additionally disabling Teams, you'll need to include this in the script or both Exchange and Sway will be enabled for those users you identified. To use a GUI to manage this functionality, see [Office 365 License Reporting and Management Tool -Assign Remove Licenses in Bulk](https://gallery.technet.microsoft.com/Office365-License-cfd9489c) for more information.

The following is an example of how to disable Teams for users who have a particular license type. For example, follow these steps to first disable Teams for all users who have a particular licensing plan, and then enable Teams for each individual user who should have access to Teams.

Run the following command to display the licensing plans you have within your organization.

      Get-MsolAccountSku

Run the following commands, where \<organization:plan> is your organization name and the licensing plan for your organization that you identified in the earlier step. For example, ContosoSchool:ENTERPRISEPACK_STUDENT.

      $acctSKU="<organization:plan>
      $x = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans "TEAMS1"
      
Run the following command to disable Teams for all users who have an active license for your licensing plan:

      Get-MsolUser | Where-Object {$_.licenses[0].AccountSku.SkuPartNumber -eq  ($acctSKU).Substring($acctSKU.IndexOf(":")+1,  $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} |  Set-MsolUserLicense -LicenseOptions $x

For more information, see:

- [Disable access to services with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-with-office-365-powershell).
- [Disable access to services while assigning user licenses](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-while-assigning-user-licenses).

## Manage teams at the organization level

[!INCLUDE [global-switch-expiry-note](includes/global-switch-expiry-note.md)]
