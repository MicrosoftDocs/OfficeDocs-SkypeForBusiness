---
title: Create people manager teams in Microsoft Teams
ms.reviewer: pbethi
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
description: Learn how to use a PowerShell script to create a team for each manager with their directs as team members. 
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Create people manager teams in Microsoft Teams


When you roll out Microsoft Teams, rather than launching with a "blank slate" (no teams or channels), we strongly recommend that you set up a base framework of teams and channels. This helps to prevent "team sprawl," where users create numerous teams when they should be creating channels in existing teams. To help you get started with a well-designed teams and channels structure, we've created a PowerShell script that creates a team for each of your first and second line people managers, with each manager's direct reports as team members. This is a "point-in-time" script (it doesn't update your teams or channels automatically when people are added or removed from an organization). But it's a valuable tool you can use to impose some order on your Teams structure from the start. This script reads your Azure AD, gets a list of managers and their direct reports. It uses this list to create one team per people manager. 

## How to use the PowerShell script 

Start by running the [Export managers and their directs script](scripts/powershell-script-create-teams-from-managers-export-managers.md) (which assumes you've already run the [Connect-AzureAd](/powershell/module/azuread/connect-azuread?view=azureadps-2.0) and [Connect-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams?view=teams-ps) PowerShell modules). The *Export managers and their directs* script creates a tab-delimited file (ExportedManagerDirects.txt) that lists all managers with their direct reports. 

Then, run the [Create new people manager teams script](scripts/powershell-script-create-teams-from-managers-new-teams.md). This script reads in the ExportedManagerDirects.txt file and creates a team for each manager, with that manager's direct reports as members. If any manager or direct isn't enabled for Teams, the script skips them and doesn't create a team. (Review the report, then rerun the script after you've turned on Teams for anybody who needs it. The script won't create a second team for any manager it's already created a team for.)

For each team, the script creates a General and "Just for fun" channel. 

## Best practices

- Ask each people manager to add your organization's crisis communications website as a tab to the General channel for each team. 

- Check out the new Crisis Communications app by reading this March 8, 2020 blog post: [Coordinate crisis communications using Microsoft Teams + Power Platform](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/coordinate-crisis-communications-using-microsoft-teams-power/ba-p/1216715).

## Related topics

[Best practices for organizing teams](best-practices-organizing.md)

[Create an org-wide team in Teams](create-an-org-wide-team.md)