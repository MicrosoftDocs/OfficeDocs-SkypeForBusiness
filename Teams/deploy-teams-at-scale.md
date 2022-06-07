---
title: Deploy teams at scale for frontline workers in Microsoft Teams
author: LanaChin
ms.author: v-lanachin
ms.reviewer: rahuldey
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to deploy teams at scale for the frontline workers in your organization. 
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Deploy teams at scale for frontline workers in Microsoft Teams

> [!NOTE]
> This feature is currently in public preview.

## Overview
 
Your organization may have a lot of teams that you use to drive communication and collaboration among your frontline workforce, who are spread across different stores, locations, and roles. Currently, there isn't an easy solution to deploy, set up, and manage these teams and users at scale.

We're building a solution to enable admins to deploy and manage teams at scale.

Here's an overview of the capabilities available today for creating and managing large numbers of teams at a time and what we're planning for the near future.

||Available today |Later in 2022  |
|---------|---------|---------|
|**Number of teams you can create per batch**|Up to 100 |Up to 500|
|**Number of users you can add per team**|Up to 25|Up to 25|

Deploying teams at scale allows you to:

- Create teams using pre-built templates or your own custom templates.
- Add users to teams as owners or members.
- Manage teams at scale by adding or removing users from existing teams.
- Stay notified through email, including completion, status, and errors (if any). Team owners and members are notified.

## How to deploy teams at scale

> [!NOTE]
> Before you deploy your teams, make sure that all teams owners have a Teams license.

Follow these steps to deploy a large number of teams at a time.

You use the ```New-CsBatchTeamsDeployment``` cmdlet to submit a batch of teams to create. An orchestration ID is generated for each batch. You can then use the ```Get-CsBatchTeamsDeployment``` cmdlet to track the progress and status of each batch.

1. Install PowerShell version 7 or later. For step-by-step guidance, see [Installing PowerShell on Windows](/powershell/scripting/install/installing-powershell-on-windows).
1. Run PowerShell in administrator mode.
1. Run the following to uninstall any previously installed Teams PowerShell module.

    ```powershell
    Uninstall-module -Name MicrosoftTeams -Force -Allversions
    ```

    If you get an error message, you're already set. Go to the next step.
1. Download  and install the [latest version of the Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams).

1. Run the following to connect to Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

    When you're prompted, sign in using your admin credentials.

1. Run the following to get a list the commands in the Teams PowerShell module.

    ```powershell
    Get-Command -Module MicrosoftTeams
    ```

    Verify that ```New-CsBatchTeamsDeployment``` and ```Get-CsBatchTeamsDeployment``` are listed.

1. Run the following to deploy a batch of teams. You can enter up to five email addresses in the **UsersToNotify** parameter.

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "*Your file path*" -UsersFilePath "*Your file path*" -UsersToNotify *Email addresses* 
    ```

1. Run the following to check the status of the batch you submitted.

    ```powershell
    Get-CsBatchTeamsDeploymentStatus -OrchestrationId "OrchestrationId"
    ```

## Send us feedback

We value your feedback. Usability, reliability, performance&mdash;we welcome it all!

Email [dscale@microsoft.com](mailto:dscale@microsoft.com) and include your orchestration ID and error file, if you have it.

## Related articles

- [Teams PowerShell Overview](teams-powershell-overview.md)
