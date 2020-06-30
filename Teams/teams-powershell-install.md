---
title: Install Microsoft Teams PowerShell
ms.reviewer: brandber
author: BrandonBernier
ms.author: brandber
manager: kojiko
ms.date: 06/30/2020
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn to use the PowerShell controls for managing Microsoft Teams.
appliesto: 
  - Microsoft Teams
---

## Install Teams PowerShell

This article explains how to install the Teams PowerShell module using
[PowerShellGet](/powershell/scripting/gallery/installing-psget). These instructions work on [Azure Cloud Shell](/azure/cloud-shell/overview), Linux, macOS and Windows platforms.

## Requirements

Teams PowerShell works with PowerShell 6.2.4 and later on all platforms. It is also supported with
PowerShell 5.1 on Windows. Install the
[latest version of PowerShell](/powershell/scripting/install/installing-powershell) available for
your operating system. Teams PowerShell has no additional requirements when run on PowerShell 6.2.4
and later.

> [!WARNING]
> There are known issues with PowerShell 7 and Teams PowerShell. For the best experience, use PowerShell 5.1.

## Install the Teams PowerShell module

> [!NOTE]
> For the best experience, you should be using either GA or Public Preview modules. They are not intended to be co-exist together.

> [!NOTE]
> If you are using the Public Preview version of Teams PowerShell. It is strongly recommended that you uninstall Skype for Business Online Connector prior.

Using the PowerShellGet cmdlets is the preferred installation method. By default, the PowerShell gallery isn't configured as a trusted repository for PowerShellGet. The first time you use the PSGallery you see the following prompt:

```output
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Answer `Yes` or `Yes to All` to continue with the installation.

Installing the module for all users on a system requires elevated privileges. Start the PowerShell
session using **Run as administrator** in Windows or use the `sudo` command on macOS or Linux:

```powershell
Install-Module MicrosoftTeams
```

## Install Teams PowerShell Public Preview

Below will guide you through installing the latest public preview of the Teams PowerShell module.



Installing the module for all users on a system requires elevated privileges. Start the PowerShell
session using **Run as administrator** in Windows or use the `sudo` command on macOS or Linux:

If you are using PowerShell 5.1, it is required that th ePowerShellGet module is updated prior. After updating the PowerShellGet, close and reopen an elevated PowerShell session to ensure the latest PowerShellGet is loaded.

```powershell
Install-Module PowerShellGet -Force -AllowClobber
```

To install Teams Powershell public preview, run the PowerShell command below.

```powershell
Install-Module MicrosoftTeams 
```

## Install the Skype for Business Online Connector

> [!WARNING]
> Skype for Business Online Connector is currently part of Teams PowerShell public preview. Once this feature is included in the GA release of Teams PowerShell, Skype for Business Online Connector will no longer be available.

Download and install the [Skype for Business PowerShell module](https://www.microsoft.com/download/details.aspx?id=39366), then run the following in PowerShell.

```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

## Sign in

To start working with Teams PowerShell, sign in with your Azure credentials.

> [!NOTE]
> If you are using the latest [Teams PowerShell public preview release](https://www.powershellgallery.com/packages/MicrosoftTeams/), it is not required to install the Skype for Business Online Connector.

```powershell
$credential = Get-Credentials

#Connect to Microsoft Teams
Connect-MicrosoftTeams -Credentials $credential

#Connection to Skype for Business Online and import into Ps session
$session = New-CsOnlineSession -Credentials $credential
Import-PsSession $session
```

## Update Teams PowerShell

> [!WARNING]
> If Teams PowerShell has already been imported into your PowerShell session, updating the module will fail.

To update Teams PowerShell, open a new elevated PowerShell command prompt and run the following.

```powershell
Update-Module MicrosoftTeams
```

## Uninstall Teams PowerShell

> [!WARNING]
> If Teams PowerShell has already been imported into your PowerShell session, uninstalling the module will fail.

To uninstall Teams PowerShell, open a new elevated PowerShell command prompt and run the following.

```powershell
Uninstall-Module MicrosoftTeams
```

## Next Steps

Now you're ready to manage Teams using Teams PowerShell. See [Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md) to get started.

## Learn more

- [Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)
- [Teams PowerShell Release Notes](teams-powershell-release-notes.md)
- [Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)
- [Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
