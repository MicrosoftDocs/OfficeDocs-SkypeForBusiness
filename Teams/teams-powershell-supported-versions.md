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

Microsoft Teams PowerShell Module (TPM) versions in the 4.x.x series will be the only versions supported going forward. All earlier versions are on the retirement path.



## New organizations

Organizations newly onboarding to Teams will only be able to use Teams PowerShell Module 4.0.0 or above starting from April 1, 2022.



## Current organizations (non TPM active)

Organizations who haven't used TPM in the last three months (Jan’22 – Mar’22), will only be able to use TPM 4.0.0 or above starting from April 1, 2022.



## Current organizations (TPM active)

Organizations who have been using TPM in the last three months (Jan’22 – Mar’22) will only be able to use TPM 4.0.0 or above starting from June 15, 2022.

This means that the Administrators will not be able to use Teams PowerShell Module versions released before 4.0.0. Instead, it's recommended to update Teams PowerShell Module to the latest version.


## Important notes

- Release notes for all the Teams PowerShell Module versions can be found at [Teams PowerShell release notes](teams-powershell-release-notes.md).

- To update any PowerShell module, you should use the same method used to install the module. For example, if you originally used Install-Module, then you should use [Update-Module](/powershell/module/powershellget/update-module) to get the latest version.  

  ```powershell
  Update-Module MicrosoftTeams
  ```

-	If updating from Teams PowerShell Module version 1.1.6, update your scripts to use `Connect-MicrosoftTeams` instead of `New-CsOnlineSession`.

-	During the update, it’s suggested to not use TPM 4.x.x/3.x.x alongside versions older than 3.0.0. For example, using versions 4.0.0 & 2.6.0 together for different admin operations in the same organization isn’t recommended. 

- Related changes
  * Updates to Get-CsOnlineUser & Get-CsOnlineVoiceUser in TPM 3.0.0 and above – more details in [Get-CsOnlineUser](/powershell/module/skype/get-csonlineuser) & [Get-CsOnlineVoiceUser](/powershell/module/skype/get-csonlinevoiceuser) (Message center post – MC340774).

  * Changes coming to Phone number assignment - more details in [Set-CsUser](/powershell/module/skype/set-csuser), [Set-CsOnlineVoiceUser](/powershell/module/skype/set-csonlinevoiceuser), [Set-CsOnlineApplicationInstance](/powershell/module/skype/set-csonlineapplicationinstance) & [Set-CsOnlineVoiceApplicationInstance](/powershell/module/skype/set-csonlinevoiceapplicationinstance) (Message center post – MC316139)



## Related topics

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Install Microsoft Teams PowerShell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](/powershell/module/teams) 

[Skype for Business cmdlet reference](/powershell/module/skype) 
