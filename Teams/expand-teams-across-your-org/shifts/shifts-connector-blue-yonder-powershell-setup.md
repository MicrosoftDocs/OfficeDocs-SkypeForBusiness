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

You must be a Microsoft 365 global admin or Shifts connector admin. Before you get started, make sure you have the following prerequisites:

- You have Blue Yonder version 2020.3 or 2021.
- Federated SSO authentication is enabled in your Blue Yonder environment.
- At least one team is set up in Teams.

You'll also need to know your Blue Yonder service account name and password and service URLs. If you don’t have this information, contact your Blue Yonder delivery partner or technical account manager.

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

You'll need to know the team IDs of the teams you want to map. Run the following command to retrieve a list of team IDs of teams in your organization.

Take note of the team IDs you want to map. The script will prompt you to enter this information.

> [!NOTE]
> If one or more teams have an existing schedule, the script will remove the schedules from those teams. Otherwise, you'll see duplicate schedules in the team.

## Run the script

Run the script:

- To set up a connection and create new teams to map, [download and run this script]().
- To set up a connection and map to existing teams, [download and run this script]().

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