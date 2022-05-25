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

# Install Microsoft Teams PowerShell Module

This article explains how to install the Microsoft Teams PowerShell module using PowerShell Gallery. The Microsoft Teams PowerShell module is supported on all Windows platforms. Mac and Linux are not supported.

## Requirements

Microsoft Teams PowerShell module requires PowerShell 5.1 or higher on all platforms. Install the [latest version of PowerShell](/powershell/scripting/install/installing-powershell) available for your operating system. 

To check your PowerShell version, run the following command from within a PowerShell session: 

```powershell
$PSVersionTable.PSVersion 
```
We recommend that you use the  Install-Module cmdlet to install the Microsoft Teams PowerShell module. 
 
If PowerShell Gallery (PSGallery) isn't configured as a trusted repository for **PowerShellGet**, the first time you use the PSGallery you'll see the following message:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Answer **Yes** or **Yes to All** to continue with the installation.

## Installing using the PowerShellGallery

Microsoft Teams PowerShell module is currently supported for use with PowerShell 5.1 on Windows. Follow these steps to install the module: 

- Update to [Windows PowerShell 5.1](/powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell). If you're on Windows 10 version 1607 or higher, you already have PowerShell 5.1 installed. 
- Install [.NET Framework 4.7.2](/dotnet/framework/install) or later. 
- Run the following command to install the latest PowerShellGet:
 
```powershell
Install-Module -Name PowerShellGet -Force -AllowClobber
```
- Install the Teams PowerShell Module.

```powershell
Install-Module -Name MicrosoftTeams -Force -AllowClobber
```

## Offline Installation 

In some environments, it's not possible to connect to the PowerShell Gallery. In those situations, please follow these [manual installation steps](https://aka.ms/psgallery-manualdownload).  

## Sign in

To start working with Microsoft Teams PowerShell module, sign in with your Azure credentials.

```PowerShell
Connect-MicrosoftTeams 
``` 

## Update Teams PowerShell Module

To update any PowerShell module, you should use the same method used to install the module. For example, if you originally used Install-Module, then you should use [Update-Module](/powershell/module/powershellget/update-module) to get the latest version.  

```powershell
Update-Module MicrosoftTeams
```

> [!WARNING]
> If Teams PowerShell has already been imported into your PowerShell session, updating the module will fail. Close PowerShell and re-open a new elevated PowerShell session.


## Uninstall Teams PowerShell

To uninstall Microsoft Teams PowerShell, open a new PowerShell command prompt and run the following: 

```powershell
Uninstall-Module MicrosoftTeams

# Uninstall all versions of the module
Uninstall-Module MicrosoftTeams -Allversions 
```

## Next Steps 

Now you're ready to manage Microsoft Teams using Microsoft Teams PowerShell. See [Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md) to get started. 

## Related topics

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Teams PowerShell Release Notes](teams-powershell-release-notes.md)

[Microsoft Teams cmdlet reference](/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](/powershell/skype/intro?view=skype-ps)
