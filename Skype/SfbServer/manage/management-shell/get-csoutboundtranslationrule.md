---
title: "Get-CsOutboundTranslationRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0564df17-dcca-44e1-9341-15521e0fa14b
description: "Retrieves one or more outbound translation rules. An outbound translation rule converts phone numbers to the local dialing format for interaction with private branch exchange (PBX) systems and public switched telephone network (PSTN) gateways. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsOutboundTranslationRule
 
Retrieves one or more outbound translation rules. An outbound translation rule converts phone numbers to the local dialing format for interaction with private branch exchange (PBX) systems and public switched telephone network (PSTN) gateways. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsOutboundTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example retrieves all outbound translation rules for the Skype for Business Server 2015 deployment.
  
```
Get-CsOutboundTranslationRule
```

### EXAMPLE 2

This example retrieves a single outbound translation rule: the rule with Identity site:Redmond/Prefix Redmond.
  
```
Get-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond"
```

### EXAMPLE 3

This example retrieves all site-level outbound translation rules. The command calls the **Get-CsOutboundTranslationRule** cmdlet with a Filter of site:*, which will return a collection of all rules with Identity values beginning with the string site:.
  
```
Get-CsOutboundTranslationRule -Filter site:*
```

## Detailed Description

Call this cmdlet to retrieve an existing outbound translation rule. Skype for Business Server 2015 normalizes phone numbers to E.164 format. However, many private branch exchange (PBX) systems aren't able to work with this format. Outbound translations rules translate the number to the local dialing format prior to sending the number to the Mediation Server or gateway.
  
Each outbound translation rule is associated with a trunk configuration. More than one outbound translation rule can be associated with each trunk configuration. Therefore, the Identity for each rule consists of a scope along with a name that is unique within the scope (in the format scope/name, for example site:Redmond/OBR1). The rule is automatically associated with the trunk configuration with the same scope.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Performs a wildcard search on Identity that allows you to narrow down your results to only those outbound translation rules whose identities match the given wildcard string.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier for the outbound translation rule you want to retrieve. The Identity consists of the scope followed by a unique name within each scope (for example, site:Redmond/OutboundRule1). Specifying a value for Identity will return at most one outbound translation rule.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the outbound translation rule from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet retrieves one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule.
  
## See also

#### 

[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)
  
[Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)
  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)

