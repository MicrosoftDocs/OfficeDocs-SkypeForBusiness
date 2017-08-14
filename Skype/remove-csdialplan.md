---
title: Remove-CsDialPlan
ms.prod: SKYPEFORBUSINESS
ms.assetid: 99845b82-1730-494a-8f47-2dec5ef177c1
---


# Remove-CsDialPlan
[]
Removes the specified dial plan. This cmdlet can also be used to remove the global dial plan. If you remove the global dial plan, however, the dial plan will not actually be removed; instead, the settings will simply be reset to their default values. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsDialPlan -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 uses the **Remove-CsDialPlan** cmdlet to delete the per-user dial plan with the Identity RedmondDialPlan. Note that when you delete a dial plan, you do not necessarily have to assign a new plan to users who were assigned the now-deleted plan. Instead, those users will use the dial plan assigned to their service or site, or the global plan.
  
    
    

```

Remove-CsDialPlan -Identity RedmondDialPlan
```


### EXAMPLE 2

In Example 2 all the dial plans that include the word Redmond in their description are deleted. To do this, the command first calls the **Get-CsDialPlan** cmdlet to return a collection of all the dial plans configured for use within the organization. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to profiles that include the word Redmond in their description. After that's done, the filtered collection is passed to the **Remove-CsDialPlan** cmdlet, which removes all the dial plans in the collection.
  
    
    

```
Get-CsDialPlan | Where-Object {$_.Description -match "Redmond"} | Remove-CsDialPlan
```


## Detailed Description

This cmdlet removes an existing dial plan (also known as a location profile). Dial plans provide information required to enable Enterprise Voice users to make telephone calls. Dial plans are also used by the Conferencing Attendant application for dial-in conferencing. A dial plan determines such things as which normalization rules are applied and whether a prefix must be dialed for external calls.
  
    
    
Note: Removing a dial plan will also remove any associated normalization rules. If the global dial plan is removed, any associated normalization rules will also be removed, but a default global normalization rule will be created.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the dial plan you want to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile object. The **Remove-CsDialPlan** cmdlet accepts pipelined input of dial plan objects.
  
    
    

## Return Types

This cmdlet removes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile object.
  
    
    

## See also


#### 


  
    
    
 [New-CsDialPlan](new-csdialplan.md)
  
    
    
 [Set-CsDialPlan](set-csdialplan.md)
  
    
    
 [Get-CsDialPlan](get-csdialplan.md)
  
    
    
 [Grant-CsDialPlan](grant-csdialplan.md)
  
    
    
 [Test-CsDialPlan](test-csdialplan.md)
  
    
    
 [Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)
  
    
    
 [Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)
