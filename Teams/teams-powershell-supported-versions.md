---
title: Teams PowerShell Module - Supported Versions
author: pbafna
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

Teams PowerShell Module – versions older than 3.0.0 to be retired!



## Current organizations

Starting 1st Apr’22, we will be retiring all Teams PowerShell Module versions older than 3.0.0.  This means that the Administrators will not be able to use Teams PowerShell Module versions released prior to 3.0.0. 

Instead, we recommend updating Teams PowerShell Module to version 3.0.0 or above.

Important notes:
- Release notes for all the Teams PowerShell Module versions can be found at [Teams PowerShell release notes](teams-powershell-release-notes.md).

- To update any PowerShell module, you should use the same method used to install the module. For example, if you originally used Install-Module, then you should use [Update-Module](/powershell/module/powershellget/update-module) to get the latest version.  

  ```powershell
  Update-Module MicrosoftTeams
  ```

-	If updating from Teams PowerShell Module version 1.1.6 - update your scripts to use `Connect-MicrosoftTeams` instead of `New-CsOnlineSession`.



## New organizations

Organizations newly onboarding to Teams will only be able to use Teams PowerShell Module 3.0.0 or above starting from 15th Feb’22.



## Related topics

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Install Microsoft Teams PowerShell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](/powershell/skype/intro?view=skype-ps)
