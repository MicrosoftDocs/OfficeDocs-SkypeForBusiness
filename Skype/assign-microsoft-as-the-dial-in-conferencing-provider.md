---
title: Assign Microsoft as the dial-in conferencing provider
ms.prod: OFFICE365
ms.assetid: d935a90d-ea61-433d-a820-b400ed9c1f5d
---


# Assign Microsoft as the dial-in conferencing provider

A dial-in conferencing provider supplies the  *conference bridge*  . The conference bridge provides the dial-in phone number, PINs, and conference IDs for meetings that are created. You only need to assign a dial-in conferencing provider to people who are going to schedule or lead Skype for Business meetings.
  
    
    

To be able to see **Microsoft** listed as the dial-in provider, you must assign a **Skype for Business PSTN Conferencing** license to the user.
> [!NOTE]
> If you assign a **Skype for Business PSTN Conferencing** license to a person that doesn't have a third-party conferencing provider, then Microsoft is automatically assigned as the dial-in conferencing provider. You can [Assign a third-party as the dial-in conferencing provider](assign-a-third-party-as-the-dial-in-conferencing-provider.md) if needed.
  
    
    

Dial-in conferencing providers are also called **audio-conferencing providers**.
## Assign Microsoft as the dial-in conferencing provider


### Using the Skype for Business admin center


1. Go to the **Office 365 admin center** > **Skype for Business**.
    
    > [!NOTE]
      > When the provider is changed from another provider to **Microsoft**, the dial-in conferencing information for the user (Conference ID, Toll and Toll-free numbers) will be replaced. You should save this information before changing the provider. 
2. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Dial-in users**, and then select the user from the list of available users.
    
  
3. In the Action pane, click **Edit**.
    
  
4. On the properties page for the user, under **Provider name**, use the drop-down and select Microsoft.
    
    > [!NOTE]
      > Since you are using Microsoft as the dial-in conferencing provider and there are multiple phone numbers, you can use the **Default number** drop-down to select a default dial-in number for the user.
5. Click **Save**.
    
  

### Using a Windows PowerShell script for a small number of users

To save time or automate this, you can use the following PowerShell script to set Microsoft as the dial-in conferencing provider for a small number of users.
  
    
    

> [!NOTE]
> When the provider is changed from another provider to **Microsoft**, the dial-in conferencing information for the user (Conference ID, Toll and Toll-free numbers) will be replaced. You should save this information before changing the provider. 
  
    
    

You can save one or more of the following scripts as a PowerShell script file and then run it.
  
    
    
