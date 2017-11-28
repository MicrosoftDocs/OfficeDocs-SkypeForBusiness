---
title: "Manage Skype for Business Online organizations using the Skype for Business Online Connector"
ms.author: tonysmit
author: tonysmit
ms.date: 5/17/2017
ms.audience: Admin
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Adm_Skype4B_Online
ms.assetid: c71f0d4d-5b6b-40ac-bc4a-6b97c05a121a
description: "Use Windows PowerShell and the Get-CsTenant and Get-CsTenantLicensingConfiguration cmdlets to get information about your Skype for Business Online tenant."
---

# Manage Skype for Business Online organizations using the Skype for Business Online Connector

You can find information about your Skype for Business Online tenant by using the **Get-CsTenant** and **Get-CsTenantLicensingConfiguration** cmdlets.
  
## Manage Skype for Business Online tenants

To return information about your Skype for Business Online tenant, call the [Get-CsTenant](https://go.microsoft.com/fwlink/p/?linkid=849599) cmdlet without any additional parameters.
  
```
Get-CsTenant
```

To return just the tenant name and ID, use this command.
  
```
Get-CsTenant | Select-Object Name, TenantID
```

The value of the  _TenantID_ parameter is required when running cmdlets such as[Set-CsTenantPublicProvider](https://go.microsoft.com/fwlink/p/?linkid=849602) and[Set-CsTenantFederationConfiguration](https://go.microsoft.com/fwlink/p/?linkid=849602).
  
To find information about whether licensing information for the specified tenant is available in the Skype for Business Online admin center, use the [Get-CsTenantLicensingConfiguration](https://go.microsoft.com/fwlink/p/?linkid=849606) cmdlet.
  

