---
title: Install the pre-release version of the Teams PowerShell module
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: brandber
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Follow these steps to install the pre-release version of the Teams PowerShell module from the PowerShell Test Gallery.
---

# Install the pre-release version of the Teams PowerShell module

This article describes how to install the latest pre-release version of the Teams PowerShell module from the [PowerShell Test Gallery](https://www.poshtestgallery.com/packages/MicrosoftTeams/). You need the pre-release version of the Teams PowerShell module in scenarios where cmdlets for managing a Teams feature aren't supported in the Generally Available version of the module and are only available in the pre-release version of the module.

Use these steps to install the latest pre-release version of the Teams PowerShell module from the PowerShell Test Gallery.

> [!NOTE]
> Don't install the Teams PowerShell module from the PowerShell Test Gallery side-by-side with a version of the module from the [public PowerShell Gallery](https://www.powershellgallery.com/packages/MicrosoftTeams/). Follow these steps to first uninstall the Teams PowerShell module from the public PowerShell Gallery, and then install the latest version of the module from the PowerShell Test Gallery.

1. Close all existing PowerShell sessions.
2. Start a new instance of the Windows PowerShell module.
3. Run the following to uninstall the Teams PowerShell module from the public PowerShell Gallery:

    ```PowerShell
    Uninstall-Module -Name MicrosoftTeams
    ```

4. Close all existing PowerShell sessions.
5. Start the Windows PowerShell module again, and then run the following to register the PowerShell Test Gallery as a trusted source:

    ```PowerShell
    Register-PSRepository -Name PSGalleryInt -SourceLocation https://www.poshtestgallery.com/ -InstallationPolicy Trusted
    ```

6. Run the following to install the latest Teams PowerShell module from the PowerShell Test Gallery:

    ```PowerShell
    Install-Module -Name MicrosoftTeams -Repository PSGalleryInt -Force
    ```

7. Run the following to verify that the latest version of the Teams PowerShell module from the PowerShell Test Gallery is successfully installed:

    ```PowerShell
    Get-Module -Name MicrosoftTeams
    ```

#### Update to the latest version of the Teams PowerShell module from the PowerShell Test Gallery

If you already installed the Teams PowerShell module from the PowerShell Test Gallery, use the following steps to update to the latest version.

1. Close all existing PowerShell sessions.
2. Start a new instance of the Windows PowerShell module.
3. Run the following to update the currently installed version of the Teams PowerShell module from the PowerShell Test Gallery:

    ```PowerShell
    Update-Module -Name MicrosoftTeams -Force
    ```

4. Run the following to verify that the latest version of the Teams PowerShell module from the PowerShell Test Gallery is successfully installed:

    ```PowerShell
    Get-Module -Name MicrosoftTeams
    ```

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
