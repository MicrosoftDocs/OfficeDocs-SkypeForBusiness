---
title: "Cmdlets in Skype for Business Online that use the Tenant parameter"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: e7fe7c12-fbe0-49c1-9e8c-eef6958f27d0
description: "When modifying your public provider settings, you always need to supply a Tenant identity; this is true even if you only have a single tenant. For example, this command sets Windows Live as the only public provider your users are allowed to communicate with:"
---

# Cmdlets in Skype for Business Online that use the Tenant parameter
[]
When modifying your public provider settings, you always need to supply a Tenant identity; this is true even if you only have a single tenant. For example, this command sets Windows Live as the only public provider your users are allowed to communicate with:
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"
```

Fortunately, you do not need to type the Tenant ID (for example, bf19b7db-6960-41e5-a139-2aa373474354) each time you run one of these cmdlets. Instead, you can retrieve the Tenant ID by running the [Get-CsTenant](get-cstenant.md) cmdlet, storing the Tenant ID in a variable, and then using that variable when you call one of the other cmdlets. For example: 
  
```
$x = (Get-CsTenant).TenantId
Set-CsTenantPublicProvider -Tenant $x -Provider "WindowsLive"
```

Alternatively, you can do this in a single command by retrieving the Tenant ID and then piping that value to the Set-CsTenantPublicProvider cmdlet:
  
```
Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider "WindowsLive"}
```

You do not need to specify the tenant ID when calling the **Get-CsTenant** cmdlet. This command returns information about your tenant: 
  
```
Get-CsTenant
```

The following cmdlets accept a tenant identity. However, in these cases, the parameter is optional and does not need to be entered when calling the cmdlet. Instead, Windows PowerShell will effectively enter the tenant identity for you based on the Skype for Business Online tenant you are currently connected to:
  
- [Get-CsTenant](get-cstenant.md)
    
- [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)
    
- [Set-CsTenantHybridConfiguration](set-cstenanthybridconfiguration.md)
    
- [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)
    
- [Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)
    
- [Get-CsTenantLicensingConfiguration](get-cstenantlicensingconfiguration.md)
    
For example, the **Get-CsTenantFederationConfiguration** cmdlet can be called by using this command: 
  
```
Get-CsTenantFederationConfiguration
```

Although not required, you can include the Tenant parameter when calling Get-CsTenantFederationConfiguration :
  
```
Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"
```

## See also

#### 

[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants.md)
  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)

