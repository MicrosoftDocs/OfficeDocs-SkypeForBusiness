---
title: Remove-CsOutboundTranslationRule
ms.prod: SKYPEFORBUSINESS
ms.assetid: 73e0bd0d-2458-464a-9e6e-1868143aadc8
---


# Remove-CsOutboundTranslationRule
[]
Removes an existing outbound translation rule. An outbound translation rule converts phone numbers to the local dialing format for interaction with private branch exchange (PBX) systems. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsOutboundTranslationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example removes an existing outbound translation rule for site Redmond named Prefix Redmond. Identities are unique, so this command will delete a single rule.
  
    
    

```

Remove-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond"
```


### EXAMPLE 2

This example removes all site-level outbound translation rules. The first part of the command is a call to the **Get-CsOutboundTranslationRule** cmdlet with a Filter of site:*, which will return a collection of all rules with Identity values beginning with site:. This collection is then piped to the **Remove-CsOutboundTranslationRule** cmdlet, which removes each rule in the collection.
  
    
    

```
Get-CsOutboundTranslationRule -Filter site:* | Remove-CsOutboundTranslationRule
```


## Detailed Description

Call this cmdlet to remove an existing outbound translation rule. Skype for Business Server 2015 normalizes phone numbers to E.164 format. However, many private branch exchange (PBX) systems aren't able to work with this format. Outbound translations rules translate the number to the local dialing format prior to sending the number to the Mediation Server or gateway.
  
    
    
Each outbound translation rule is associated with a trunk configuration. That means that using this cmdlet to remove a rule will remove it from the trunk configuration at the corresponding scope.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the outbound translation rule you want to remove. The Identity consists of the scope followed by a unique name within each scope. For example, site:Redmond/OutboundRule1.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule object. Accepts pipelined input of outbound translation rule objects.
  
    
    

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule.
  
    
    

## See also


#### 


  
    
    
 [New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)
  
    
    
 [Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)
  
    
    
 [Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)
