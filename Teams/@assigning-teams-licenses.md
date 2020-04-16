---
title: Manage user access to Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/12/2018
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
f1.keywords: ms.teamsadmincenter.signin.domainerror.nolicensedusers
ms.reviewer: ritikag
search.appverid: MET150
description: Learn how to enable or disable user-level access on a per-user basis.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Assign Teams and Teams add-on licenses to users

This article describes how to assign Teams licenses and Teams add-on licenses to users. You can assign or remove Teams licenses and Teams add-on licenses in the Microsoft 365 admin center or by using PowerShell. You must be a Global admin or User management admin to manage licenses.

## Assign Teams licenses to users

You enable or disable Teams at the user level by assigning or removing a Microsoft Teams product license. Each user in your organization must be assigned a Teams license from a licensing plan before they can use Teams. You can assign licenses to new users when new user accounts are created or to users who have existing accounts.

> [!NOTE]
> We recommend that you enable Teams for all users so that teams can be formed organically for projects and other dynamic initiatives. Even if you're running a pilot, it may still be helpful to keep Teams enabled for all users, but only target communications to the pilot group of users.

### Using the Microsoft 365 admin center

You can manage Teams licenses for users on **Active users** page or the **Licenses** page of the Microsoft 365 admin center.

- To enable Teams for a user, switch the toggle next to **Microsoft Teams** to **On**.
- To disable Teams for a user, switch the toggle to **Off**. When the license is disabled, the user will no longer see Teams in the app launcher or homepage.

For detailed steps on how to assign licenses, see [Assign licenses to users](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).

### Using PowerShell

You enable and disable Teams through PowerShell as you would for any other service plan license. Here are the service plan names for Teams:

- Microsoft Teams: TEAMS1
- Microsoft Teams for GCC: TEAMS_GOV
- Microsoft Teams for DoD: TEAMS_DOD

For more information, see:
- [Disable access to services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-with-office-365-powershell).
- [Disable access to services while assigning user licenses](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-while-assigning-user-licenses)

