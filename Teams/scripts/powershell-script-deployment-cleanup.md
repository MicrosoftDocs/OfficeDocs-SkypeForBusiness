---
title: PowerShell script sample - Teams deployment cleanup
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.reviewer: amitsri
ms.service: msteams
audience: admin
description: Use this PowerShell script to uninstall Teams and remove the Teams folder for users. 
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# PowerShell script sample - Teams deployment clean up

Use this script to remove Teams. This script uninstalls Teams and removes the Teams folder for a user. Run this script for each user profile in which Teams was installed on a computer.


## Sample script

````powershell
<#
.SYNOPSIS
This script uninstalls the Teams app and removes the Teams directory for a user.
.DESCRIPTION
Use this script to remove and clear the Teams app from a computer. Run this PowerShell script for each user profile in which Teams was installed on the computer. After you run this script for all user profiles, redeploy Teams.
#>

$TeamsPath = [System.IO.Path]::Combine($env:LOCALAPPDATA, 'Microsoft', 'Teams')
$TeamsUpdateExePath = [System.IO.Path]::Combine($TeamsPath, 'Update.exe')

try
{
    if ([System.IO.File]::Exists($TeamsUpdateExePath)) {
        Write-Host "Uninstalling Teams process"

        # Uninstall app
        $proc = Start-Process $TeamsUpdateExePath "-uninstall -s" -PassThru
        $proc.WaitForExit()
    }
    Write-Host "Deleting Teams directory"
    Remove-Item –path $TeamsPath -recurse
}
catch
{
    Write-Output "Uninstall failed with exception $_.exception.message"
    exit /b 1
}

````

## Related topics

- [Install Microsoft Teams using Microsoft Endpoint Configuration Manager](../msi-deployment.md)
- [Deploy Teams with Microsoft 365 Apps](/deployoffice/teams-install)
