---
title: "Cmdlets in Skype for Business Online that use only the global scope"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 0ffd3bc9-a6a1-4c2e-8d52-e599acc49d2d
description: "A number of Skype for Business Online settings are available only at the global scope. This means that there is a single collection of settings that applies to all the users who are assigned to that tenant. (Each tenant has its own unique collection of global settings.) When you are using cmdlets that are limited to the global scope, the Identity parameter is optional. For example, to retrieve meeting configuration settings, you can use this command:"
---

# Cmdlets in Skype for Business Online that use only the global scope
[]
A number of Skype for Business Online settings are available only at the global scope. This means that there is a single collection of settings that applies to all the users who are assigned to that tenant. (Each tenant has its own unique collection of global settings.) When you are using cmdlets that are limited to the global scope, the Identity parameter is optional. For example, to retrieve meeting configuration settings, you can use this command:
  
```
Get-CsMeetingConfiguration -Identity "global"
```

Alternatively, you can omit the Identity parameter and use this simpler command instead:
  
```
Get-CsMeetingConfiguration
```

Because there is only one global collection of meeting configuration settings, the two commands return the exact same information. The Identity parameter can also be omitted when using one of the **Set-Cs** cmdlets. These two commands are identical: 
  
```
Set-CsMeetingConfiguration -Identity "global" -AdmitAnonymousUsersByDefault $False
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False
```

The two commands are identical because, by default, Windows PowerShell will modify the global collection if you do not include the Identity parameter.
  
The following cmdlets operate only at the global scope:
  
- [Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)
    
- [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)
    
- [Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)
    
- [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)
    
- [Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)
    
- [Get-CsTenantLicensingConfiguration](get-cstenantlicensingconfiguration.md)
    
- [Get-CsTenantPublicProvider](get-cstenantpublicprovider.md)
    
- [Remove-CsVoicePolicy](remove-csvoicepolicy.md)
    
- [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)
    
- [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)
    
Note that the **Remove-CsVoicePolicy** cmdlet is something of an anomaly. First, this cmdlet does require you to include the Identity parameter: 
  
```
Remove-CsVoicePolicy -Identity "global"
```

Second, the **Remove-CsVoicePolicy** cmdlet does not actually delete the global voice policy; Skype for Business Online does not allow you to delete global policies or configuration settings. What the cmdlet does do is enable you to reset all the properties in the global voice policy to their default values. For example, by default, the AllowCallForwarding property is set to False. However, AllowCallForwarding may have been modified, with the value now set to True. When you run the **Remove-CsVoicePolicy** cmdlet, the AllowCallForwarding property will revert to its default value: False. The following table summarizes this scenario: 
  
|**AllowCallForwarding Value**|**Scenario**|
|:-----|:-----|
|False  <br/> |Default value  <br/> |
|True  <br/> |After the global policy has been modified  <br/> |
|False  <br/> |After **Remove-CsVoicePolicy** cmdlet has been run  <br/> |
   
## See also

#### 

[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants.md)
  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)

