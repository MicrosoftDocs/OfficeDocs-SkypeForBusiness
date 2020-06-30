---
title: Teams PowerShell Overview
ms.reviewer: 
author: BrandonBernier
ms.author: brandber
manager: kojiko
ms.date: 06/30/2020
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn to use the PowerShell controls for managing Microsoft Teams.
appliesto: 
  - Microsoft Teams
---

# Teams PowerShell Overview

Microsoft Teams PowerShell is a set of cmdlets for managing Teams directly from the PowerShell command line. Written in .NET Standard, Teams PowerShell works on PowerShell 5.1 on Windows,PowerShell 6.x and higher on all platforms including Azure Shell.

Please see [Install Teams PowerShell](teams-powershell-install.md) for detailed instructions of the installation process.

> [!WARNING]
> There are known issues with PowerShell 7 and Teams PowerShell. It is suggested to use PowerShell 5.1 until they are resolved.

## Managing Teams with Teams PowerShell

> [!NOTE]
> The latest [Teams PowerShell public preview release](https://www.powershellgallery.com/packages/MicrosoftTeams/) is integrated with <b>Skype for Business Online Connector</b> providing a single module for Teams PowerShell management.

The following two PowerShell modules are needed to fully manage Teams.

- [Microsoft Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/): The Teams PowerShell module contains cmdlets for managing teams.
- [Skype for Business PowerShell module](https://www.microsoft.com/download/details.aspx?id=39366): The Skype for Business PowerShell module contains the cmdlets to manage meetings, phone system and policies features.

For a complete guide to managing Teams using these modules, please see [Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md).

## Releases

> [!NOTE]
> A few features such a Private Channel management and using all available Team Templates are only available in Public Preview.

Teams PowerShell is available on [PowerShell Gallery](https://www.powershellgallery.com/packages/MicrosoftTeams) in two release types.

- <b>General Availability</b>: Production-ready cmdlets updated monthly.
- <b>Public Preview</b>: Early access to features and may be updated more frequently than general availability.

Detailed information on feature additions and improvements for both releases can be found in the [Teams PowerShell release notes](teams-powershell-release-notes.md).

## Learn more

- [Installing Teams PowerShell](teams-powershell-install.md)
- [Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)
- [Teams PowerShell Release Notes](teams-powershell-release-notes.md)
- [Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)
- [Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
- [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md)
