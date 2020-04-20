---
title: Assign Teams add-on licenses to users (was assign-teams-licenses)
author: LanaChin
ms.author: v-lanac
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_RemoteWorkers
search.appverid: MET150
f1.keywords:
- NOCSH
ms.reviewer: mikedav
description: "Learn how to assign Teams add-on licenses to users for features like Audio Conferencing, Phone System, and Calling Plans."
appliesto: 
  - Microsoft Teams
---

# Assign Teams add-on licenses to users

Add-on licenses are licenses for specific Teams features such as Audio Conferencing, Phone System, and Calling Plans. You can use the Microsoft 365 admin center or PowerShell to assign add-on licenses to users in your organization. You must be a Global admin or User management admin to manage licenses.

See [Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md) for Teams features that are available with add-on licenses. You'll also find information about what licenses you need to buy and how to buy them (depending on your plan), so users can get features such as Audio Conferencing, toll-free numbers, and the ability to call phone numbers outside your organization.

## Using the Microsoft 365 admin center

You can assign Teams add-on licenses on the **Licenses** page or the **Active users** page of the Microsoft 365 admin center. Use the Microsoft 365 admin center to assign licenses to individual users or small groups of users at a time. For example, use the **Licenses** page to assign licenses for up to 20 users at a time. If you need to assign licenses for a large number of users, such as hundreds or thousands of users, use Powershell.

For detailed steps, see [Assign licenses to users](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).

## Using PowerShell

Before you assign Teams add-on licenses to users, you'll need to know the identifier for the license that you want to assign. The identifier is different than the friendly name. For example, the identifier for Audio Conferencing is MCOMEETADV. To learn more, see [Product name and SKU identifiers for licensing](#product-name-and-sku-identifiers-for-licensing).

1. Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
2. Install the Microsoft Azure Active Directory Module for Windows PowerShell:
    1. Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an admin).
    2. Run the following command:
        ```powershell
        Install-Module MSOnline
        ```
    3. If you're prompted to install the NuGet provider, type **Y**, and then press Enter.
    4. If you're prompted to install the module from PSGallery, type **Y**, and then press Enter.
3. At the Windows PowerShell command prompt, run the following script to assign licenses to your users, where \<CompanyName:License> is your organization name and the identifier for the license that you want to assign. For example, Litwareinc:MCOMEETADV. 

    In this example, we assign a Microsoft 365 Enterprise license and an Audio Conferencing license.

    ```powershell
    #Create a text file with a single row containing list of UserPrincipalName(UPN) of users to license. The MSOLservice uses UPN to license user accounts in Office 365.
    #Example of text file:
    #user1@domain.com
    #user2@domain.com

    #Import Module
    ipmo MSOnline

    #Authenticate to MSOLservice
    Connect-MSOLService
    #File prompt to select the userlist txt file
    [System.Reflection.Assembly]::LoadWithPartialName("System.windows.forms") | Out-Null
      $OFD = New-Object System.Windows.Forms.OpenFileDialog
      $OFD.filter = "text files (*.*)| *.txt"
      $OFD.ShowDialog() | Out-Null
      $OFD.filename

    If ($OFD.filename -eq '')
    {
    Write-Host "You did not choose a file. Try again" -ForegroundColor White -BackgroundColor Red
    }

    #Create a variable of all users
    $users = Get-Content $OFD.filename

    #License each user in the $users variable
    foreach ($user in $users)
        {
        Write-host "Assigning License: $user"
        Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:ENTERPRISEPACK " -ErrorAction SilentlyContinue
        Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:MCOMEETADV " -ErrorAction SilentlyContinue
        }
    ```

For more information, see [Assign licenses to user accounts with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell).

### Product name and SKU identifiers for licensing

Here's a partial list of product names and their corresponding SKU part names that you can use as a reference when you use PowerShell to manage add-on licenses in Teams.

For more information, see [View licenses and services with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell), [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference), and [Education SKU reference](sku-reference-edu.md).

| Product name| SKU part name |
|--------------|---------------|
| Enterprise E5 (with Phone System) | ENTERPRISEPREMIUM |
| Enterprise E5 (without Audio Conferencing) | ENTERPRISEPREMIUM_NOPSTNCONF |
| Enterprise E5 (with Audio Conferencing) | ENTERPRISEPREMIUM |
| Enterprise E3 | ENTERPRISEPACK | 
| Enterprise E1 | STANDARDPACK |
| Audio Conferencing | MCOMEETADV | 
| Audio Conferencing Pay Per Minute (pay as you go)</br>Requires Communications Credits to be set up and enabled. | MCOMEETACPEA |
| Business Voice (with Calling Plan) | TBD  |
| Business Voice (without Calling Plan) | TBD |
| Phone System | MCOEV |
| Domestic and International Calling Plan | MCOPSTN2 |
| Domestic Calling Plan (3000 minutes per user/month for US/PR/CA, 1200 minutes per user/month for EU countries) | MCOPSTN1 |
| Domestic Calling Plan (120 minutes per user/month for each country) </br>This plan is not available in the United States. | MCOPSTN5 |
| Domestic Calling Plan (240 minutes per user/month for each country) </br>This plan is not available in the United States. | MCOPSTN6 |
| Communications Credits | MCOPSTNPP |