To change the provider to Microsoft for a small number of users, you can use the  [Enable-CsOnlineDialInConferencingUser](https://technet.microsoft.com/en-us/library/mt243813.aspx).
  
    
    


  
    
    
> **Example 1:** You can run this script by providing a list of users that you want updated.
    

  
    
    
> 
  ```
  
Script.ps1 -UserList <List of users>
  ```


  
    
    
> 
  ```
  
./Script.ps1 -UserList "user01@constoso.com, user02@contoso.com, user03@contoso.com"
  ```


  
    
    
> **Example 2:** You can run this script by providing a .csv file that contains the email address (alias) of each user that you want updated.
    

  
    
    
> 
  ```
  
Script.ps1 -CsvFile <Path of the csv file>
  ```


  
    
    
> 
  ```
  
./Script.ps1 -CsvFile ".\\CsvFile.csv"
  ```


### Using a Windows PowerShell script for a large number of users

To save time or automate this, you can use the following PowerShell script to set Microsoft as the dial-in conferencing provider for a large number of users.
  
    
    

> [!NOTE]
> When the provider is changed from another provider to **Microsoft**, the dial-in conferencing information for the user (Conference ID, Toll and Toll-free numbers) will be replaced. You should save this information before changing the provider. 
  
    
    

You can save one or more of the following scripts as a PowerShell script file and then run it.
  
    
    


  
    
    
> **Example 1:** In this example, you can use this script to change the dial-in conferencing provider from Intercall (or another provider) to **Microsoft** for a large number users in your organization.
    

  
    
    
> 
  ```
  
Script.ps1 -ACPProviderName <Provider>
  ```


  
    
    
> 
  ```
  
./Script.ps1 -ACPProviderName "Intercall"
  ```


    **Here is the script:**
    
  

  
    
    
> 

  
    
    
> 
  ```
  
<#
  ```


  
    
    
> 
  ```
  
.SYNOPSIS

  ```


  ```
  
This is a PowerShell script to set Microsoft as the dial-in conferencing provider of a set of users. It's required for applicable users to have a valid PSTN Conferencing license assigned before their provider is changed.
  ```


  
    
    
> 
  ```
  
.DESCRIPTION
  ```


  
    
    
> 
  ```
  
This is a PowerShell script to set Microsoft as the dial-in conferencing provider of a set of users. It's required for applicable users to have a valid PSTN Conferencing license assigned before their provider is changed.
  ```


  
    
    
> 
  ```
  
.EXAMPLE
  ```


  
    
    
> 
  ```
  
./Script.ps1 -UserList "user01@constoso.com, user02@contoso.com, user03@contoso.com"
  ```


  
    
    
> 
  ```
  
./Script.ps1 -CsvFile ".\\CsvFile.csv"
  ```


  
    
    
> 
  ```
  
./Script.ps1 -ACPProviderName ""Intercall""
  ```


  
    
    
> 
  ```
  
#>
  ```


  
    
    
> 
  ```
  
param (
  ```


  
    
    
> 
  ```
  
[Parameter(Mandatory = $true, ParameterSetName = "CsvFile")]
  ```


  
    
    
> 
  ```
  
 [string]$CsvFile,
  ```


  
    
    
> 
  ```
  
 [Parameter(Mandatory = $true, ParameterSetName = "UserList")]
  ```


  
    
    
> 
  ```
  
 [string]$UserList,
  ```


  
    
    
> 
  ```
  
 [Parameter(Mandatory = $true, ParameterSetName = "ACPProviderName")]
  ```


  
    
    
> 
  ```
  
[string]$ACPProviderName
  ```


  
    
    
> 
  ```
  
)
  ```


  
    
    
> 
  ```
  
if ($CsvFile)
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
if(!(Test-Path $CsvFile))
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
Write-Error "File does not exist."
  ```


  
    
    
> 
  ```
  
Exit
  ```


  
    
    
> 
  ```
  
 }
  ```


  
    
    
> 
  ```
  
$users = Get-Content $CsvFile
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
if ($UserList)
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
$users = $UserList.Split(",")
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
if ($ACPProviderName)
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
$supportedACPProviders = Get-csAudioConferencingProvider
  ```


  
    
    
> 
  ```
  
$providerNameMatch = $supportedACPProviders | ?{$_.Identity -eq $ACPProviderName}
  ```


  
    
    
> 
  ```
  
if ($providerNameMatch -eq $null)
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
Write-Host "The provider name is not from a supported provider, please use any of the following values: "
  ```


  
    
    
> 
  ```
  
$supportedACPProviders      | %{$_.Identity}
  ```


  
    
    
> 
  ```
  
return
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
$allUsersInTenant = Get-csOnlineUser
  ```


  
    
    
> 
  ```
  
$users =  $allUsersInTenant | ?{$_.AcpInfo -ne $null -and $_.ACPInfo.Name -eq $ACPProviderName}
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
Write-Host "Number of users to have their dial-in conferencing provider set to Microsoft: " $users.counts
  ```


  
    
    
> 
  ```
  
foreach ($user in $users)
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
if ($CsvFile -or $UserList)
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
try
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
$adUser = Get-csOnlineUser -Identity $user
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
catch
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
Write-Error "There was an exception while retrieving user: $user. "   $error[0].Exception.Message
  ```


  
    
    
> 
  ```
  
Continue
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
else
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
$adUser = $user
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
if ($adUser -ne $null -and ($adUser.OnlineDialInConferencingPOlicy -ne $null))
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
if ($adUser.AcpInfo -eq $null -Or $adUser.AcpInfo.Name -ne "Microsoft")
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
try
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
$enableUser = Enable-CsOnlineDialInConferencingUser -Identity $adUser.ObjectId -Tenant $adUser.TenantId -ReplaceProvider
  ```


  
    
    
> 
  ```
  
Write-Host "The provider of $user has changed to Microsoft."
  ```


  
    
    
> 
  ```
  
$enableUser
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
catch
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
Write-Error "There was an exception while enabling user: $user. "  $error[0].Exception.Message
  ```


  
    
    
> 
  ```
  
continue;
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
 else
  ```


  
    
    
> 
  ```
  
{
  ```


  
    
    
> 
  ```
  
Write-Warning "The provider of $user is already set to Microsoft."
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
else
  ```


  
    
    
> 
  ```
  
            {
  ```


  
    
    
> 
  ```
  
Write-Error "$user does not have valid PSTN Conferencing license assigned."
  ```


  
    
    
> 
  ```
  
}
  ```


  
    
    
> 
  ```
  
}
  ```

For more information about using Windows PowerShell, see  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038).
  
    
    

## What else should I know?


- A user can be assigned only one dial-in conferencing provider.
    
  
- You can change the dial-in conferencing provider from Microsoft to a third-party provider at any time. To learn more, see  [Assign a third-party as the dial-in conferencing provider](assign-a-third-party-as-the-dial-in-conferencing-provider.md).
    
  
- In your organization, you can have some people who use Microsoft as their dial-in conferencing provider, and others who use a third-party provider. But this is more complicated to set up and manage.
    
  

## Related Topics

 [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md)
  
    
    
 [Set up Skype for Business Online](set-up-skype-for-business-online.md)
  
    
    

