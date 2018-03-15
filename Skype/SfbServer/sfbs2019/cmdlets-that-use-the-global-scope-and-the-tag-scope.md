---
title: "Cmdlets in Skype for Business Online that use the global scope and the tag scope"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 1e2bc055-8a72-425e-967b-e253add7018c
description: "In Skype for Business Online, policies can be configured at either the global scope or at the tag scope (or per-user scope). When using the Get-Cs cmdlets, you do not have to specify a scope or identity. If you call one of these cmdlets without any parameters, then all the relevant items will be returned. For example, this command returns information about all your external access policies:"
---

# Cmdlets in Skype for Business Online that use the global scope and the tag scope
[]
In Skype for Business Online, policies can be configured at either the global scope or at the tag scope (or per-user scope). When using the **Get-Cs** cmdlets, you do not have to specify a scope or identity. If you call one of these cmdlets without any parameters, then all the relevant items will be returned. For example, this command returns information about all your external access policies: 
  
```
Get-CsExternalAccessPolicy
```

You need to include only the Identity parameter or the Filter parameter if you want to limit the returned data. For example, to return only the global policy, use this command:
  
```
Get-CsExternalAccessPolicy -Identity "global"
```

To return a per-user policy that has the Identity "RedmondAccessPolicy", use this command:
  
```
Get-CsExternalAccessPolicy -Identity "RedmondAccessPolicy"
```

> [!NOTE]
> When referencing a per-user policy, the tag **prefix** is optional. This syntax, which includes the prefix, is also valid: > Get-CsExternalAccessPolicy -Identity "tag:RedmondAccessPolicy" 
  
To return all policies except the global policies (that is, all the per-user policies), use this command:
  
```
Get-CsExternalAccessPolicy -Filter "tag:*"
```

The following cmdlets operate against both the global scope and the per-user (tag) scope:
  
- [Get-CsClientPolicy](get-csclientpolicy.md)
    
- [Get-CsConferencingPolicy](get-csconferencingpolicy.md)
    
- [Get-CsDialPlan](get-csdialplan.md)
    
- [Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)
    
- [Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)
    
- [Get-CsPresencePolicy](get-cspresencepolicy.md)
    
- [Get-CsVoicePolicy](get-csvoicepolicy.md)
    
> [!NOTE]
> Despite the name, dial plans are, functionally speaking, policies. The term dial plan is used instead of, for example, dialing policy, in order to preserve the terminology used with previous versions of Lync Server. 
  
## See also

#### 

[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants.md)
  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)

