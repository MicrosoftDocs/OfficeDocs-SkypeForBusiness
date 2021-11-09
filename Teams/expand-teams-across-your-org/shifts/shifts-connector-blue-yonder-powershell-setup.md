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
ms.localizationpriority: high
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Use PowerShell to connect Shifts to your Blue Yonder workforce management system

The script tests and verifies the connection to Blue Yonder, configures the Shifts connector, applies sync settings, creates the connection, and maps Blue Yonder sites to teams.

## Before you begin

You must be a Microsoft 365 global admin. Before you get started, make sure you meet the following prerequisites:

- Blue Yonder version 2020.3 and 2021
- At least one team set up in Teams
- Licenses?

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

1. Set Powershell to exit if an error occurs when running the script.

    ```powershell
    $ErrorActionPreference = "Stop" 
    ```

1. Enable scripts to run in Windows.

    ```powershell
    Set-ExecutionPolicy bypass 
    ```

## Remove existing Shifts schedules in teams

## Run the Shifts connector to Blue Yonder script

Run the Shifts connector script to connect Shifts to Blue Yonder. The script does the following:

1. Tests and verifies the connection using the Blue Yonder connection details that you enter.
1. Configures the Shifts connector, applies sync settings that you specify, and creates the connection.
1. Maps Blue Yonder sites to teams that you specify.

We have two scripts that you can use, depending on whether you want to create a new team in Teams when the connection is created.



## Related topics

- [Manage the Shifts app for your organization in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
- [Teams PowerShell overview](../../teams-powershell-overview.md)