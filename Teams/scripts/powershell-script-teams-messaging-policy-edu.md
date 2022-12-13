---
title: PowerShell script sample - Create & assign messaging policy
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.reviewer: ritikag
ms.service: msteams
audience: admin
description: Use this PowerShell script to create a messaging policy in Teams and assign it to users in your organization.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# PowerShell script sample - Create and assign a messaging policy

Use this PowerShell script to create a messaging policy in Microsoft Teams and assign it to users. 

For more information about using this PowerShell script, see [Quick start - Teams for Education](../teams-quick-start-edu.yml).

This script uses the [Grant-CsTeamsMessagingPolicy](/powershell/module/skype/grant-csteamsmessagingpolicy) cmdlet which is in the Skype for Business Online PowerShell module. See [Teams PowerShell overview](../teams-powershell-overview.md) to learn more about managing Teams using PowerShell.


## Before you start

Download and install the [Skype for Business Online PowerShell module](https://www.microsoft.com/download/details.aspx?id=54616), and then restart your computer if prompted.

To lean more, see [Manage Skype for Business Online with Office 365 PowerShell](/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

## Sample script

```powershell
<#
.SYNOPSIS
This script creates a messaging policy in Teams and assigns it to users.
.DESCRIPTION
Use this script to create a messaging policy and assign it to users in your organization.
#>

$dataSetFilePath = "<csv file with user ids for newly provisioned students> "
 $dataSet = Import-Csv "$($dataSetFilePath)" -Header UserId –delimiter ","
 foreach($line in $dataSet)
 {
    $userId = $line.UserId
    Write-Host $userId
    Grant-CsTeamsMessagingPolicy -PolicyName "<<PolicyName for a policy created with Chat Off>>" -Identity $userId

 }
```

> [!NOTE]
> You can also assign a messaging policy directly to users at scale through a batch policy assignment or to a group that the users are members of. For more information see [Assign policies to large sets of users in your school](../batch-group-policy-assignment-edu.md) and [Assign policies to your users in Teams](../policy-assignment-overview.md).