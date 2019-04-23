---
title: Assign Teams licenses
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 12/14/2018
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
ms.reviewer: mikedav
description: "Learn how to assign licenses for features like Audio Conferencing, Phone System, and Calling plans."
appliesto: 
- Microsoft Teams
---

# Assign Microsoft Teams licenses

You can assign licenses to your users for features like Audio Conferencing, Phone System, and Calling Plans. This article explains how to add these licenses in bulk and for an individual user. 

> [!IMPORTANT]
> See [Microsoft Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md) for information about what licenses you need to buy and how to buy them, depending on your Office 365 plan, so users get Audio Conferencing, toll-free numbers, and the ability to call phone numbers outside your business.

## Phone System and Calling Plans: Tips and scripts for assigning licenses

Here’s what you need to know before assigning Audio Conferencing, Phone System, and Calling Plan licenses.

- **Using on-premises PSTN connectivity for hybrid users?** If so, you only need to assign a Phone System license. You should NOT assign a Calling Plan.

- **Latency after assigning licenses**: Because of the latency between Office 365 and Microsoft Teams, it can take up to 24 hours for a user to be assigned a Calling Plan after you assign a license. If after 24 hours the user isn't assigned a Calling Plan, please [contact support for business products - admin help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).

- **Error messages**: You will get an error message if you haven't purchased the correct number of licenses. If you need to buy more Calling Plan licenses, choose **Buy more**.

- **Next steps**: After you assign Calling Plan licenses to your users, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up Calling Plans](set-up-calling-plans.md).

## Assign a Phone System and Calling Plan license to one user

The steps are the same as assigning an Office 365 license. See [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## Assign Phone System and Calling Plan licenses in bulk

1. Install the Microsoft Online Services Sign-In Assistant for IT Professionals RTW. Don't have the module installed? See [Microsoft Online Services Sign-In Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/?LinkId=625123) to download it.

2. Install the Windows Azure Active Directory Module. Don't have the module installed? See [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=320628) for download instructions and cmdlet syntax.

3. Once you get the modules installed, use the Windows PowerShell command prompt and the following syntax to assign the licenses to your users:

This example assigns an Enterprise E3 license along with a Phone System and a Domestic Calling Plan license.

The name of the licenses or product names in the script are listed in italics (see [Phone System and Calling Plans product names or SKUs used for scripting](#phone-system-and-calling-plans-product-names-or-skus-used-for-scripting), after the example).

```
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

## Audio Conferencing: tips and scripts for assigning licenses

Here's what you need to know before assigning Audio Conferencing licenses.

- **Third-party audio conferencing provider**: If someone is already set up to use a third-party audio conferencing provider, when you assign them an Audio Conferencing license, they will be changed to use Microsoft as the audio conferencing provider. You can change them back to the third-party provider.

- **Next steps**: After you assign Audio Conferencing licenses, you need to assign an audio conferencing provider. See [Assign Microsoft as the audio conferencing provider](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/assign-microsoft-as-the-audio-conferencing-provider).

## Assign an Audio Conferencing license to one user

The steps are the same as assigning an Office 365 license. See [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## Assign Audio Conferencing licenses in bulk

1. Download and install [Microsoft Online Services Sign-In Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/?LinkId=625123).

2. Download and install the Windows Azure Active Directory Module. See [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=320628) for download instructions and cmdlet syntax.

Once you get the modules installed, use the Windows PowerShell command prompt and the following syntax to assign the licenses to your users:

The name of the licenses or product names in the script are listed in italics. See [Audio Conferencing product names or SKUS used for scripting](#audio-conferencing-product-names-or-skus-used-for-scripting) for all of the product names.

This example assigns an Enterprise E3 license along with an Audio Conferencing license.

```
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
| Audio Conferencing Pay Per Minute (pay as you go)</br>*Note: Requires Communications Credits to be set up and enabled*. |	MCOMEETACPEA |
| Enterprise E1 | STANDARDPACK | 
| Enterprise E3 | ENTERPRISEPACK |
| Enterprise E5 (without Audio Conferencing) | 	ENTERPRISEPREMIUM_NOPSTNCONF |
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
