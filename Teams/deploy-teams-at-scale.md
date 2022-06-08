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
ROBOTS: NOINDEX, NOFOLLOW
---

# Deploy teams at scale for frontline workers in Microsoft Teams

> [!NOTE]
> This feature is currently in private preview. If you'd like to participate in the private preview, reach out to us at [dscale@microsoft.com](mailto:dscale@microsoft.com).

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

### Prepare your CSV files

You'll need to create two comma-separated values (CSV) files for each batch of teams that you deploy:

- A CSV file that defines the teams you're creating. This file must contain these required columns, in the following order, starting with the first column:

    |Column name  |Description  |
    |---------|---------|
    |Team Name    |The name of the team.        |
    |Existing Team ID     | If you're add or removing users from an existing team, specify the team ID of the team.          |
    |Visibility     |Whether the team is public (in which anyone in your organization can join) or private (in which users need approval from the team owners to join). Options are **Public** or **Private**.|
    |Team Template ID    |If you're creating a team from a template, specify the team template ID. See [Get started with team templates in the Teams admin center](get-started-with-teams-templates-in-the-admin-console.md) for a list of team template IDs.        |
 
- A CSV file that lists the users you're adding to each team.


#### Examples

Use the following examples to help you create your CSV files.

Teams.csv

```CSV
Team name, Existing team ID, Visibility, Team template ID
Contoso Store 1,,Public,com.microsoft.teams.template.retailStore
Contoso Store 2,,Public,com.microsoft.teams.template.retailStore
Contoso Store 3,,Public,com.microsoft.teams.template.retailStore
Contoso Store 4,,Public,com.microsoft.teams.template.ManageAProject
Contoso Store 5,,Public,com.microsoft.teams.template.ManageAProject
Contoso Store 6,,Public,com.microsoft.teams.template.ManageAProject
Contoso Store 7,,Public,
Contoso Store 8,,Private,com.microsoft.teams.template.OnboardEmployees
Contoso Store 9,,Private,com.microsoft.teams.template.OnboardEmployees
Contoso Store 10,,Private,com.microsoft.teams.template.OnboardEmployees
```

Users.csv

```CSV
User Full Name,User UPN or ID,Team name,ActionType,Owner or Member,License
Contoso User 001,user-001@contoso.com,Contoso Store 1,AddMember,Owner,M365F3
Contoso User 002,user-002@contoso.com,Contoso Store 2,AddMember,Owner,M365F3
Contoso User 003,user-003@contoso.com,Contoso Store 3,AddMember,Owner,M365F3
Contoso User 004,user-004@contoso.com,Contoso Store 4,AddMember,Owner,M365F3
Contoso User 005,user-005@contoso.com,Contoso Store 5,AddMember,Owner,M365F3
Contoso User 006,user-006@contoso.com,Contoso Store 6,AddMember,Member,M365F3
Contoso User 007,user-007@contoso.com,Contoso Store 7,AddMember,Member,M365F3
Contoso User 008,user-008@contoso.com,Contoso Store 8,AddMember,Member,M365F3
Contoso User 009,user-009@contoso.com,Contoso Store 9,AddMember,Member,M365F3
Contoso User 010,user-010@contoso.com,Contoso Store 10,AddMember,Member,M365F3
```

### Deploy your teams

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

    The email recipients you entered will receive an email notification about deployment status. The email contains the orchestration ID for the batch you submitted and any errors that may have occurred.

1. Run the following to check the status of the batch you submitted.

    ```powershell
    Get-CsBatchTeamsDeploymentStatus -OrchestrationId "OrchestrationId"
    ```

## Send us feedback

We value your feedback. Usability, reliability, performance&mdash;we welcome it all!

Email [dscale@microsoft.com](mailto:dscale@microsoft.com) and include your orchestration ID and error file, if you have it.

## Related articles

- [Teams PowerShell Overview](teams-powershell-overview.md)
