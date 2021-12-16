---
title: Use PowerShell to manage your Shifts connection to Blue Yonder
author: LanaChin
ms.author: v-lanachin
ms.reviewer: 
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Use PowerShell to manage the Shifts connector after you set up a connection to your workforce management system. 
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Use PowerShell to manage your Shifts connection to Blue Yonder

## Overview

The [Microsoft Teams Shifts connector for Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) enables you to integrate the Shifts app in Microsoft Teams with your Blue Yonder workforce management (WFM) system. After you set up a connection, your frontline workers can seamlessly view and manage their schedules in Blue Yonder from within Shifts.

You can use the [Shifts connector wizard](shifts-connector-wizard.md) in the Microsoft 365 admin center or [PowerShell](shifts-connector-blue-yonder-powershell-setup.md) to set up a connection. After a connection is set up, you manage it by using [Shifts connector PowerShell cmdlets](#shifts-connector-cmdlets).

This article describes how to use PowerShell to do the following:

- [Check connection setup status](#check-connection-setup-status)
- [View an error report for a connection](#view-an-error-report-for-a-connection)
- [Resolve connection errors](#resolve-connection-errors)
- [Change connection settings](#change-connection-settings)
- [Disable a connection](#disable-a-connection)

> [!NOTE]
> This article assumes that you've already set up a connection to Blue Yonder, either by using the wizard or PowerShell.

## Before you begin

[!INCLUDE [shifts-connector-admin-role](../../includes/shifts-connector-admin-role.md)]

## Set up your environment

> [!NOTE]
> Make sure you follow these steps to set up your environment before running any of the commands or scripts in this article.

[!INCLUDE [shifts-connector-set-up-environment](../../includes/shifts-connector-set-up-environment.md)]

## Check connection setup status
<a name="setup_status"> </a>

To check the status of the connection you set up using the operation ID:

1. [Set up your environment](#set-up-your-environment) (if you haven't already).
1. Run the following command. This command gives you the overall status of the team mappings for the connection.

    ``` powershell
    Get-CsTeamsShiftsConnectionOperation -OperationId <YourOperationId>
    ```

To learn more, see [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation?view=teams-ps).

## View an error report for a connection
<a name="error_report"> </a>

You can run a report that shows error details for a connection. The report lists team and user mappings that succeeded and failed. It also provides information about any issues related to the accounts associated with the connection.

1. [Set up your environment](#set-up-your-environment) (if you haven't already).
1. Run the following command.

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. To view a specific error report, run the following command:

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ErrorReportId <ErrorReportId>
    ```

To learn more, see [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport?view=teams-ps).

## Resolve connection errors

### User mapping errors

User mapping errors may occur if one or more users in a Blue Yonder site isn't a member of the mapped team in Teams. To resolve this issue, make sure that the users in the mapped team match the users in the Blue Yonder site.

### Account authorization errors

Account authorization errors may occur if the Blue Yonder service account or Microsoft 365 system account credentials are incorrect or don't have the required permissions.

To change your Microsoft 365 system account, you can run the [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance?view=teams-ps) cmdlet to update the account or use the PowerShell script in the [Change connection settings](#change-connection-settings) section of this article.

## Change connection settings
<a name="change_settings"> </a>

Use this script to change connection settings. Settings that you can change include your Blue Yonder service account and password, Microsoft 365 service account, team mappings, and sync settings.

Sync settings include the sync frequency (in minutes) and the schedule data that's synced between Blue Yonder and Shifts. Schedule data is defined in the following parameters, which you can view by running [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector?view=teams-ps).

- The **enabledConnectorScenarios** parameter defines data that's synced from Blue Yonder to Shifts. Options are `Shift`, `SwapRequest`, `UserShiftPreferences`, `OpenShift`, `OpenShiftRequest`, `TimeOff`, `TimeOffRequest`.
- The **enabledWfiScenarios** parameter defines data that's synced from Shifts to Blue Yonder. Options are `SwapRequest`, `OpenShiftRequest`,  `TimeOffRequest`, `UserShiftPreferences`.

> [!NOTE]
> For settings that you don't want to change, you'll need to re-enter those original settings when you run this script.

[Set up your environment](#set-up-your-environment) (if you haven't already), and then run the following script.

```powershell
#Update script
Write-Host "Update work flow"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
	Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 3.0
} catch {
	throw
}

#Authenticate with powershell as to the authorization capabilities of the caller. 
#Connect to Teams
Write-Host "Connecting to Teams"
Connect-MicrosoftTeams
Write-Host "Connected"

#Connect to MS Graph
Connect-MgGraph -Scopes "User.Read.All","Group.ReadWrite.All"

#List connector types available (comment out if not implemented for preview) 
Write-Host "Listing connector types available"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$blueYonder = $connectors | where {$_.Id -match $BlueYonderId}

#List connection instances available
Write-Host "Listing connection instances available"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Prompt for the WFM username and password 
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Get the instance ID
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$InstanceId = Read-Host -Prompt 'Input the instance ID that you want to update'
$Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
$Etag = $Instance.etag

#Add comment in the code about how the WFM username/pw is not required for changing any of the other settings. 

#Change sync setting
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$UpdatedInstanceName = Read-Host -Prompt 'Input new connection instance name'
$updatedConnectorScenarioString = Read-Host -Prompt 'Input new enabled connector scenarios'
$updatedWfiScenarioString = Read-Host -Prompt 'Input new enabled WFI scenarios'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$updatedConnectorScenario = $updatedConnectorScenarioString -Split {$Delimiters -contains $_}
$updatedConnectorScenario = $updatedConnectorScenario.Trim()
$updatedConnectorScenario = $updatedConnectorScenario.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
$updatedWfiScenario = $updatedWfiScenarioString -Split {$Delimiters -contains $_}
$updatedWfiScenario = $updatedWfiScenario.Trim()
$updatedWfiScenario = $updatedWfiScenario.Split('', [System.StringSplitOptions]::RemoveEmptyEntries)
$adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
$cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
$essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
$federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
$retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
$siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
$syncFreq = Read-Host -Prompt 'Input new sync frequency'
#Read admin email list
[psobject[]]$AdminEmailList = @()
while ($true){
$AdminEmail = Read-Host -Prompt "Enter admin's email to receive error report"
$AdminEmailList += $AdminEmail
$title    = 'Adding another email'
$question = 'Would you like to add another admin email?'
$choices  = '&Yes', '&No'
$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $teamsUserId -EnabledConnectorScenario $updatedConnectorScenario -EnabledWfiScenario $updatedWfiScenario -Name $UpdatedInstanceName -SyncFrequencyInMin $syncFreq -IfMatch $Etag -ConnectorAdminEmail AdminEmailList

#Get a list of the mappings
Write-Host "Listing mappings"
$TeamMaps = Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId
write $TeamMaps

#Modify a mapping
#Remove a mapping 
Write-Host "Removing a mapping"
$TeamsTeamId = Read-Host -Prompt 'Input the Teams team ID that you want to unlink'
$WfmTeamId = Read-Host -Prompt 'Input the WFM team ID that you want to unlink'
Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId
Write-Host "Success"

#Add a mapping 
Write-Host "Adding a mapping"
New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone "America/Los_Angeles" -WfmTeamId $WfmTeamId
Write-Host "Success"
```

## Disable a connection

Use this script to turn off sync for a connection. Keep in mind this script doesn't remove or delete a connection. It turns off sync so that no data is synced between Shifts and Blue Yonder for the connection that you specify. 

[Set up your environment](#set-up-your-environment) (if you haven't already), and then run the following script.

```powershell
#Oh oh! Script 
Write-Host "Oh oh! work flow"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
	Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 3.0
} catch {
	throw
}

#Authenticate with powershell as to the authorization capabilities of the caller. 
#Connect to Teams
Write-Host "Connecting to Teams"
Connect-MicrosoftTeams
Write-Host "Connected"

#List connection instances available 
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
	$InstanceId = Read-Host -Prompt 'Input the instance ID that you want to disable sync'
	$Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
	$Etag = $Instance.etag
	$InstanceName = $Instance.Name
	$DesignatedActorId = $Instance.designatedActorId
	$adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
	$cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
	$essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
	$federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
	$retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
	$siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
}
else {
	throw "Instance list is empty"
}

#Remove scenarios in the mapping
Write-Host "Disabling scenarios in the team mapping"
$UpdatedInstanceName = $InstanceName + " - Disabled"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $DesignatedActorId -EnabledConnectorScenario @() -EnabledWfiScenario @() -Name $UpdatedInstanceName -SyncFrequencyInMin 60 -IfMatch $Etag

if ($UpdatedInstance.Id -ne $null) {
	Write-Host "Success"
}
else {
	throw "Update instance failed"
}
```

## Shifts connector cmdlets

For help with Shifts connector cmdlets, search for **CsTeamsShiftsConnection** in the [Teams PowerShell cmdlet reference](/powershell/teams/intro?view=teams-ps). Here are links to some commonly used cmdlets.

- [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation?view=teams-ps)
- [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance?view=teams-ps)
- [Get-CsTeamsShiftsConnectionInstance](/powershell/module/teams/get-csteamsshiftsconnectioninstance?view=teams-ps)
- [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance?view=teams-ps)
- [Remove-CsTeamsShiftsConnectionInstance](/powershell/module/teams/remove-csteamsshiftsconnectioninstance?view=teams-ps)
- [Test-CsTeamsShiftsConnectionValidate](/powershell/module/teams/test-csteamsshiftsconnectionvalidate?view=teams-ps)
- [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap?view=teams-ps)
- [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap?view=teams-ps)
- [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap?view=teams-ps)
- [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector?view=teams-ps)
- [Get-CsTeamsShiftsConnectionSyncResult](/powershell/module/teams/get-csteamsshiftsconnectionsyncresult?view=teams-ps)
- [Get-CsTeamsShiftsConnectionUser](/powershell/module/teams/get-csteamsshiftsconnectionuser?view=teams-ps)
- [Get-CsTeamsShiftsConnectionWfmTeam](/powershell/module/teams/get-csteamsshiftsconnectionwfmteam?view=teams-ps)
- [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport?view=teams-ps)
- [Remove-CsTeamsShiftsScheduleRecord](/powershell/module/teams/remove-csteamsshiftsschedulerecord?view=teams-ps)

## Related articles

- [Shifts connectors](shifts-connectors.md)
- [Manage the Shifts app](manage-the-shifts-app-for-your-organization-in-teams.md)
- [Teams PowerShell overview](../../teams-powershell-overview.md)