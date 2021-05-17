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

> [!WARNING]
> Skype for Business Online Connector connections will be rejected starting May 17, 2021. Please contact Microsoft Support for help and support for migrating to Teams PowerShell Module.

## How to Migrate

Migrating from using Skype for Business Online Connector to Teams PowerShell module is easy and simple. The below steps explains how to do this.

1. Install the latest Teams PowerShell module. For steps, see [Install Microsoft Teams Powershell](teams-powershell-install.md).
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

## Online Support

Save time by starting your service request online. We'll help you find a solution or connect you to technical support.
1.	Go to the admin center at [https://admin.microsoft.com](https://admin.microsoft.com). If you get a message that says you don't have permission to access this page or perform this action, then you aren't an admin. Who has admin permissions in my business?
2.	Select the **Need help**? button.
3.	In the **Need help**? pane, tell us what you need help with, and then press Enter.
4.	If the results don't help, select **Contact support**.
5.	Enter a description of your issue, confirm your contact number and email address, select your preferred contact method, and then select **Contact me**. The expected wait time is indicated in the Need help? pane.

## Related topics

[Install Microsoft Teams Powershell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](/powershell/skype/intro?view=skype-ps)
