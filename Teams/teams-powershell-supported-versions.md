---
title: Teams PowerShell Module - Supported Versions
author: pbafna03
ms.author: pbafna
ms.reviewer: pbafna
manager: sshastri
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn about versions supported of the Teams PowerShell Module, used for administration of Microsoft Teams.
appliesto: 
  - Microsoft Teams
---

# Teams PowerShell Module - Supported Versions

Microsoft Teams PowerShell Module versions in the 4.x.x series will be the only versions supported going forward. All earlier versions are on the retirement path.



## New organizations

Organizations newly onboarding to Teams will only be able to use Teams PowerShell Module 4.0.0 or above starting from April 1, 2022.



## Current organizations (non TPM active)

Organizations who have not used older TPM versions (< 4.0.0) in the last 3 months (Jan’22 – Mar’22), will only be able to use TPM 4.0.0 or above starting from April 1, 2022.



## Current organizations (TPM active)

Organizations who have been actively using older TPM versions (<4.0.0) in the last 3 months (Jan’22 – Mar’22) will have more time to update to TPM 4.x.x. More details to follow soon. 



## Important notes

- Release notes for all the Teams PowerShell Module versions can be found at [Teams PowerShell release notes](teams-powershell-release-notes.md).

- To update any PowerShell module, you should use the same method used to install the module. For example, if you originally used Install-Module, then you should use [Update-Module](/powershell/module/powershellget/update-module) to get the latest version.  

  ```powershell
  Update-Module MicrosoftTeams
  ```

-	If updating from Teams PowerShell Module version 1.1.6 - update your scripts to use `Connect-MicrosoftTeams` instead of `New-CsOnlineSession`.



## Related topics

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Install Microsoft Teams PowerShell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](/powershell/module/teams) 

[Skype for Business cmdlet reference](/powershell/module/skype) 
