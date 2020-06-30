---
title: Microsoft Teams PowerShell Overview
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
description: Learn to use the PowerShell controls to manage Microsoft Teams.
appliesto: 
  - Microsoft Teams
---

# Microsoft Teams PowerShell Overview

Microsoft Teams PowerShell is a set of cmdlets for managing Teams directly from the PowerShell command line. Written in .NET Standard, Teams PowerShell works on PowerShell 5.1 on Windows,PowerShell 6.x and higher on all platforms including Azure Shell.

Before you can start using PowerShell, you'll need to [install it](teams-powershell-install.md). 

> [!WARNING]
> There are known issues with PowerShell 7 and Teams PowerShell. We recommend using PowerShell 5.1 until the issues are resolved.

## Releases


Teams PowerShell is available on [PowerShell Gallery](https://www.powershellgallery.com/packages/MicrosoftTeams) in two release types.

- **General Availability (GA)**: Production-ready cmdlets, updated monthly.

- **Public Preview**: Early access to features. May be updated more frequently than GA.

For detailed information on feature additions and improvements for both releases, read the [Teams PowerShell release notes](teams-powershell-release-notes.md).

> [!NOTE]
> For some Teams features for which there are PowerShell cmdlets, the feature itself is available only in Teams public preview. Examples include [private channel management](private-channels-life-cycle-management.md) and team templates for Education and firstline workers.

## Manage Teams with PowerShell

You'll use both of these PowerShell modules to fully manage Teams:

- [Microsoft Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/): The Teams PowerShell module contains cmdlets for managing teams, chat, and channels.

- [Skype for Business PowerShell module](https://www.microsoft.com/download/details.aspx?id=39366): The Skype for Business PowerShell module contains the cmdlets to manage meetings, phone system, and policies features.

For a complete guide to managing Teams using these modules, please see [Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md).

> [!NOTE]
> The latest [Teams PowerShell public preview release](https://www.powershellgallery.com/packages/MicrosoftTeams/) is integrated with Skype for Business Online Connector, providing a single module for Teams PowerShell management.

## Related topics

[Installing Teams PowerShell](teams-powershell-install.md)

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell Release Notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)

[Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md)
