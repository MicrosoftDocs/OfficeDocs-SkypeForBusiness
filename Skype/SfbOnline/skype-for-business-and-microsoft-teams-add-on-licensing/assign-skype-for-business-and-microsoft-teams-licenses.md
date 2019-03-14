---
title: "Assign Skype for Business licenses"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav
ms.topic: article
ms.assetid: fd41934d-f2eb-4a1b-89d8-32cb37702b33
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection:
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- Licensing
description: "Learn how to assign Skype for Business licenses for Phone System, Audio Conferencing, Calling Plans, and Communications Credits. "
---

# Assign Skype for Business licenses

This article gives you tips about assigning licenses to your users for features like Audio Conferencing, Phone System, and Calling Plans. It also provides scripts for assigning licenses in bulk.

> [!IMPORTANT]
> See [Skype for Business add-on licensing](skype-for-business-and-microsoft-teams-add-on-licensing.md) for information about what licenses you need to buy and **how to buy** them - depending on your Office 365 plan - so users get Audio Conferencing, toll-free numbers, and the ability to call phone numbers outside your business.


## Phone System and Calling Plans: Tips and scripts for assigning licenses

What you need to know before assigning Audio Conferencing, Phone System and Calling Plan licenses

- **Using on-premises PSTN connectivity for hybrid users?** If so, you only need to assign a **Phone System** license. You should **NOT** assign a Calling Plan.

- **Latency after assigning licenses**: Because of the latency between Office 365 and Skype for Business Online, it can possibly take up to 24 hours for a user to be assigned a Calling Plan after you assign a license. If after 24 hours the user isn't assigned a Calling Plan, please [Contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).

- **Error messages**: You will get an error message if you haven't purchased the correct number of licenses. If you need to buy more Calling Plan licenses, choose **Buy more**.
    
- **Next steps**: After you assign Calling Plan licenses to your users, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up Calling Plans](/microsoftteams/set-up-calling-plans).
    
### How to assign a Phone System and Calling Plan license to one user

The steps are the same as assigning an Office 365 license. See [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

### How to assign Phone System and Calling Plan licenses in bulk

1. Install the **Microsoft Online Services Sign-In Assistant for IT Professionals RTW**. Don't have the module installed? See [Microsoft Online Services Sign-In Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/?LinkId=625123) to download it.

2. Install the **Windows Azure Active Directory Module.** Don't have the module installed? See [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=320628) for download instructions and cmdlet syntax.

3. Once you get the modules installed, use the Windows PowerShell command prompt and the following syntax to assign the licenses to your users:

   This example assigns an **Enterprise E3 license** along with a **Phone System** and a **Domestic Calling Plan** license.

   The name of the licenses or product names in the script are listed in italics text (see **Phone System and Calling Plan product names or SKUs used for scripting**, after the example).

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
   ### Phone System and Calling Plans product names or SKUs used for scripting

|**Product name**|**SKU part name**|
|:-----|:-----|
|Enterprise E5 (with Phone System)  <br/> |ENTERPRISEPREMIUM  <br/> |
|Enterprise E3  <br/> |ENTERPRISEPACK  <br/> |
|Enterprise E1  <br/> |STANDARDPACK  <br/> |
|Skype for Business Online Standalone Plan 2  <br/> |MCOSTANDARD  <br/> |
|Phone System  <br/> |MCOEV  <br/> |
|International Calling Plan  <br/> |MCOPSTN2  <br/> |
|Domestic Calling Plan  <br/> |MCOPSTN1  <br/> |
|Communications Credits  <br/> |MCOPSTNC  <br/> |

## Audio Conferencing: Tips and scripts for assigning licenses

### What you need to know before assigning Audio Conferencing licenses

- **Third-party audio conferencing provider**: If someone is already set up to use a third-party audio conferencing provider, when you assign them an **Audio Conferencing** license, they will be changed to use Microsoft as the audio conferencing provider. You can change them back to the third-party provider.

- Next steps: After you assign **Audio Conferencing** licenses, you need to assign an audio conferencing provider. See [Assign Microsoft as the audio conferencing provider].

### How to assign an Audio Conferencing license to one user

The steps are the same as assigning an Office 365 license. See [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

### How to assign Audio Conferencing licenses in bulk

1. Download and install [Microsoft Online Services Sign-In Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/?LinkId=625123).

2. Download and install the **Windows Azure Active Directory Module.** See[Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=320628) for download instructions and cmdlet syntax.

    Once you get the modules installed, use the Windows PowerShell command prompt and the following syntax to assign the licenses to your users:

    The name of the licenses or product names in the script are listed in italics text. See [Audio Conferencing product names or SKUs used for scripting](assign-skype-for-business-and-microsoft-teams-licenses.md#sku) for all of the product names.

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

### Audio Conferencing product names or SKUs used for scripting
<a name="sku"> </a>

|**Product name**|**SKU part name**|
|:-----|:-----|
|Audio Conferencing  <br/> |MCOMEETADV  <br/> |
|Skype for Business Online Standalone Plan 2  <br/> |MCOSTANDARD  <br/> |
|Enterprise E1  <br/> |STANDARDPACK  <br/> |
|Enterprise E3  <br/> |ENTERPRISEPACK  <br/> |
|Enterprise E5 (without Audio Conferencing)  <br/> |ENTERPRISEPREMIUM_NOPSTNCONF  <br/> |
|Enterprise E5 (with Audio Conferencing)  <br/> |ENTERPRISEPREMIUM  <br/> |

## Communications Credits

### What you need to know before assigning Communications Credits licenses

- **Enterprise E5 customers**: Even if your users are assigned Enterprise E5 licenses, we still recommend that you assign them **Communications Credits** licenses.
    
- **Next steps**: After you assign these licenses, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up Calling Plans](/microsoftteams/set-up-calling-plans).
    
### How to assign a Communications Credits license to one user

The steps are the same as assigning an Office 365 license. See [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

### How to assign Communications Credits licenses in bulk

Take a look at the sample script for assigning **Audio Conferencing** licenses. Update it with the info for assigning **Communications Credits** licenses.

## Related topics
  
[Set up Calling Plans](/microsoftteams/set-up-calling-plans)
  
[Add funds and manage Communications Credits](/microsoftteams/add-funds-and-manage-communications-credits)
  
  
 
