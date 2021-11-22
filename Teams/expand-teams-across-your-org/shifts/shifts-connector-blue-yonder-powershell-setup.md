---
title: Use PowerShell to connect Shifts to your Blue Yonder workforce management system
author: LanaChin
ms.author: v-lanachin
ms.reviewer: 
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Integrate Shifts with your Blue Yonder workforce management system using PowerShell.
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Use PowerShell to connect Shifts to your Blue Yonder workforce management system

## Overview

The Shifts to Blue Yonder connector makes it easy to integrate the Shifts app in Microsoft Teams with your Blue Yonder workforce management (WFM) system. After the connection is set up, your frontline workers can seamlessly view and manage their schedules in Blue Yonder from within Shifts.

In this article, we walk you through how to use PowerShell to set up and configure the connector to integrate Shifts with Blue Yonder.

To set up the connection, you run a PowerShell script. The script configures the connector, applies sync settings, creates the connection, and maps Blue Yonder sites to teams. Sync settings determine the features enabled in Shifts and the schedule information that's synced between Blue Yonder and Shifts. Mappings define the relationship between your Blue Yonder sites and teams in Teams. You can map to existing teams and new teams.

We provide two scripts. You can use either script, depending on whether you want to map to existing teams or create new teams to map to.

You can set up multiple connections, each with different sync settings. For example, if your organization has multiple locations with different schedule requirements, create a connection with unique sync settings for each location. Keep in mind that a Blue Yonder site can only be mapped to one team at any given time. If a site is already mapped to a team, it can't be mapped to another team.

With Blue Yonder as the system of record, your frontline workers can see and swap shifts, manage their availability, and request time off in Shifts on their devices. Frontline managers can continue to use Blue Yonder or use Shifts to set up schedules.

> [!NOTE]
> You can also use the Shifts connector wizard in the Microsoft 365 admin center to connect Shifts to Blue Yonder. To learn more, see [Use the Shifts connector wizard to connect your workforce management system](shifts-connector-wizard.md).

## Before you begin

### Prerequisites

Before you get started, make sure you have the following prerequisites:

- Blue Yonder version 2020.3, 2021.1, or 2021.2. </br>If you have 2020.3 or 2021.1, we recommend applying the 2020.3.0.4 or 2021.1.0.3 patch. The patch has a fix required for users to update their availability in Shifts.
- Blue Yonder service account name and password and service URLs. </br>If you don’t have this information, contact your Blue Yonder delivery partner or technical account manager. The account is created at the root enterprise level by a Blue Yonder enterprise administrator and must have APIAccess, Client Admin, and Store Manager access. The account and password are required to create a connection.
- Federated SSO authentication is enabled in your Blue Yonder environment. Contact your Blue Yonder delivery partner or technical account manager to make sure federated SSO is enabled. They'll need the following information:

    - federatedSSOValidationService: `https://amer.wfmconnector.teams.microsoft.com/api/v1/fedauth/{tenantId}/6A51B888-FF44-4FEA-82E1-839401E9CD74/authorize` where {tenantId} is your tenantId
     - proxyHeader: X-MS-AuthToken

- At least one team is set up in Teams.
- Microsoft 365 service account for the Shifts connector.</br> Create this account in Azure Active Directory (Azure AD) and assign it a Microsoft 365 license. Then, add it as a team owner to all teams that you want to map. The Shifts connector uses this account when syncing Shifts changes from Blue Yonder.

    We recommend that you create a service account specifically for this purpose and not use your user account.

Additionally, to complete the steps in this article, you must be:

- A Microsoft 365 global admin
- A Shifts connector admin

 The Shifts connector admin role is a custom role that you create in Azure AD and assign to a user account. The custom role must be named "Shifts connector admin". The role doesn't need to have any specific permissions, although, at least one permission must be set. The service only relies on the presence of the role on the user. To learn more, see [Create and assign a custom role in Azure AD](/azure/active-directory/roles/custom-create) and [Assign Azure AD roles to users](/azure/active-directory/roles/manage-roles-portal). Keep in mind that it can take up to 24 hours for the role to be created and applied to a user.  

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

## Identify the teams you want to map

> [!NOTE]
> Complete this step if you're mapping Blue Yonder sites to existing teams. If you're creating new teams to map to, you can skip this step.

Get a list of the TeamIds of teams in your organization.

```powershell
Get-Team
 ```

Take note of the TeamIds of the teams you want to map. The script will prompt you to enter this information.

> [!NOTE]
> If one or more teams have an existing schedule, the script will remove the schedules from those teams. Otherwise, you'll see duplicate schedules in the team.

## Run the script

Run the script:

