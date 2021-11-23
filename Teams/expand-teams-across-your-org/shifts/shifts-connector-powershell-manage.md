---
title: Use PowerShell to manage the Shifts connector
author: LanaChin
ms.author: v-lanachin
ms.reviewer: 
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use PowerShell to manage and configure the Shifts connector. You can change connection settings, view the health of the connection, disable the connection, and more. 
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Use PowerShell to manage the Shifts connector

## Overview

Shifts connectors enable you to integrate Shifts, the schedule management tool in Microsoft Teams, with your workforce management (WFM) system. Your frontline workers can seamlessly view and manage their schedules in your WFM system from within Shifts.

You can use the [Shifts connector wizard](shifts-connector-wizard.md) in the Microsoft 365 admin center or PowerShell to set up a connection. After you set up a connection, you manage the connection using PowerShell. We provide PowerShell scripts that you can use to change connection settings such as sync settings and team mappings, view connection health, disable a connection, and more.

## Before you begin

### Prerequisites

Before you get started, make sure you have the following prerequisites:

- Blue Yonder version 2020.3, 2021.1, or 2021.2. </br>If you have 2020.3 or 2021.1, we recommend applying the 2020.3.0.4 or 2021.1.0.3 patch. The patch has a fix required for users to update their availability in Shifts.
- Blue Yonder service account name and password and service URLs. </br>If you don’t have this information, contact your Blue Yonder delivery partner or technical account manager. The account is created at the root enterprise level by a Blue Yonder enterprise administrator and must have APIAccess, Client Admin, and Store Manager access. The account and password are required to create a connection.
- Federated SSO authentication is enabled in your Blue Yonder environment. Contact your Blue Yonder delivery partner or technical account manager to make sure federated SSO be enabled. They'll need the following information:

    - federatedSSOValidationService: `https://amer.wfmconnector.teams.microsoft.com/api/v1/fedauth/{tenantId}/6A51B888-FF44-4FEA-82E1-839401E9CD74/authorize` where {tenantId} is your tenantId
     - proxyHeader: X-MS-AuthToken

- At least one team is set up in Teams.
- Microsoft 365 service account for the Shifts connector.</br> Create this account in Azure Active Directory (Azure AD) and assign it a Microsoft 365 license. Then, add it as a team owner to all teams that you want to map. The Shifts connector uses this account when syncing Shifts changes from Blue Yonder.

    We recommend that you create a service account specifically for this purpose and not use your user account.

### Admin role to manage the Shifts connector using PowerShell

To complete the steps in this article, you must be a Microsoft 365 global admin or a Shifts connector admin.

 The Shifts connector admin role is a custom role that you create in Azure AD and assign to a user. The name of the role must be "Shifts connector admin". The role doesn't need to have any specific permissions, although, at least one permission must be set. The service only relies on the presence of the role on the user. To learn more, see [Create and assign a custom role in Azure AD](/azure/active-directory/roles/custom-create) and [Assign Azure AD roles to users](/azure/active-directory/roles/manage-roles-portal). Keep in mind that it can take up to 24 hours for the role to be created and applied to a user.  

## Set up your environment

1. Install PowerShell version 7 or later. For step-by-step guidance, see [Installing PowerShell on Windows](/powershell/scripting/install/installing-powershell-on-windows).

1. Run PowerShell in administrator mode.
1. Install the Microsoft Graph PowerShell module.

    ```powershell
    Install-Module Microsoft.Graph
    Import-Module Microsoft.Graph
    ```

    Verify that it's version 1.6.1 or later.

    ```powershell
    Get-InstalledModule Microsoft.Graph 
    ```

1. Install the Teams Preview PowerShell module.

    ```powershell
    Install-Module -Name MicrosoftTeams -AllowPrerelease -Force
    Import-Module MicrosoftTeams 
    ```

    Verify that it's at least version 2.4.1 and contains the Shifts connector cmdlets.

    ```powershell
    Get-Command -Module MicrosoftTeams -Name *teamsshiftsconnection* 
    ```

1. Set PowerShell to exit if an error occurs when running the script.

    ```powershell
    $ErrorActionPreference = "Stop" 
    ```

1. Enable scripts to run in Windows.

    ```powershell
    Set-ExecutionPolicy bypass 
    ```

## Change connection settings

You can change connection settings such as your Blue Yonder service account and password, Blue Yonder service URLs, your Microsoft 365 service account, team mappings, and sync settings.

[Set up your environment](#set-up-your-environment) (if you haven't already), and then run this script.

## View connection health

[Set up your environment](#set-up-your-environment) (if you haven't already), and then run script.


## View connection settings

[Set up your environment](#set-up-your-environment) (if you haven't already), and then run script.

## Disable a connection

To disable a connection, [set up your environment](#set-up-your-environment) (if you haven't already), and then run script.

## Remove schedules from teams you want to map

[Set up your environment](#set-up-your-environment) (if you haven't already), and then run the following command:

```powershell
Remove-CsTeamsShiftsScheduleRecord -TeamId <Teams team ID> -DateRangeStartDate <start time> -DateRangeEndDate<end time> -ClearSchedulingGroup:$false -EntityType <the scenario entities that you want to remove, the format is @(scenario1, scenario2, ...)> -DesignatedActorId <Teams team owner ID>
```

To learn more, see Remove-CsTeamsShiftsScheduleRecord.

## Scripts

### Change connection settings

```powershell
#Update script
Write-Host "Update work flow"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
	Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 2.3
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
$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $teamsUserId -EnabledConnectorScenario $updatedConnectorScenario -EnabledWfiScenario $updatedWfiScenario -Name $UpdatedInstanceName -SyncFrequencyInMin $syncFreq -IfMatch $Etag

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

### Disable a connection

```powershell
#Oh oh! Script 
Write-Host "Oh oh! work flow"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
	Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 2.3
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

To learn more about Shifts connector cmdlets, see:

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
- Remove-CsTeamsShiftsScheduleRecord

## Related articles

- [Shifts connectors](shifts-connectors.md)
- [Manage the Shifts app](manage-the-shifts-app-for-your-organization-in-teams.md)
- [Teams PowerShell overview](../../teams-powershell-overview.md)
- [Teams PowerShell cmdlet reference](/powershell/teams/intro?view=teams-ps)