> [!IMPORTANT]
> The [New-MsolLicenseOptions](https://docs.microsoft.com/powershell/module/msonline/new-msollicenseoptions) cmdlet will enable all services that were previously disabled unless explicitly identified in your custom script. For example, if you want to leave both Exchange and Sway disabled while additionally disabling Teams, you'll need to include this in the script or both Exchange and Sway will be enabled for those users you identified. To use a GUI to manage this functionality, see [Office 365 License Reporting and Management Tool -Assign Remove Licenses in Bulk](https://gallery.technet.microsoft.com/Office365-License-cfd9489c) for more information.

#### Example

The following is an example of how to disable Teams for users who have a particular license type. For example, follow these steps to first disable Teams for all users who have a particular licensing plan, and then enable Teams for each individual user who should have access to Teams.

Run the following command to display the licensing plans you have within your organization.

      Get-MsolAccountSku

Run the following commands, where \<plan name> is the name of your organization name and the licnensing plan for your organization. For example, ContosoSchool:ENTERPRISEPACK_STUDENT.

      $acctSKU="<plan name>
      $x = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans "TEAMS1"
      
Run the following command to disable Teams for all users who have an active license for your licensing plan:

      Get-MsolUser | Where-Object {$_.licenses[0].AccountSku.SkuPartNumber -eq  ($acctSKU).Substring($acctSKU.IndexOf(":")+1,  $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} |  Set-MsolUserLicense -LicenseOptions $x

## Assign Teams add-on licenses to users

Add-on licenses are licenses for specific Teams features such as Audio Conferencing, Phone System, and Calling Plans. For more information about the add-on licenses that are available for Teams, and how to buy them depending on your plan, see LINK.

### Assign an add-on license to one user

For steps on how to assign a license to one user, see [Add users individually or in bulk to Office 365}(https://docs.microsoft.com/microsoft-365/admin/add-users/add-users).

### Assign an add-on license to multiple users in bulk

------

## Assign a license to a user for Teams

Teams licenses are managed directly through the Microsoft 365 admin center user management interfaces. An administrator can assign licenses to new users when new user accounts are created, or to users with existing accounts. The administrator must have Office 365 Global Administrator or User Management Administrator privileges to manage Microsoft Teams licenses.



![Screenshot of Product licenses section in admin center.](media/Manage_user_access_to_Microsoft_Teams_image2.png) 

A Teams user license can be disabled at any time. Once the license is disabled, the users access to Microsoft Teams will be prevented and the user will no longer be able to see Teams in the Office 365 app launcher and homepage.

![Screenshot showing Teams selected in the Product licenses section.](media/Manage_user_access_to_Microsoft_Teams_image4.png)

## Manage via PowerShell

> [!IMPORTANT]
> New-MsolLicenseOptions will enable all services that were previously disabled unless explicitly identified in your customized script. As an example, if you wanted to leave both Exchange & Sway disabled while additionally disabling Teams, you'd need to include this in the script or both Exchange & Sway will become enabled for those users you've identified. To use a GUI to manage this functionality, see [Office 365 License Reporting and Management Tool -Assign Remove Licenses in Bulk](https://gallery.technet.microsoft.com/Office365-License-cfd9489c) for more information.

Enabling and disabling Teams as a workload license through PowerShell is done just as any other workload. The service plan name is TEAMS1 for Microsoft Teams. For GCC the service plan name is TEAMS_GOV. For GCC High the service plan name is TEAMS_GCCHIGH. For DoD the service plan name is TEAMS_DOD (See [Disable access to services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-with-office-365-powershell) for more information.)

**Sample:** The following is just a quick sample on how you would disable Teams for everyone in a particular license type. You'll need to do this first, then individually enable it for the users who should have access for piloting purposes.

To display the subscription types you have within your organization, use the following command:

      Get-MsolAccountSku

Fill in the name of your plan that includes your organization name and the plan for your school (such as ContosoSchool:ENTERPRISEPACK_STUDENT), and then run the following commands:

      $acctSKU="<plan name>
      $x = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans "TEAMS1"
To disable Teams for all users with an active license for your named plan, run the following command:

      Get-MsolUser | Where-Object {$_.licenses[0].AccountSku.SkuPartNumber -eq  ($acctSKU).Substring($acctSKU.IndexOf(":")+1,  $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} |  Set-MsolUserLicense -LicenseOptions $x

| | | |
|---------|---------|---------|
|![An icon representing a decision point](media/Manage_user_access_to_Microsoft_Teams_image5.png)     |Decision Point         |<ul><li>What is your organization's plan for Teams onboarding across the organization?  (Pilot or Open)</li></ul>         |
|![An icon representing the next steps](media/Manage_user_access_to_Microsoft_Teams_image6.png)     |Next Steps         |<ul><li>If onboarding via a closed Pilot, decide if you would like to do so via licensing, or targeted communication.</li><li>Depending on decision, take steps to make sure only Pilot users who are allowed to access Teams (if needed).</li><li>Document the guidelines for which users who will (or will not) have access to Teams.</li></ul>         |


<Inserting the bulk license assignment>

`powershell
#Create a text file with a single row containing list of UserPrincipalName (UPN) of users to license. The MSOLservice uses UPN to license user accounts in Office 365.

#Example of text file:
#user1@domain.com
#user2@domain.com

#Import Module
ipmo MSOnline
#Authenticate to MSOLservice.
Connect-MSOLService
#File prompt to select the userlist txt file.
[System.Reflection.Assembly]::LoadWithPartialName("System.windows.forms") | Out-Null
$OFD = New-Object System.Windows.Forms.OpenFileDialog
$OFD.filter = "text files (*.*)| *.txt"
$OFD.ShowDialog() | Out-Null
$OFD.filename
If ($OFD.filename -eq '')
{
 Write-Host "You did not choose a file. Try again" -ForegroundColor White -BackgroundColor Red
}
#Create a variable of all users.
$users = Get-Content $OFD.filename
#License each user in the $users variable.
#Use MCOPSTN1 for PSTN Domestic Calling and MCOPSTN2 for Domestic and
International Calling.
for each ($user in $users)
 {
 Write-host "Assigning License: $user"
 Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:ENTERPRISEPACK " -ErrorAction SilentlyContinue
 Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:MCOEV " -ErrorAction SilentlyContinue
 Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:MCOPSTN1 " -ErrorAction SilentlyContinue
 }

```
## Phone System and Calling Plans product names or SKUs used for scripting

| Product name | SKU part name |
|--------------|---------------|
| Enterprise E5 (with Phone System) | ENTERPRISEPREMIUM |
| Enterprise E3 | ENTERPRISEPACK | 
| Enterprise E1 | STANDARDPACK | 
| Phone System | MCOEV |
| Domestic & International Calling Plan | MCOPSTN2 |
| Domestic Calling Plan (3000 minutes per user/month for US/PR/CA, 1200 minutes per user/month for EU countries) | MCOPSTN1 |
| Domestic Calling Plan (120 minutes per user/month for each country) </br>*Note: This plan is not available in US*. | MCOPSTN5 |
| Domestic Calling Plan (240 minutes per user/month for each country) </br>*Note: This plan is not available in US*. | MCOPSTN6 |
| Communications Credits | MCOPSTNPP | 

## Manage Teams at the Office 365 tenant level
[!INCLUDE [global-switch-expiry-note](includes/global-switch-expiry-note.md)]

## Adding voice features for your Teams users

If you are a small business, go to ---------

If you are an Enterprise or large business, go to --------