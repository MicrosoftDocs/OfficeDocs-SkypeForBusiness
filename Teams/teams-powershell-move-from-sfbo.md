---
title: Move from Skype for Business Online Connector to the Teams PowerShell module
author: pupara
ms.author: pupara
ms.reviewer: pupara
manager: bulenteg
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn how to move from Skype for Business Online Connector to the Teams PowerShell module to manage Teams.
appliesto: 
  - Microsoft Teams
---

# Move from Skype for Business Online Connector to the Teams PowerShell module

To move from using Skype for Business Online Connector to the Teams PowerShell module to manage Teams, you'll need to update your existing PowerShell scripts. This article explains how to do this.

1. Install the latest Teams PowerShell module. For steps, see [Install Microsoft Teams Powershell](teams-powershell-install.md).
2. Uninstall Skype For Business Online Connector. To do this, in Control Panel, go **Programs and Features**, select **Skype for Business Online, Windows PowerShell Module**, and then select **Uninstall**. 
3. In your PowerShell scripts, change the module name that's referenced in ```Import-Module``` from 
```SkypeOnlineConnector``` or ```LyncOnlineConnector``` to ```MicrosoftTeams```.

    For example, change ```Import-Module -Name SkypeOnlineConnector``` to ```Import-Module -Name MicrosoftTeams```.
4. When using Teams PowerShell Module 2.0 or later, change New-csOnlineSession to Connect-MicrosoftTeams. 

```powershell
  # When using Teams PowerShell Module 1.1.6
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $credential
   Import-PSSession $sfbSession
   
   # When using Teams PowerShell Module 2.0 or later
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
```

## Related topics

[Install Microsoft Teams Powershell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
