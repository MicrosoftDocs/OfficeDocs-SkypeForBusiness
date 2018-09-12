---
title: PowerShell script sample - Create and assign a messaging policy to users 
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
description: Use this PowerShell script to create a messaging policy in Teams and assign it to users in your organization.
localization_priority: Normal
MS.collection: Strat_MT_TeamsAdmin
---

PowerShell script sample - Create and assign a messaging policy
-------------------------------------------------------------------------

Use this PowerShell script to create a messaging policy in Microsoft Teams and assign it to users. 

For complete instructions on using this PowerShell script, check out [Quick start - Teams for Education](./teams-quick-start-educ.yml).

If you're new to PowerShell and need help getting started, see [Overview of Azure PowerShell](https://docs.microsoft.com/powershell/azure/overview?view=azurermps-5.1.1).


## Sample script

````powershell
<#
.SYNOPSIS
This script creates a messaging policy in Teams and assigns it to users.
.DESCRIPTION
Use this script to create a messaging policy and assign it to your users.
#>

$dataSetFilePath = "<csv file with user ids for newly provisioned students> "
 $dataSet = Import-Csv "$($dataSetFilePath)" -Header UserId –delimiter ","
 foreach($line in $dataSet)
 {
    $userId = $line.UserId
    Write-Host $userId
    Grant-CsTeamsMessagingPolicy -PolicyName "<<PolicyName for a policy created with Chat Off>>" -Identity $userId
   
 }

````


