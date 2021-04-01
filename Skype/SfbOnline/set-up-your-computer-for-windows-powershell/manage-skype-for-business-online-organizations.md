---
title: "Manage Skype for Business Online organizations"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: c71f0d4d-5b6b-40ac-bc4a-6b97c05a121a
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1.keywords:
- NOCSH
ms.custom:
- PowerShell
description: "Use Windows PowerShell and the Get-CsTenant and Get-CsTenantLicensingConfiguration cmdlets to get information about your Skype for Business Online tenant."
---

# Manage Skype for Business Online organizations
> [!NOTE]
> The latest [Teams PowerShell public preview release](https://www.powershellgallery.com/packages/MicrosoftTeams/) is integrated with Skype for Business Online Connector, providing a single module for Teams PowerShell management.

You can find information about your Skype for Business Online tenant by using the **Get-CsTenant** and **Get-CsTenantLicensingConfiguration** cmdlets.
  
## Manage Skype for Business Online tenants

To return information about your Skype for Business Online tenant, call the [Get-CsTenant](/powershell/module/skype/Get-CsTenant) cmdlet without any additional parameters.
  
```PowerShell
Get-CsTenant
```

To return just the tenant name and ID, use this command.
  
```PowerShell
Get-CsTenant | Select-Object Name, TenantID
```

The value of the  _TenantID_ parameter is required when running cmdlets such as [Set-CsTenantPublicProvider](/powershell/module/skype/Set-CsTenantPublicProvider) and [Set-CsTenantFederationConfiguration](/powershell/module/skype/Set-CsTenantFederationConfiguration).
  
To find information about whether licensing information for the specified tenant is available in the Skype for Business Online admin center, use the [Get-CsTenantLicensingConfiguration](/powershell/module/skype/Get-CsTenantLicensingConfiguration) cmdlet.
  
## Related topics
[Set up your computer for skype for business online management using Windows PowerShell](set-up-your-computer-for-windows-powershell.md)

  
