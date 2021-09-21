---
title: ITAdmins set-up for the EDU Microsoft Parents app
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: 
description: Microsoft Teams for EDU article document prerequisites and PowerShell set-up for the Parents app.
ms.localizationpriority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

[!INCLUDE [preview-feature](includes/preview-feature.md)]

# deploying the parents app in Microsoft Teams

Enabling the parents app in Microsoft Teams is a straightforward process for admins, delivering a secure method for educators to communicate to students and their contacts that remains in-tenant, and which will scale across your educator organization.

## Requirements

- SDS (School data sync) - You'll need to upload related contacts associated with your students into SDS’s using the CSV option. Check out [Configure CSV for SDS](/schooldatasync/set-up-your-sds-flow) and [Update relatedContacts](/graph/api/relatedcontact-update) for more information.
- In Teams admin center, the Class Owner must have **Chat** enabled; as well as **Federated chat** with **Teams accounts not management by an organization**

If you need to enable federated chat on a per-user basis, the steps are below.

## Enabling federated chat on a per-user basis

1. Install latest MicrosoftTeams powershell module preview

```powershell
Install-Module -Name PowerShellGet -Force -AllowClobber
Install-Module -Name MicrosoftTeams -AllowPrerelease -Force -AllowClobber
```

2. Run in powershell window using credentials that have admin privileges

```powershell
$credential = Get-Credential
Connect-MicrosoftTeams -Credential $credential
```

3. Turn off and on at the global group/user level configuration or tenant level configuration

```powershell
#Retrieves tenant level configuration
Get-CsTenantFederationConfiguration
#Turn OFF tenant level configuration
Set-CsTenantFederationConfiguration -AllowTeamsConsumer $false
#Turn ON tenant level configuration
Set-CsTenantFederationConfiguration -AllowTeamsConsumer $true
#Turn OFF Global GROUP/USER level configuration
Set-CsExternalAccessPolicy -EnableTeamsConsumerAccess $false
#Turn ON Global GROUP/USER level configuration
Set-CsExternalAccessPolicy -EnableTeamsConsumerAccess $false
```

> [!NOTE]
> When running this PowerShell, changes can take an hour or more to complete.

## More information

[CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)
[Assigning your policy to a user](/powershell/module/skype/grant-csexternalaccesspolicy)
