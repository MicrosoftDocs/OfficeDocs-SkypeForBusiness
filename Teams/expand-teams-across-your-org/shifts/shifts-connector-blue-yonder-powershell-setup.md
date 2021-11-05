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

## Overview


1. Tests your connection settings
1. Configures the Shifts connector for Blue Yonder, applies sync settings, and creates the connection.
1. Maps Blue Yonder sites to teams

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

## Run the Shifts connector script to create the connection

The script tests your connection settings, configures the Shifts connector, applies sync settings, creates the connection, and maps Blue Yonder sites to teams.





## Related topics

- [Manage the Shifts app for your organization in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
- [Teams PowerShell overview](../../teams-powershell-overview.md)