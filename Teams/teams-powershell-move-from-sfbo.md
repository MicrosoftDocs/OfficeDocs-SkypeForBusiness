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

To move from using Skype for Business Online Connector to the Teams PowerShell module to manage Teams, you'll need to update existing PowerShell scripts. This article explains how to do this. Note that by using Teams PowerShell module you can manage both Skype for Business Online and Teams users.

1. Install the latest Teams PowerShell module. For steps, see [Install Microsoft Teams Powershell](teams-powershell-install.md).
2. Uninstall Skype For Business Online Connector. To do this, in Control Panel, go to **Programs and Features**, select **Skype for Business Online, Windows PowerShell Module**, and then select **Uninstall**.
3. 
   | Original                              | Change To                     | Additional Comments                                             |
   |-------------------------------------- |-------------------------------|-----------------------------------------------------------------|
   | Import-Module SkypeOnlineConnector    | Import-Module MicrosoftTeams  |                                                                 |
   | Import-Module LyncOnlineConnector     | Import-Module MicrosoftTeams  |                                                                 |
   | $session = New-CsOnlineSession <br> Import-PsSession -Session $session    | Connect-MicrosoftTeams        | using New-CsOnlineSession and importing session is optional at this time and will be deprecated in the future                  |
   | Enable-CsOnlinesessionForReconnection | -Remove it-                   | Reconnections are now made automatically and this cmdlet is no longer needed, thus it is removed from the module.  |

## Related topics

[Install Microsoft Teams Powershell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