- To set up a connection and create new teams to map, [run this script](#set-up-a-connection-and-create-new-teams).
- To set up a connection and map to existing teams, [run this script](#set-up-a-connection-and-map-to-existing-teams).

The script does the following actions. You'll be prompted to enter setup and configuration details.

1. Tests and verifies the connection to Blue Yonder using the Blue Yonder service account credentials and service URLs that you enter.
1. Configures the Shifts connector.
1. Applies sync settings. These settings include the sync frequency (in minutes) and the schedule data that's synced between Blue Yonder and Shifts. Schedule data is defined in the following parameters:

    - The **enabledConnectorScenarios** parameter defines data that's synced from Blue Yonder to Shifts. Options are `Shift`, `SwapRequest`, `UserShiftPreferences`, `OpenShift`, `OpenShiftRequest`, `TimeOff`, `TimeOffRequest`.
    - The **enabledWfiScenarios** parameter defines data that's synced from Shifts to Blue Yonder. Options are `SwapRequest`, `OpenShiftRequest`,  `TimeOffRequest`, `UserShiftPreferences`.

    > [!IMPORTANT]
    > The script enables sync for all these options. If you want to change these settings, you can do so after the connection is set up. To learn more, see [Link to PowerShell config doc]().

1. Creates the connection.
1. Maps Blue Yonder sites to teams. Mappings are based on the Blue Yonder site IDs and team IDs that you enter or new teams you create, depending on the script that you run. If a team has an existing schedule, the script removes the schedule.

A Success message on the screen indicates that your connection is successfully set up.

## If you need to make changes to a connection

To make changes to a connection after it's set up, see [Link to PowerShell article](). For example, you can update sync settings, team mappings, or disable a connection.

## Scripts

### Set up a connection and create new teams

```powershell
#Onboarding script
Write-Host "Onboarding Shifts Connector work flow"
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
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password 
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName 
if ($testResult.Code -ne $NULL) {
	write $testResult
	throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create an instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency"
$InstanceResponse = New-CsTeamsShiftsConnectionInstance -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -DesignatedActorId $teamsUserId -EnabledConnectorScenario $enabledConnectorScenario -EnabledWfiScenario $wfiSupportedScenario -SyncFrequencyInMin $syncFreq
$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
	Write-Host "Suceess"
} else {
	throw "Connector instance creation failed"
}

#Retrieve the list of sites
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if ($WfmTeamIds -ne $NULL && $WfmTeamIds.Count -gt 0){
	[System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
	throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles 
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while (true)
{

#Create a new Teams team with owner set to system account and name set to the site name
Write-Host "Creating a Teams team"
$teamsTeamName = Read-Host -Prompt "Input the Teams team name"
$Team = New-Team -DisplayName $teamsTeamName -Visibility "Public" -Owner $teamsUserId
Write-Host "Success"
$TeamsTeamId=$Team.GroupId

#add users to the Team for Shifts
Write-Host "Adding users to Teams team"
$currentUser = Read-Host -Prompt "Input the current user's user name or ID"
Add-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
$failedWfmUsers=@()
foreach ($user in $WFMUsers) {
	try {
	$userEmail = $user.Name + "@" +$domain
	Add-TeamUser -GroupId $TeamsTeamId -User $userEmail
	} catch {
		$failedWfmUsers+=$user
	}
}
if($failedWfmUsers.Count -gt 0){
	Write-Host "There are WFM users not existed in Teams tenant:"
	write $failedWfmUsers
}

#Enable sheduling in the group
$RequestBody = @{
    Enabled = $true
    TimeZone = "America/Los_Angeles"
}
$teamUpdateUrl="https://graph.microsoft.com/v1.0/teams/"+$TeamsTeamId+"/schedule"
$Schedule = Invoke-MgGraphRequest -Uri $teamUpdateUrl -Method PUT -Body $RequestBody

#Create a mapping of the new team to the site 
Write-Host "Create a mapping of the new team to the site"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone "America/Los_Angeles" -WfmTeamId $WfmTeamId
Write-Host "Success"

$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
Remove-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
Disconnect-MgGraph
Disconnect-MicrosoftTeams
```
### Set up a connection and map to existing teams

```powershell
#Onboarding script
Write-Host "Onboarding Shifts Connector work flow"
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
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password 
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName 
if ($testResult.Code -ne $NULL) {
	write $testResult
	throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create an instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency"
$InstanceResponse = New-CsTeamsShiftsConnectionInstance -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -DesignatedActorId $teamsUserId -EnabledConnectorScenario $enabledConnectorScenario -EnabledWfiScenario $wfiSupportedScenario -SyncFrequencyInMin $syncFreq
$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
	Write-Host "Suceess"
} else {
	throw "Connector instance creation failed"
}

#Retrieve the list of sites
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if ($WfmTeamIds -ne $NULL && $WfmTeamIds.Count -gt 0){
	[System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
	throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles 
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while (true)
{

$TeamsTeamId = Read-Host -Prompt "Input the ID of the Teams team to be mapped"
#Clear schedule of the Teams team
Write-Host "Clear schedule of the existing team"
$startTime = Read-Host -Prompt "Input the start time of clear schedule"
$endTime = Read-Host -Prompt "Input the end time of clear schedule"

$entityTypeString = Read-Host -Prompt 'Input the entity types of clear schedule'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$entityType = $entityTypeString -Split {$Delimiters -contains $_}
$entityType = $entityType.Trim()
$entityType = $entityType.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
Remove-CsTeamsShiftsScheduleRecord -TeamId $TeamsTeamId -DateRangeStartDate $startTime -DateRangeEndDate $endTime -ClearSchedulingGroup:$True -EntityType $entityType -DesignatedActorId $$teamsUserId

#Create a mapping of the new team to the site 
Write-Host "Create a mapping of the existing team to the site"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone "America/Los_Angeles" -WfmTeamId $WfmTeamId
Write-Host "Success"


$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
Disconnect-MgGraph
Disconnect-MicrosoftTeams
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

## Related articles

- [Shifts connectors](shifts-connectors.md)
- [Manage the Shifts app](manage-the-shifts-app-for-your-organization-in-teams.md)
- [Teams PowerShell overview](../../teams-powershell-overview.md)
- [Teams PowerShell cmdlet reference](/powershell/teams/intro?view=teams-ps)