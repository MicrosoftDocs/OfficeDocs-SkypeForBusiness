---
title: Assign Skype for Business licenses
ms.prod: OFFICE365
ms.assetid: fd41934d-f2eb-4a1b-89d8-32cb37702b33
---


# Assign Skype for Business licenses

This article gives you tips about assigning Skype for Business licenses to your users. It also provides scripts for assigning licenses in bulk. 
  
    
    

 **IMPORTANT**: See [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md) for information about what licenses you need to buy and **how to buy** them - depending on your Office 365 plan - so users get dial-in conferencing, toll free numbers, and the ability to call phone numbers outside your business.
## Cloud PBX and PSTN Calling: Tips and scripts for assigning licenses


### What you need to know before assigning Cloud PBX and PSTN Calling licenses


- **IMPORTANT**: For you to see the **Voice** option in the left navigation in the Skype for Business admin center, you must first buy at least one **Enterprise E5 license**, one **Skype for Business Cloud PBX** add-on license, or one **Skype for Business PSTN Conferencing** add-on license.
    
    
    
  
- **Using on-premises PSTN connectivity for hybrid users?** If so, you only need to assign a Skype for Business Cloud PBX license. You should **NOT** assign a PSTN Calling plan.
    
  
- **Latency after assigning licenses**: Because of the latency between Office 365 and Skype for Business Online, it can possibly take up to 24 hours for a user to be enabled for PSTN Calling after you assign a license. If after 24 hours, the user isn't enabled for PSTN Calling please [Contact support for business products - Admin Help](http://technet.microsoft.com/library/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b%28Office.14%29.aspx).
    
  
- **Error messages**: You will get an error message if you haven't purchased the correct number of licenses. If you need to buy more licenses to enable this user for PSTN Calling, choose **Buy more**. 
    
  
- **Next steps**: After you assign PSTN Calling plan licenses to your users, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up PSTN Calling for Skype for Business](set-up-pstn-calling-for-skype-for-business.md).
    
  

### How to assign a Cloud PBX and PSTN Calling license to one user

