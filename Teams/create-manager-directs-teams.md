---
title: Create teams for managers and their directs
ms.reviewer: pbethi
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
description: Learn about best practices for organizing teams in Microsoft Teams to meet your organization's needs.
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

Create teams for managers and their directs
======================================================

When you roll out Teams, rather than launching with a "blank slate" (no teams or channels), we strongly recommend that you set up a base framework of teams and channels. This helps to prevent "team sprawl," where users create numerous teams when they should be creating channels in existing teams. To help you get started with a well-designed teams and channels structure, we've created a PowerShell script that creates a team for each of your 1st and 2nd line people managers, with each manager's direct reports as team members. This is a "point-in-time" script (it doesn't update your teams or channels automatically when people are added or removed from an organization). But it's a valuable tool you can use to impose some order on your Teams structure from the start. This script reads your Azure AD, gets a list of managers and their direct reports. It uses this list to create one team per people manager. 

## How to use the PowerShell script 

Start by running the ExportManagers script (which assumes you've already run the Connect-AzureAd and Connect-MicrosoftTeams PowerShell modules). ExportManagers creates a tab-delimited file (ExportedManagerDirects.txt) that lists all managers with their direct reports. 

**LOLA GET SCREEN CAP OF A SAMPLE LIST**

Then, run New-TeamsFromManagers. This script reads in the ExportedManagerDirects.txt file and creates a team for each manager, with that manager's direct reports as members. If any manager or direct isn't enabled for Teams, the script skips them and doesn't create a team. (Review the report, then rerun the script after you've turned on Teams for anybody who needs it. The script won't create a 2nd team for any manager it's already created a team for.)

For each team, the script creates a General and "Just for fun" channel. 

## Related topics

[Best practices for organizing teams](best-practices-organizing.md)

[Create an org-wide team in Teams](create-an-org-wide-team.md)
