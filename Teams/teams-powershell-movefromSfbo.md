---
title: Install Microsoft Teams PowerShell
ms.reviewer: pupara
author: pupara
ms.author: pupara
manager: bulenteg
ms.date: 10/12/2020
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn to move from SfB Online connector to Teams module PowerShell for managing Microsoft Teams.
appliesto: 
  - Microsoft Teams
---

# How to move from Skype for  Business Online Connector to Teams PowerShell module.

This article explains the changes needed in your scripts to move from Skype for  Business Online Connector to Teams PowerShell module.

## Steps

1. Install the latest Teams PowerShell module. Please follow [Install Microsoft Teams Powershell](teams-powershell-install.md) for instructions.
2. Uninstall Skype For Business Online Connector.
    a.	Go to the control panel and remove the application “Skype for Business Online, Windows PowerShell Module” from Add or Remove programs.
3.	In PowerShell scripts change the module name referenced in the Import-Module.
    a.	SkypeOnlineConnector or LyncOnlineConnector to MicrosoftTeams.

> [!NOTE]
> Import-Module -Name SkypeOnlineConnector to Import-Module -Name MicrosoftTeams

> [!Note]
> Administrator should continue to use New-CsOnlineSession   and import session before using the Skype for Business Online cmdlets. 

## Related topics

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell Release Notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
