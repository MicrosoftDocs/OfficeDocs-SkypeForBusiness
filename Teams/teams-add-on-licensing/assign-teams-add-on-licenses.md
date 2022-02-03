---
title: Assign Teams add-on licenses to users
author: HowlinWolf-92
ms.author: v-mahoffman
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

Add-on licenses are licenses for specific Teams features such as Audio Conferencing, Phone System, and Calling Plans. This article describes how to assign add-on licenses to individual users and to large sets of users in bulk.

> [!NOTE]
> See [Teams add-on licensing](./microsoft-teams-add-on-licensing.md) for Teams features that are available with add-on licenses. You'll also find information about what licenses you need to buy and how to buy them (depending on your plan), so users can get features such as Audio Conferencing, toll-free numbers, and the ability to call phone numbers outside your organization. After you decide  which features you want for your users, assign the licenses to them.

You can use the Microsoft 365 admin center or PowerShell to assign licenses to users in your organization. You must be a Global admin or User management admin to manage licenses.

## What you need to know before you assign Phone System, Calling Plan, and Communication Credits licenses

Before you get started, review the following requirements:

- If you're using on-premises Public Switched Telephone Network (PSTN) connectivity for hybrid users, you only need to assign a Phone System license. Do NOT assign a Calling Plan license.

- Because of the latency between Microsoft 365 and Microsoft Teams, it can take up to 24 hours for a user to be assigned a Calling Plan after you assign a license. If the user isn't assigned a Calling Plan after 24 hours, [contact support for business products - admin help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).

- You'll get an error message if you haven't purchased the correct number of licenses. If you need to buy more Calling Plan licenses, choose the option to buy more.

- Even if your users are assigned Enterprise E5 licenses, you still need to assign [Communications Credits](../what-are-communications-credits.md) licenses to them if they want to make or receive calls from the PSTN.

- After you assign Calling Plan or Communication Credits licenses to your users, you'll need to get phone numbers for your organization, and then assign those numbers to users. For step-by-step instructions, see [Set up Calling Plans](../set-up-calling-plans.md).

## Using the Microsoft 365 admin center

Use the Microsoft 365 admin center to assign licenses to individual users or small sets of users at a time. 
You assign licenses on the **Licenses** page (for up to 20 users at a time) or the **Active users** page (for up to 40 users at a time). The method you choose depends on whether you want to manage product licenses for specific users or manage user licenses for specific products.

For step-by-step instructions, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

If you need to assign licenses for a large number of users, such as hundreds or thousands of users, use Powershell or [group-based licensing in Azure Active Directory (Azure AD)](/azure/active-directory/users-groups-roles/licensing-groups-assign).  

## Using PowerShell

Use PowerShell to assign licenses to users in bulk.  To learn more, see [Assign licenses to user accounts with PowerShell](/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell).

### Example script

Here's an example of how to use a script to assign licenses to your users.

1. Install the 64-bit version of the [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](/collaborate/connect-redirect?DownloadID=59185).
2. Install the Microsoft Azure Active Directory Module for Windows PowerShell:
    1. Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an admin).
    2. Run the following command:
        ```powershell
        Install-Module MSOnline
        ```
    3. If you're prompted to install the NuGet provider, type **Y**, and then press Enter.
    4. If you're prompted to install the module from PSGallery, type **Y**, and then press Enter.
3. At the Windows PowerShell command prompt, run the following script to assign licenses to your users, where \<CompanyName:License> is your organization name and the identifier for the license that you want to assign. For example, litwareinc:MCOMEETADV.

    The identifier is different than the friendly name of the license. For example, the identifier for Audio Conferencing is MCOMEETADV. To learn more, see [Product names and SKU identifiers for licensing](#product-names-and-sku-identifiers-for-licensing).

    ```powershell
    #Create a text file with a single column that lists the user principal names (UPNs) of users to assign licenses to. The MSOL service uses the UPN to license user accounts.
    #Example of text file:''
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
        Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "litwareinc:<CompanyName:License>" -ErrorAction SilentlyContinue
        Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "litwareinc:<CompanyName:License>" -ErrorAction SilentlyContinue
        }
    ```

    For example, to assign Microsoft 365 Enterprise 1 and Audio Conferencing licenses, use the following syntax in the script:

      ```powershell
      Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "litwareinc:ENTERPRISEPACK" -ErrorAction SilentlyContinue
      Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "litwareinc:MCOMEETADV" -ErrorAction SilentlyContinue
      ```

    To assign a Microsoft Business Voice (without Calling Plan) license, use the following syntax in the script:

      ```powershell
      Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "litwareinc:BUSINESS_VOICE_DIRECTROUTING" -ErrorAction SilentlyContinue
      ```

## Product names and SKU identifiers for licensing

Here's a partial list of product names and their corresponding SKU part names that you can use as a reference when you use PowerShell to manage licenses in Teams.

To learn more, see [View licenses and services with PowerShell](/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell), [Product names and service plan identifiers for licensing](/azure/active-directory/users-groups-roles/licensing-service-plan-reference), and [Education SKU reference](../sku-reference-edu.md).

| Product name| SKU part name |
|--------------|---------------|
| Microsoft Enterprise E5 (with Phone System) | ENTERPRISEPREMIUM |
| Microsoft Enterprise E5 (without Audio Conferencing) | ENTERPRISEPREMIUM_NOPSTNCONF |
| Microsoft Enterprise E5 (with Audio Conferencing) | ENTERPRISEPREMIUM |
| Microsoft Enterprise E3 | ENTERPRISEPACK |
| Microsoft Enterprise E1 | STANDARDPACK |
| Microsoft 365 Business Basic | O365_BUSINESS_ESSENTIALS|
| Microsoft 365 Business Standard | O365_BUSINESS_PREMIUM|
| Microsoft 365 Business | SPB|
| Microsoft Business Voice (Canada)| BUSINESS_VOICE_MED  |
| Microsoft Business Voice (United Kingdom) | BUSINESS_VOICE  |
| Microsoft Business Voice (United States) | BUSINESS_VOICE_MED2  |
| Microsoft Business Voice (without Calling Plan) | BUSINESS_VOICE_DIRECTROUTING  |
| Microsoft Business Voice (without Calling Plan) for the United States| BUSINESS_VOICE_DIRECTROUTING _MED |
| Audio Conferencing | MCOMEETADV | 
| Audio Conferencing Pay Per Minute (pay as you go)</br>*Requires Communications Credits to be set up and enabled.* | MCOMEETACPEA |
| Phone System | MCOEV |
| Domestic and International Calling Plan | MCOPSTN2 |
| Domestic Calling Plan (3000 minutes per user/month for US/PR/CA, 1200 minutes per user/month for EU countries) | MCOPSTN1 |
| Domestic Calling Plan (120 minutes per user/month for each country) </br>*This plan isn't available in the United States.* | MCOPSTN5 |
| Domestic Calling Plan (240 minutes per user/month for each country) </br>*This plan isn't available in the United States.* | MCOPSTN6 |
| Communications Credits | MCOPSTNPP |

## Related topics

- [Teams add-on licensing](./microsoft-teams-add-on-licensing.md)
- [Manage user access to Teams](../user-access.md)
- [View licenses and services with PowerShell](/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)
- [Product names and service plan identifiers for licensing](/azure/active-directory/users-groups-roles/licensing-service-plan-reference)
- [Education SKU reference](../sku-reference-edu.md)
