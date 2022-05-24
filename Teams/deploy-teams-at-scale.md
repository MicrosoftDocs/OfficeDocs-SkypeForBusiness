---
title: Deploy teams at scale in Microsoft Teams
author: LanaChin
ms.author: v-lanachin
ms.reviewer: rahuldey
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to deploy teams at scale using PowerShell. 
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
ROBOTS: NOINDEX, NOFOLLOW
---

# Deploy teams at scale in Microsoft Teams

> [!NOTE]
> This feature is in private preview.

## Overview
 
We're aware some of our customers have a lot of teams that they use to drive communication and collaboration among their team members who are spread across different stores, locations, and roles. There currently isn't an easy solution to deploy, set up, and manage these teams and users at scale.

We're building a solution to allow admins to deploy and manage teams at scale.  

Here's an overview of what's available today for creating teams, what's coming soon, and what we're planning in the near future.

|Available today  |Available soon  |In the future  |
|---------|---------|---------|
| <ul><li>Create up to 30 teams per upload using pre-built templates or your own custom templates.</li><li>Add up to 20 users per team as owners or members.</li><li>Manage teams at scale by adding or removing users from existing teams.</li><li>Stay notified with emails. This includes job completion, job status, and errors if any. Team owners and members are notified.</li></ul>|<ul><li>Create up to 100 teams per upload.</li><li>Add up to 25 users per team as owners or members. </li></ul>|<ul><li>Create up to 500 teams per upload.</li></ul>|

## Deploy teams at scale using PowerShell

Here's how to deploy teams at scale. You can create up to XYZ of teams at a time.

You use the ```New-CsBatchTeamsDeployment``` cmdlet to submit a batch of teams. An orchestration ID is generated for each batch. You can then use the ```Get-CsBatchTeamsDeployment``` cmdlet to track the progress and status of the teams created in each batch.

1. Install PowerShell version 7 or later. For step-by-step guidance, see [Installing PowerShell on Windows](/powershell/scripting/install/installing-powershell-on-windows).
1. Run PowerShell in administrator mode.
1. Run the following to uninstall any previously installed Teams PowerShell module.

    ```powershell
    Uninstall-module -Name MicrosoftTeams -Force -Allversions
    ```

    If you get an error message, you're already set. Go to the next step.
1. Download the [latest version of the Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/4.3.1-preview), and then run the following to install it:

    ```powershell
    Install-Module -Name MicrosoftTeams –AllowPrerelease 
    ```

1. Run the following to connect to Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

When you're prompted, sign in using your admin credentials.

1. Run the following to list the commands in the Teams PowerShell module

    ```powershell
    Get-Command -Module MicrosoftTeams
    ```

Verify that ```New-CsBatchTeamsDeployment``` and ```Get-CsBatchTeamsDeployment``` are listed.

1. Run the following to deploy a batch of teams:

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "*Your file path*" -UsersFilePath "*Your file path*" -UsersToNotify *Email address* 
    ```

1. Run the following to check the status of the batch you submitted.

    ```powershell
    Get-CsBatchTeamsDeploymentStatus -OrchestrationId "OrchestrationId"
    ```

## Send us your feedback

Let us know if you have feedback. Usability, reliability, performance - we welcome it all.

Email [rahuldey@microsoft.com](mailto:rahuldey@microsoft.com) and include your orchestration ID and error file, if you've it.

## Related articles

- [Teams PowerShell Overview](teams-powershell-overview.md)
