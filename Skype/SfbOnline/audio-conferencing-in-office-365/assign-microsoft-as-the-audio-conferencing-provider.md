---
title: "Assign Microsoft as the audio conferencing provider"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.date: 01/23/2018
ms.topic: article
ms.assetid: d935a90d-ea61-433d-a820-b400ed9c1f5d
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
- Strat_SB_PSTN
description: "Learn how to assign Microsoft the dial-in conferencing provider for Skype for Business. Conferencing bridge."
---

# Assign Microsoft as the audio conferencing provider

An audio conferencing provider supplies the *conference bridge*. The conference bridge provides the dial-in phone numbers, PINs, and conference IDs for meetings that are created. You only need to assign an audio conferencing provider to people who are going to schedule or lead Skype for Business or Microsoft Teams meetings.
  
If you want to be able to see **Microsoft** listed as the audio provider, you must assign an **Audio Conferencing** license to the user.
  
> [!NOTE]
> If you assign an **Audio Conferencing** license to a person who doesn't have a third-party audio conferencing provider, Microsoft is automatically assigned as the audio conferencing provider. You can [Assign a third-party as the audio conferencing provider](assign-a-third-party-as-the-audio-conferencing-provider.md) if needed.
  
## Assign Microsoft as the audio conferencing provider

### Using the Skype for Business admin center

1. Go to the **Office 365 admin center** > **Skype for Business**.
    
    > [!NOTE]
    > When the provider is changed from another provider to **Microsoft**, the audio conferencing information for the user (Conference ID, Toll and Toll-free numbers) will be replaced. You should save this information before changing the provider. 
  
2. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Users**, and then select the user from the list of available users.
    
3. In the Action pane, click **Edit**.
    
4. On the properties page for the user, under **Provider name**, select **Microsoft** in the drop-down list.
    
    > [!NOTE]
    > Because you are using Microsoft as the audio conferencing provider and there are multiple phone numbers, you can use the **Default toll number** drop-down list to select a default audio number for the user.
  
5. Click **Save**.
    
### Using a Windows PowerShell script for a small number of users

To save time or automate this, you can use the following PowerShell script to set Microsoft as the audio conferencing provider for a small number of users.

> [!NOTE]
> When the provider is changed from another provider to **Microsoft**, the audio conferencing information for the user (Conference ID, Toll and Toll-free numbers) will be replaced. You should save this information before changing the provider. 
  
You can save one or more of the following scripts as a PowerShell script file and then run it.
  
