---
title: Sample script - Microsoft Teams firewall PowerShell script
author: dstrome
ms.author: dstrome
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
ms.reviewer: harij, rafarhi
ms.localizationpriority: medium
search.appverid: MET150
description: A sample script that can be used to configure Windows to allow Teams connections through Windows Firewall.
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# Sample script - Microsoft Teams firewall PowerShell script

This sample script, which needs to run on client computers in the context of an elevated administrator account, will create a new inbound firewall rule for each user folder found in c:\users. When Teams finds this rule, it will prevent the Teams application from prompting users to create firewall rules when the users make their first call from Teams.

```powershell

<#
.SYNOPSIS
   Creates firewall rules for Teams.
.DESCRIPTION
   (c) Microsoft Corporation 2018. All rights reserved. Script provided as-is without any warranty of any kind. Use it freely at your own risks.
   Must be run with elevated permissions. Can be run as a GPO Computer Startup script, or as a Scheduled Task with elevated permissions.
   The script will create a new inbound firewall rule for each user folder found in c:\users.
   Requires PowerShell 3.0.
#>

#Requires -Version 3

$users = Get-ChildItem (Join-Path -Path $env:SystemDrive -ChildPath 'Users') -Exclude 'Public', 'ADMINI~*'
if ($null -ne $users) {
    foreach ($user in $users) {
        $progPath = Join-Path -Path $user.FullName -ChildPath "AppData\Local\Microsoft\Teams\Current\Teams.exe"
        if (Test-Path $progPath) {
            if (-not (Get-NetFirewallApplicationFilter -Program $progPath -ErrorAction SilentlyContinue)) {
                $ruleName = "Teams.exe for user $($user.Name)"
                "UDP", "TCP" | ForEach-Object { New-NetFirewallRule -DisplayName $ruleName -Direction Inbound -Profile Domain -Program $progPath -Action Allow -Protocol $_ }
                Clear-Variable ruleName
            }
        }
        Clear-Variable progPath
    }
}

```
