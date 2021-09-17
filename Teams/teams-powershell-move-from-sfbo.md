---
title: Migrating from Skype for Business Online Connector to the Teams PowerShell module
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

# Migrating from Skype for Business Online Connector to the Teams PowerShell module

Teams PowerShell Module provides a complete set of cmdlets for managing Teams directly from the PowerShell command line. Administrators do not require Skype For Business Online Connector for their Teams administration.

> [!NOTE]
> Teams administrator were notified through Message center post (MC244740, dated March 16, 2021; MC250940, dated April 16 2021) about this change.
>
> Teams PowerShell Module uses modern authentication, but the underlying Windows Remote Management (WinRM) client must be configured to allow Basic authentication. See [Download and install Windows PowerShell](/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-windows-powershell-5-1) for instructions on how to enable WinRM for Basic authentication.

## How to Migrate

Migrating from using Skype for Business Online Connector to Teams PowerShell module is easy and simple. The below steps explains how to do this.

1. Install the latest Teams PowerShell module. For steps, see [Install Microsoft Teams PowerShell](teams-powershell-install.md).

2. Uninstall Skype For Business Online Connector. To do this, in Control Panel, go to **Programs and Features**, select **Skype for Business Online, Windows PowerShell Module**, and then select **Uninstall**.

3. In your PowerShell scripts, change the module name that's referenced in ```Import-Module``` from

    `SkypeOnlineConnector` or `LyncOnlineConnector` to `MicrosoftTeams`.

    For example, change `Import-Module -Name SkypeOnlineConnector` to `Import-Module -Name MicrosoftTeams`.

4. When using Teams PowerShell Module 2.0 or later, update your scripts that refers `New-CsOnlineSession` to `Connect-MicrosoftTeams`. `Import-PsSession` is no longer required to establish a Skype for Business Online Remote PowerShell Session as that is done implicit when using `Connect-MicrosoftTeams`.

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

[Microsoft Teams cmdlet reference](/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](/powershell/skype/intro?view=skype-ps)