The steps are the same as assigning an Office 365 license. See  [Assign or remove licenses for Office 365 for business](http://technet.microsoft.com/library/997596b5-4173-4627-b915-36abac6786dc%28Office.14%29.aspx). 
  
    
    

### How to assign Cloud PBX and PSTN Calling licenses in bulk


1. Install the **Microsoft Online Services Sign-In Assistant for IT Professionals RTW**. Don't have the module installed? See [Microsoft Online Services Sign-In Assistant for IT Professionals RTW ](https://go.microsoft.com/fwlink/?LinkId=625123) to download it.
    
  
2. Install the **Windows Azure Active Directory Module.** Don't have the module installed? See [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=320628) for download instructions and cmdlet syntax.
    
  
3. Once you get the modules installed, use the Windows PowerShell command prompt and the following syntax to assign the licenses to your users:
    
    This example assigns an **Enterprise E3 license** along with a **Skype for Business Cloud PBX** and **Skype for Business PSTN Domestic Calling PSTN calling plan** license.
    
    The name of the licenses or product names in the script are listed in italics text (see **Cloud PBX and PSTN Calling product names or SKUs used for scripting**, after the example).
    


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
#Use MCOPSTN1 for PSTN Domestic Calling and MCOPSTN2 for Domestic and International Calling.
foreach ($user in $users)
    {
    Write-host "Assigning License: $user"
    Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:ENTERPRISEPACK " -ErrorAction SilentlyContinue
    Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:MCOEV " -ErrorAction SilentlyContinue
    Set-MsolUserLicense -UserPrincipalName $user -AddLicenses "companyname:MCOPSTN1 " -ErrorAction SilentlyContinue
    } 

  ```


### Cloud PBX and PSTN Calling product names or SKUs used for scripting



|**Product name**|**SKU part name**|
|:-----|:-----|
|Enterprise E5 (with Cloud PBX)  <br/> |ENTERPRISEPREMIUM  <br/> |
|Enterprise E3  <br/> |ENTERPRISEPACK  <br/> |
|Enterprise E1  <br/> |STANDARDPACK  <br/> |
|Skype for Business Online Standalone Plan 2  <br/> | MCOSTANDARD <br/> |
|Skype for Business Cloud PBX  <br/> |MCOEV  <br/> |
|Skype for Business PSTN Domestic and International Calling  <br/> |MCOPSTN2  <br/> |
|Skype for Business PSTN Domestic Calling  <br/> |MCOPSTN1  <br/> |
|Skype for Business PSTN Consumption  <br/> |MCOPSTNPP  <br/> |
   

## PSTN conferencing: Tips and scripts for assigning licenses


  
    
    

### What you need to know before assigning PSTN conferencing licenses


- **Third-party conferencing provider**: If someone is already set up to use a third-party dial-in conferencing provider, when you assign them a **Skype for Business PSTN Conferencing** license, they will be changed to use Microsoft as the dial-in conferencing provider. You can change them back to the third-party provider.
    
  
- Next steps: After you assign PSTN conferencing licenses, you need to assign a dial-in conferencing provider. Do one of the following:
    
  -  [Assign Microsoft as the dial-in conferencing provider](assign-microsoft-as-the-dial-in-conferencing-provider.md)
    
  
  - Or,  [Assign a third-party as the dial-in conferencing provider](assign-a-third-party-as-the-dial-in-conferencing-provider.md)
    
  

### How to assign a PSTN Conferencing license to one user

The steps are the same as assigning an Office 365 license. See  [Assign or remove licenses for Office 365 for business](http://technet.microsoft.com/library/997596b5-4173-4627-b915-36abac6786dc%28Office.14%29.aspx). 
  
    
    

### How to assign PSTN conferencing licenses in bulk


1. Download and install  [Microsoft Online Services Sign-In Assistant for IT Professionals RTW ](https://go.microsoft.com/fwlink/?LinkId=625123).
    
  
2. Download and install the **Windows Azure Active Directory Module.** See [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=320628) for download instructions and cmdlet syntax.
    
    Once you get the modules installed, use the Windows PowerShell command prompt and the following syntax to assign the licenses to your users:
    
    The name of the licenses or product names in the script are listed in italics text. See  [Assign several PSTN conferencing licenses at the same time](http://technet.microsoft.com/library/9a193817-3da1-4198-a000-30c682510119%28Office.14%29.aspx#bk_sku) for all of the product names.
    
    This example assigns an Enterprise E3 license along with a PSTN Conferencing license.
    


  ```
  
#Create a text file with a single row containing list of UserPrincipalName (UPN) of users to license. The MSOLservice uses UPN to license user accounts in Office 365.
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


### Dial-in conferencing product names or SKUs used for scripting



|**Product name**|**SKU part name**|
|:-----|:-----|
|Skype for Business PSTN Conferencing  <br/> |MCOMEETADV  <br/> |
|Skype for Business Online Standalone Plan 2  <br/> |MCOSTANDARD  <br/> |
|Enterprise E1  <br/> | STANDARDPACK <br/> |
|Enterprise E3  <br/> |ENTERPRISEPACK  <br/> |
|Enterprise E5 (with dial-in conferencing)  <br/> |ENTERPRISEPREMIUM_NOPSTNCONF  <br/> |
|Enterprise E5 (with dial-in conferencing)  <br/> |ENTERPRISEPREMIUM  <br/> |
   

## PSTN Consumption


### What you need to know before assigning PSTN Consumption licenses


- **Enterprise E5 customers**: Even if your users are assigned Enterprise E5 licenses, we still recommend that you assign them **Skype for Business PSTN Consumption** licenses.
    
  
- **Next steps**: After you assign these licenses, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up PSTN Calling for Skype for Business](set-up-pstn-calling-for-skype-for-business.md).
    
  

### How to assign a PSTN Consumption license to one user

 The steps are the same as assigning an Office 365 license. See [Assign or remove licenses for Office 365 for business](http://technet.microsoft.com/library/997596b5-4173-4627-b915-36abac6786dc%28Office.14%29.aspx). 
  
    
    

### How to assign PSTN Consumption licenses in bulk

Take a look at the sample script for assigning PSTN Conferencing licenses. Update it with the info for assigning PSTN Consumption licenses. 
  
    
    

## Related articles

 [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md)
  
    
    
 [Set up PSTN Calling for Skype for Business](set-up-pstn-calling-for-skype-for-business.md)
  
    
    
 [Add funds and manage Skype for Business PSTN Consumption](add-funds-and-manage-skype-for-business-pstn-consumption.md)
  
    
    

