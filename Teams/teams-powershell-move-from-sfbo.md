---
title: Migrating from Skype for Business Online Connector to the Teams PowerShell module
author: pbafna03
ms.author: pbafna
ms.reviewer: pbafna
ms.date: 10/14/2020
manager: sshastri
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn how to move from Skype for Business Online Connector to the Teams PowerShell module to manage Teams.
appliesto: 
  - Microsoft Teams
---

# Migrating from Skype for Business Online Connector to the Teams PowerShell module

Teams PowerShell Module provides a complete set of cmdlets for managing Teams directly from the PowerShell command line. Administrators don't require Skype For Business Online Connector for their Teams administration.

> [!NOTE]
> Teams administrator were notified through Message center post (MC244740, dated March 16, 2021; MC250940, dated April 16 2021) about this change.

## How to Migrate

Migrating from using Skype for Business Online Connector to Teams PowerShell module is easy and simple. The below steps explain how to do this migration.

1. Install the latest Teams PowerShell module. For steps, see [Install Microsoft Teams PowerShell](teams-powershell-install.md).

2. Uninstall Skype For Business Online Connector. To uninstall, in Control Panel, go to **Programs and Features**, select **Skype for Business Online, Windows PowerShell Module**, and then select **Uninstall**.

3. In your PowerShell scripts, change the module name that's referenced in ```Import-Module``` from

    `SkypeOnlineConnector` or `LyncOnlineConnector` to `MicrosoftTeams`.

    For example, change `Import-Module -Name SkypeOnlineConnector` to `Import-Module -Name MicrosoftTeams`.

4. When using Teams PowerShell Module 2.0 or later, update your scripts that refers `New-CsOnlineSession` to `Connect-MicrosoftTeams`. `Import-PsSession` is no longer required to establish a Skype for Business Online Remote PowerShell Session.

    ```powershell
       # When using the Skype for Business online connector
         
         # Establishing a session
         Import-Module SkypeOnlineConnector [LyncOnlineConnector]
         $credential = Get-Credential
         $SkypeSession = New-CsOnlineSession -Credential $credential
         Import-Session $SkypeSession
    
         # Example getting tenant details
         Get-csTenant
         
         # Disconnecting and closing the Session 
         Get-PsSession $SkypeSession | Remove-PsSession
    
       # When using Teams PowerShell Module 2.0 or later
       
         # Establishing a session
         Import-Module MicrosoftTeams
         $credential = Get-Credential
         Connect-MicrosoftTeams -Credential $credential
       
         # Example getting tenant details
         Get-csTenant
         
         # Disconnecting and closing the Session  
         Disconnect-MicrosoftTeams
    ```

## Related topics

[Install Microsoft Teams PowerShell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](/powershell/teams/)

[Skype for Business cmdlet reference](/powershell/skype/intro)