To change the provider to Microsoft for a small number of users, you can use the  [Enable-CsOnlineDialInConferencingUser](https://technet.microsoft.com/en-us/library/mt243813.aspx).
  
**Example 1:** You can run this script by providing a list of users that you want updated.
> 
  ```
  Script.ps1 -UserList <List of users>
  ./Script.ps1 -UserList "user01@constoso.com,   user02@contoso.com, user03@contoso.com"
  ```
**Example 2:** You can run this script by providing a .csv file that contains the email address (alias) of each user that you want updated.  
> 
  ```
  Script.ps1 -CsvFile <Path of the csv file>
  ./Script.ps1 -CsvFile ".\\CsvFile.csv"
  ```
### Using a Windows PowerShell script for a large number of users
To save time or automate this, you can use the following PowerShell script to set Microsoft as the audio conferencing provider for a large number of users.

When the provider is changed from another provider to **Microsoft**, the audio conferencing information for the user (Conference ID, Toll and Toll-free numbers) will be replaced. You should save this information before changing the provider. 
  
You can save one or more of the following scripts as a PowerShell script file and then run it.

**Example 1:** In this example, you can use this script to change the audio conferencing provider from Intercall (or another provider) to **Microsoft** for a large number users in your organization.
    
  ```
  Script.ps1 -ACPProviderName <Provider>
  ./Script.ps1 -ACPProviderName "Intercall"
  ```
  Here is the script:

  ```
  <#
  .SYNOPSIS

  This is a PowerShell script to set Microsoft as the audio conferencing provider of a set of users. It's required for applicable users to have a valid PSTN Conferencing license assigned before their provider is changed.

  .DESCRIPTION
  This is a PowerShell script to set Microsoft as the audio conferencing provider of a set of users. It's required for applicable users to have a valid PSTN Conferencing license assigned before their provider is changed.

  .EXAMPLE
  
  ./Script.ps1 -UserList "user01@constoso.com, user02@contoso.com, user03@contoso.com"
  ./Script.ps1 -CsvFile ".\\CsvFile.csv"
  ./Script.ps1 -ACPProviderName ""Intercall""
  #>
  param (
  [Parameter(Mandatory = $true, ParameterSetName = "CsvFile")]
   [string]$CsvFile,
   [Parameter(Mandatory = $true, ParameterSetName = "UserList")]
   [string]$UserList,
   [Parameter(Mandatory = $true, ParameterSetName = "ACPProviderName")]
  [string]$ACPProviderName
  )
  if ($CsvFile)
  {
  if(!(Test-Path $CsvFile))
  {
  Write-Error "File does not exist."
  Exit
   }
  $users = Get-Content $CsvFile
  }
  if ($UserList)
  {
  $users = $UserList.Split(",")
  }
  if ($ACPProviderName)
  {
  $supportedACPProviders = Get-csAudioConferencingProvider
  $providerNameMatch = $supportedACPProviders | ?{$_.Identity -eq $ACPProviderName}
  if ($providerNameMatch -eq $null)
  {
  Write-Host "The provider name is not from a supported provider, please use any of the following values: "
  $supportedACPProviders      | %{$_.Identity}
  return
  }
  $allUsersInTenant = Get-csOnlineUser
  $users =  $allUsersInTenant | ?{$_.AcpInfo -ne $null -and $_.ACPInfo.Name -eq $ACPProviderName}
  }
  Write-Host "Number of users to have their audio conferencing provider set to Microsoft: " $users.count
  foreach ($user in $users)
  {
  if ($CsvFile -or $UserList)
  {
  try
  {
  $adUser = Get-csOnlineUser -Identity $user
  }
  catch
  {
  Write-Error "There was an exception while retrieving user: $user. "   $error[0].Exception.Message
  Continue
  }
  }
  else
  {
  $adUser = $user
  }
  if ($adUser -ne $null -and ($adUser.OnlineDialInConferencingPOlicy -ne $null))
  {
  if ($adUser.AcpInfo -eq $null -Or $adUser.AcpInfo.Name -ne "Microsoft")
  {
  try
  {
  $enableUser = Enable-CsOnlineDialInConferencingUser -Identity $adUser.ObjectId -Tenant $adUser.TenantId -ReplaceProvider
  Write-Host "The provider of $user has changed to Microsoft."
  $enableUser
  }
  catch
  {
  Write-Error "There was an exception while enabling user: $user. "  $error[0].Exception.Message
  continue;
  }
  }
   else
  {
  Write-Warning "The provider of $user is already set to Microsoft."
  }
  }
  else
              {
  Write-Error "$user does not have valid Audio Conferencing license assigned."
  }
  }
  ```
For more information about using Windows PowerShell, see [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038).
  
## What else should I know?

- A user can be assigned only one audio conferencing provider.
    
- You can change the audio conferencing provider from Microsoft to a third-party provider at any time. To learn more, see [Assign a third-party as the audio conferencing provider](assign-a-third-party-as-the-audio-conferencing-provider.md).
    
- In your organization, you can have some people who use Microsoft as their audio conferencing provider, and others who use a third-party provider. But this is more complicated to set up and manage.
    
## Related topics

[Set up Audio Conferencing for Skype for Business and Microsoft Teams](set-up-audio-conferencing.md)
  
[Set up Skype for Business Online](../set-up-skype-for-business-online/set-up-skype-for-business-online.md)

## Feedback?
To provide product feedback or to let us know how we're doing, see [Skype for Business Feedback](https://www.skypefeedback.com).