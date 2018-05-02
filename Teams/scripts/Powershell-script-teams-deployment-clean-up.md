---
title: PowerShell Script Sample - Assists with Microsoft Teams Deployment Clean Up
author: ninadara
ms.author: ninadara
manager: serdars
ms.date: 03/21/2018
ms.topic: article
ms.service: msteams
description: Use this PowerShell script to create a public, company-wide team in Teams.
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
---

PowerShell Script Sample - Microsoft Teams deployment clean up
-------------------------------------------------------------------------

This PowerShell script can be leveraged for the cleanup of Microsoft Teams from target machines\users. It should be executed for every user on a targeted machine. 


## Sample script

````powershell
<#
.SYNOPSIS
This script allows you to uninstall the Microsoft Teams app and remove Teams directory for a user.
.DESCRIPTION
Use this script to clear the installed Microsoft Teams application. Run this PowerShell script for each user profile for which the Teams App was installed on a machine. After the PowerShell has executed on all user profiles, Teams can be redeployed.
#>

$TeamsPath = [System.IO.Path]::Combine($env:LOCALAPPDATA, 'Microsoft', 'Teams')
$TeamsUpdateExePath = [System.IO.Path]::Combine($env:LOCALAPPDATA, 'Microsoft', 'Teams', 'Update.exe')

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


