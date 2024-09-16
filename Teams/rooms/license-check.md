---
title: Find Teams Rooms devices with unsupported licenses 
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: ayerragangu
ms.date: 11/02/2023
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Learn how to find Teams Rooms devices with unsupported licenses.
---

# Find Teams Rooms devices with unsupported licenses

Resource accounts that only have user licenses or Microsoft Teams Shared Device licenses assigned to them aren't supported for use with Microsoft Teams Rooms devices. Resource accounts used with Teams Rooms devices need to be assigned one of the following licenses:

- Microsoft Teams Rooms Pro
- Microsoft Teams Rooms Basic
- Microsoft Teams Rooms Standard (legacy)
- Microsoft Teams Rooms Premium (legacy)

[!INCLUDE [mtr-user-licensing](../includes/mtr-user-licensing.md)]

You have a couple of options for checking whether the resource accounts signed into your Teams Rooms devices have a Teams Rooms license. If you only have a couple Teams Rooms devices, use the steps in [Check the license of a few Teams Rooms devices](#check-the-license-of-a-couple-teams-rooms-devices). If you have more than a few Teams Rooms devices, use the steps in [Check the license of multiple Microsoft Teams Rooms devices](#check-the-license-of-multiple-microsoft-teams-rooms-devices).

For information about Teams Rooms licensing, see [Microsoft Teams Rooms licenses](rooms-licensing.md).

## Check the license of a couple Teams Rooms devices

For a small number of devices, you can see what license your devices have by going to Teams devices in the Teams admin center, and then selecting the device category (**Teams Rooms on Windows**, **Teams Rooms on Android**, or **Surface Hubs**) you want to see.

For example, if you select **Teams devices > Teams Rooms on Windows**, you'll see the following image. The **License** column shows the Teams Rooms license assigned to each device.

:::image type="content" source="../media/mtr-device-inventory-license-focus.png" alt-text="Teams Rooms inventory list with focus on Standard, Pro, and Pro (Trial) licenses.":::

Devices that have the Teams Rooms Pro license can access all the capabilities of their Teams Rooms devices. Devices with other Teams Rooms licenses can access a subset of those features. You can see which features are available to each license in [Teams Rooms Basic and Teams Rooms Pro feature comparison](rooms-licensing.md#teams-rooms-basic-and-teams-rooms-pro-feature-comparison).

## Check the license of multiple Microsoft Teams Rooms devices

Checking licenses for Teams Rooms devices one at a time can be time consuming. To make this process easier, we're making available a sample script that checks the licenses of all your Teams Rooms devices. The script provides you with a list of the resource accounts that are associated with your Teams Rooms devices, organized by license type. Resource accounts with licenses that aren't supported with Teams Rooms devices are grouped together for your review. If resource accounts associated with Teams Rooms devices have an unsupported license type, you'll need to change it to a supported license before July 1, 2023.

Take a look at this short video to see how to use the example script to audit your licenses:

> [!VIDEO https://www.youtube.com/embed/Jd_dT4beJDw]


```PowerShell
<#PSScriptInfo
.VERSION 0.25
 
.GUID 
 
.AUTHOR Peter Lurie, Mark Hodge
 
.COMPANYNAME Microsoft
 
.COPYRIGHT (c) 2022-2023 Peter Lurie & Mark Hodge
 
.TAGS Microsoft Teams Room System Surface Hub MEETING_ROOM for Resource Accounts
 
.LICENSEURI   https://creativecommons.org/licenses/by/4.0/?ref=chooser-v1
 
.PROJECTURI 
 
.ICONURI 
 
.EXTERNALMODULEDEPENDENCIES 
 
.REQUIREDSCRIPTS 
 
.EXTERNALSCRIPTDEPENDENCIES 
 
.RELEASENOTES
 
Version 0.23:  Updated to improve support for CSV output 
 
Version 0.24:  updating file/path UI
 
Version 0.25:  udpated to to filter on the server vs. local per feedback  
 
#>
 
 
 
<#
 
.SYNOPSIS
 
Reports out the list of resource accounts that have assigned licenses, highlighting the ones with Teams Meeting Room liceses in green
 
.DESCRIPTION
 
This script uses Graph Powershell & EXO to check for resource accounts and their licenses. 
 
.PARAMETER 
 
None
 
.NOTES
 
author: Peter Lurie
 
created: 2022-05-10
 
editied: 2023-05-30
 
#>
 
 
 
Function Get-SaveFilePath ([string]$initialDirectory) {  #prompts for filename and path for exporting to CSV, if needed
 
 
 
      Add-Type -AssemblyName System.Windows.Forms
 
      $SaveFileDialog = New-Object System.Windows.Forms.SaveFileDialog
 
      $SaveInitialPath = ".\"
 
      $SaveFileName = "TeamsMeetingRoomLicenses.csv"
 
    $SaveFileDialog.initialDirectory = $SaveInitialPath #Sets current starting path
 
    $SaveFileDialog.filter = "CSV (*.csv)| *.csv"    #Restricts to CSV by default
 
      $SaveFileDialog.FileName = $SaveFileName                   #Default filename 
 
    
 
 $SaveFileDialog.ShowDialog()   #actually asks for the filepath
 
      return $SaveFileDialog.filename #Returns filepath for writing to CSV
 
}
 
 
 
Clear-Host
 
Write-Host
 
Write-Host "Welcome to Meeting Room License Checker." -ForegroundColor Green
 
Write-Host
 
Write-Host "This tool will look through your Exchange Online and AAD to find Resource Account Mailbox UPNs."
 
Write-host "It will then report which resource accounts have Teams Room licenses, which have no license, and which have some other licenses"
 
Write-host "This is ver 0.25." 
 
Write-Host
 
 
 
 
 
#Setup for Graph
 
Write-Host "Loading Microsoft Graph Modules" 
 
If (!(Get-Module -listavailable | Where-Object {$_.name -like "*Microsoft.Graph.Users*"})) 
 
      { 
 
             Install-Module Microsoft.Graph.Users  #-ErrorAction SilentlyContinue 
 
      } 
 
Else 
 
      {     Import-Module Microsoft.Graph.Users  #-ErrorAction SilentlyContinue 
 
      } 
 
Try
 
      {     write-host "Getting ready to connect to the Microsoft Graph" 
 
        Connect-MgGraph -Scopes "User.Read.All"
 
             write-host "Connected successfully the Microsoft Graph" -ForegroundColor Green
 
      }
 
Catch
 
      {     write-host "Unable to connect to your Microsoft Graph Environment" -ForegroundColor Red
 
      }
 
 
 
Write-Host 
 
Write-Host "Getting ready to connect to Exchange Online." -ForegroundColor Green
 
If (!(Get-Module -listavailable | Where-Object {$_.name -like "*ExchangeOnlineManagement*"})) 
 
      {     Install-Module ExchangeOnlineManagement  -ErrorAction SilentlyContinue 
 
      } 
 
Else 
 
      {     Import-Module ExchangeOnlineManagement  -ErrorAction SilentlyContinue 
 
      } 
 
Try
 
      {     write-host "Connecting to your Exchange Online instance"
 
        Connect-ExchangeOnline  -ShowBanner:$false #Note if using GCC, DOD, or a soverign cloud, see docs for this command for the correct -ExchangeEnvironmentName.  Default is Commerical cloud
 
             write-host "Connected successfully to your Exchange Online"  -ForegroundColor Green
 
      }
 
Catch
 
      {     write-host "Unable to connect to your Exchange Online Environment"  -ForegroundColor Red
 
      }
 
 
 
Write-Host 
 
Write-Host "Starting to search for Resource Account Mailbox UPNs and their licenses..." -ForegroundColor Green
 
$StartElapsedTime = $(get-date)
 
[System.Collections.ArrayList]$No_License = @()
 
[System.Collections.ArrayList]$MTR_Premium_License = @()    # Also includes MMR1 license
 
[System.Collections.ArrayList]$MeetingRoom_License = @()   #Teams Meeting Room Standard license
 
[System.Collections.ArrayList]$MeetingRoomPro_License = @()  #Optimal license
 
[System.Collections.ArrayList]$MeetingRoomBasic_License = @()  #Basic license does max out at 25 licenses/tenant
 
[System.Collections.ArrayList]$MeetingRoomOther_License = @()  #Licenses OTHER than what should be applied to a Teams Room Resource Account
 
$Report = [System.Collections.Generic.List[Object]]::new()
 
 
 
#Updated to filter server side and not client side.  See next line for new filter. 
 
#$Room_UPNs = get-mailbox | Where-Object {$_.recipientTypeDetails -eq "roomMailbox"} | Select-Object DisplayName, PrimarySmtpAddress, ExternalDirectoryObjectId  
 
 
 
$Room_UPNs = Get-ExoMailbox -Filter {recipientTypeDetails -eq "RoomMailbox" } -ResultSize unlimited | Select-Object DisplayName, PrimarySmtpAddress, ExternalDirectoryObjectId 
 
Write-Host $Room_UPNs.Length " were found." -ForegroundColor Green
 
Write-Host "Note that resource accounts can contain 0 or multiple licenses. As such, the total of all licenses discovered may be different than the number of resource accounts" -ForegroundColor Yellow
 
Write-Host 
 
 
 
$i,$x = 0,$Room_UPNs.count   #Setup for counting devices
 
if ($null -eq $x) {$x = 1}   #run through the loop at least once to print results, otherwise will get a divide/0 error
 
# Note that resource accounts can contain multiple licenese.  As such, the sum of all licenses may exceed the number of resource accounts
 
 
 
ForEach ($UPN in $Room_UPNs){
 
    $i++
 
      Write-Progress -activity "Searching for resource accounts with licenses..." -status "Scanned: $i of $x" 
 
    $UPN_license =  Get-MgUserLicenseDetail -UserID $UPN.ExternalDirectoryObjectId | Select-Object -ExpandProperty SkuPartNumber
 
    $temp = [pscustomobject]@{'DisplayName'=$UPN.DisplayName;'UPN'=$UPN.PrimarySmtpAddress; 'Licenses'=$UPN_license -join ", "} #pulls out the license from a UPN
 
 
 
    if ($null -eq $UPN_license) {$No_License.add($temp) | Out-Null}  #find resource accounts without licenses
 
 
 
      if ($UPN_license -like "MTR_PREM*" -or $UPN_license -like "MMR_P*" ) {$MTR_Premium_License.add($temp) | Out-Null}   #find resource accounts with legacy MTR Premium  
 
    if ($UPN_license -like "MEETING_ROOM*") {$MeetingRoom_License.add($temp) | Out-Null}   #find resource accounts with legacy Teams Room Standard licenses
 
    if ($UPN_license -like "Microsoft_Teams_Rooms_Pro*") {$MeetingRoomPro_License.add($temp) | Out-Null}   #find resource accounts with meeting room pro licenses
 
      if ($UPN_license -like "Microsoft_Teams_Rooms_Basic*") {$MeetingRoomBasic_License.add($temp) | Out-Null}   #find resource accounts with meeting room basic licenses
 
 
 
    if (!(($UPN_license -like "MEETING_ROOM*" ) -or ($UPN_license -like "Microsoft_Teams_Rooms_*" ) -or ($UPN_License -like "MTR_PREM") -or ($UPN_License -like "MMR_P1")-or ($null -eq $UPN_license) ))  {$MeetingRoomOther_License.add($temp) | Out-Null}  #If there are resource accounts that have other licenses, add them too.
 
 
 
    $Report.Add($temp)   #Creating the file for the CSV, if needed later
 
 
 
    $temp = $null
 
      }
 
 
 
   
 
 
 
    Write-Progress -Completed -activity "Searching for resource accounts with licenses..."
 
 
 
Write-Host
 
 
 
Write-Host $No_License.count "Resource accounts without any licenses.  (Typically these would be bookable rooms without any Teams Meeting technology or resource accounts yet to be licensed.)" -ForegroundColor Cyan
 
$No_License | Sort-Object UPN | Format-Table  
 
Write-Host 
 
Write-Host 
 
Write-Host $MeetingRoom_License.count "resource accounts with Legacy Teams Room Standard licenses. (Typically, these licenses should be upgraded to Teams Room Pro at EA Renewal)." -ForegroundColor Yellow
 
$MeetingRoom_License | Sort-Object UPN | Format-Table
 
Write-Host 
 
Write-Host 
 
Write-Host $MTR_Premium.count "Resource accounts with Teams Room Premium or MMR license. (Typically, these licenses should be migrated to Teams Room Pro at EA Anniversary/Renewal)." -ForegroundColor Red
 
$MTR_Premium | Sort-Object UPN | Format-Table
 
Write-Host 
 
Write-Host 
 
Write-Host $MeetingRoomPro_License.count "Resource accounts with MTR Pro licenses." -ForegroundColor Green
 
$MeetingRoomPro_License | Sort-Object UPN | Format-Table
 
Write-Host 
 
Write-Host 
 
Write-Host $MeetingRoomBasic_License.count "Resource accounts with Teams Room System Basic licenses." -ForegroundColor Green
 
$MeetingRoomBasic_License | Sort-Object UPN | Format-Table
 
Write-Host 
 
Write-Host 
 
Write-Host $MeetingRoomOther_License.count "Resource accounts with licenses other than Teams Room System licenses. (Confirm if these licenses are actually needed)." -ForegroundColor Yellow
 
$MeetingRoomOther_License | Sort-Object UPN | Format-Table
 
Write-Host 
 
Write-Host 
 
 
 
$elapsedTime = $(get-date) - $StartElapsedTime
 
$totalTime = "{0:HH:mm:ss}" -f ([datetime]$elapsedTime.Ticks)
 
Write-Host "Processing took $totalTime."  -ForegroundColor Green
 
Write-Host 
 
Write-Host
 
$answer = read-host -prompt "Do you want to export results to a CSV file?  [y/N]"
 
If ($answer.ToLower() -eq 'y' ) 
 
      {
 
             try {
 
                   $SaveMyFile = Get-SaveFilePath    #Use Get-SaveFilePath function to prompt for filepath information
 
                   $Report |  Sort-Object  UPN  | Export-CSV -Path $SaveMyFile[1] -NoTypeInformation  
 
                   Write-Host "Results Saved." -ForegroundColor green
 
             }
 
             catch {
 
                   Write-Host "Unable to save CSV" -ForegroundColor red
 
                   }
 
      }
 
 
 
Write-Host 
 
Write-host "Note: MgGraph and ExchangeOnline connections were not disconnected.  Use Disconnect-ExchangeOnline and Disconnect-MgGraph if needed."  -ForegroundColor yellow
 
Write-Host 
 
Write-Host "Done" -ForegroundColor Green
```

## See which features require a Microsoft Teams Rooms Pro license

Features that require a Microsoft Teams Rooms Pro license can be identified by looking for the icon on a device's details page. If the device that's currently selected isn't assigned a Microsoft Teams Rooms Pro license, you can't perform the action and a prompt to upgrade is displayed.

:::image type="content" source="../media/mtr-restart-device-dialog.png" alt-text="Dialog showing Teams Rooms device restart options.":::

### Related Content

- [Step 1 - Purchase a license for the Teams Rooms console](../hybrid-meetings-device-config-license.md)

- [Teams add-on licensing](/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing)

- [Manage user access to Teams](/microsoftteams/user-access)

- [View licenses and services with PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell?)

- [Product names and service plan identifiers for licensing](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

- [Education SKU reference](/microsoftteams/sku-reference-edu)

- [How long does it take for new license orders to appear in the license summary](/licensing/license-faq#how-long-does-it-take-for-new-license-orders-to-appear-in-the-license-summary)