## Related topics

- [View licenses and services with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)
- [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)
--------

## Phone System and Calling Plans: Tips and scripts for assigning licenses

Here's what you need to know before assigning Audio Conferencing, Phone System, and Calling Plan licenses.

- **Using on-premises PSTN connectivity for hybrid users?** If so, you only need to assign a Phone System license. You should NOT assign a Calling Plan.

- **Latency after assigning licenses**: Because of the latency between Office 365 and Microsoft Teams, it can take up to 24 hours for a user to be assigned a Calling Plan after you assign a license. If after 24 hours the user isn't assigned a Calling Plan, please [contact support for business products - admin help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).

- **Error messages**: You will get an error message if you haven't purchased the correct number of licenses. If you need to buy more Calling Plan licenses, choose **Buy more**.

- **Next steps**: After you assign Calling Plan licenses to your users, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up Calling Plans](set-up-calling-plans.md).

## Assign Audio Conferencing licenses in bulk

1. Download and install [Microsoft Online Services Sign-In Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/?LinkId=625123).

2. Download and install the Windows Azure Active Directory Module. See [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=320628) for download instructions and cmdlet syntax.

Once you get the modules installed, use the Windows PowerShell command prompt and the following syntax to assign the licenses to your users:

The name of the licenses or product names in the script are listed in italics. See [Audio Conferencing product names or SKUS used for scripting](#audio-conferencing-product-names-or-skus-used-for-scripting) for all of the product names.

This example assigns an Enterprise E3 license along with an Audio Conferencing license.

```powershell
#Create a text file with a single row containing list of UserPrincipalName(UPN) of users to license. The MSOLservice uses UPN to license user accounts in Office 365.
#Example of text file:
#user1@domain.com
#user2@domain.com

#Import Module
ipmo MSOnline

#Authenticate to MSOLservice
Connect-MSOLService
#File prompt to select the userlist txt file
[System.Reflection.Assembly]::LoadWithPartialName("System.windows.forms") | Out-Null
  $OFD = New-Object System.Windows.Forms.OpenFileDialog
  $OFD.filter = "text files (*.*)| *.txt"
  $OFD.ShowDialog() | Out-Null
  $OFD.filename

If ($OFD.filename -eq '')
{
Write-Host "You did not choose a file. Try again" -ForegroundColor White -BackgroundColor Red
}

#Create a variable of all users
$users = Get-Content $OFD.filename

#License each user in the $users variable
foreach ($user in $users)
    {
    Write-host "Assigning License: $user"
    Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:ENTERPRISEPACK " -ErrorAction SilentlyContinue
    Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:MCOMEETADV " -ErrorAction SilentlyContinue
    }
```

## Audio Conferencing product names or SKUS used for scripting

| Product name | SKU part name |
|--------------|---------------|
| Audio Conferencing (subscription) | MCOMEETADV | 
| Audio Conferencing Pay Per Minute (pay as you go)</br>*Note: Requires Communications Credits to be set up and enabled*. |    MCOMEETACPEA |
| Enterprise E1 | STANDARDPACK | 
| Enterprise E3 | ENTERPRISEPACK |
| Enterprise E5 (without Audio Conferencing) |     ENTERPRISEPREMIUM_NOPSTNCONF |
| Enterprise E5 (with Audio Conferencing) | ENTERPRISEPREMIUM |

##  Communications Credits

Here's what you need to know before assigning Communications Credits licenses.

- **Enterprise E5 customers**: Even if your users are assigned Enterprise E5 licenses, we still recommend that you assign them Communications Credits licenses.

- **Next steps**: After you assign these licenses, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up Calling Plans](set-up-calling-plans.md).

## Assign a Communications Credits license to one user

The steps are the same as assigning an Office 365 license. See [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## Assign Communications Credits licenses in bulk

Take a look at the sample script for assigning Audio Conferencing licenses. Update it with the info for assigning Communications Credits licenses.

## Related topics

[Set up Calling Plans](set-up-calling-plans.md)
</br>
[Add funds and manage Communications Credits](add-funds-and-manage-communications-credits.md)
