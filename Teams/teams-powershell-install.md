---
title: Install Microsoft Teams PowerShell
ms.reviewer: brandber
author: brandber
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

# Install Microsoft Teams PowerShell

This article explains how to install the Microsoft Teams PowerShell module using
[PowerShellGet](/powershell/scripting/gallery/installing-psget). These instructions work on [Azure Cloud Shell](/azure/cloud-shell/overview), Linux, macOS, and Windows platforms.

## Requirements

Teams PowerShell requires PowerShell 5.1 or higher on all platforms. Install the [latest version of PowerShell](/powershell/scripting/install/installing-powershell) available for your operating system.

> [!WARNING]
> There are known issues with PowerShell 7 and Teams PowerShell. For the best experience, we recommend that you use PowerShell 5.1.

## Install the Teams PowerShell module

> [!NOTE]
> For the best experience, use either General Availability (GA) or Public Preview modules - not both. They're not intended to work together.


Use the **PowerShellGet** cmdlets to install the Teams PowerShell module. Installing the module for all users on a system requires elevated privileges. Start the PowerShell
session using **Run as administrator** in Windows or use the `sudo` command on macOS or Linux:

```powershell
Install-Module MicrosoftTeams
```

By default, the PowerShell Gallery (PSGallery) isn't configured as a trusted repository for **PowerShellGet**. The first time you use the PSGallery, you'll see the following message:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Answer **Yes** or **Yes to All** to continue with the installation.


## Install Teams PowerShell public preview

> [!NOTE]
> If you're using the Public Preview version of Teams PowerShell, we strongly recommend that you first uninstall Skype for Business Online Connector.

Installing the Teams PowerShell public preview module for all users on a system requires elevated privileges. Start the PowerShell
session using **Run as administrator** in Windows or use the `sudo` command on macOS or Linux.

If you're using PowerShell 5.1, you must update the **PowerShellGet** module beforehand. After you update **PowerShellGet**, close and reopen an elevated PowerShell session to ensure that the latest **PowerShellGet** is loaded.

```powershell
Install-Module PowerShellGet -Force -AllowClobber
```

To install Teams PowerShell public preview, run the PowerShell command below.

```powershell
Install-Module MicrosoftTeams -AllowPrerelease
```

## Install the Skype for Business Online Connector

> [!WARNING]
> Skype for Business Online Connector is currently part of Teams PowerShell public preview. Once we've rolled this feature into the GA release of Teams PowerShell, Skype for Business Online Connector will no longer be available.

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
> If you're using the latest [Teams PowerShell public preview release](https://www.powershellgallery.com/packages/MicrosoftTeams/), you don't need to install the Skype for Business Online Connector.

```powershell
$credential = Get-Credential

#Connect to Microsoft Teams
Connect-MicrosoftTeams -Credential $credential

#Connection to Skype for Business Online and import into Ps session
$session = New-CsOnlineSession -Credential $credential
Import-PsSession $session
```

## Update Teams PowerShell

To update Teams PowerShell, open a new elevated PowerShell command prompt and run the following:

```powershell
Update-Module MicrosoftTeams
```

> [!WARNING]
> If Teams PowerShell has already been imported into your PowerShell session, updating the module will fail. Close PowerShell and re-open a new elevated PowerShell session.


## Uninstall Teams PowerShell



To uninstall Teams PowerShell, open a new elevated PowerShell command prompt and run the following:

```powershell
Uninstall-Module MicrosoftTeams
```
> [!WARNING]
> If Teams PowerShell has already been imported into your PowerShell session, uninstalling the module will fail. Close PowerShell and re-open a new elevated PowerShell session.

## Next Steps

Now you're ready to manage Teams using Teams PowerShell. See [Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md) to get started.

## Related topics

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell Release Notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
