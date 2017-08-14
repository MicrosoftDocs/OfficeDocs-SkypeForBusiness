---
title: Remove-CsEnhancedEmergencyServiceDisclaimer
ms.prod: SKYPEFORBUSINESS
ms.assetid: 30a5aa8c-04b8-4c1f-92b3-88c86bf69a52
---


# Remove-CsEnhancedEmergencyServiceDisclaimer
[]
Removes the disclaimer text that is used globally to prompt for location information for an Enhanced 9-1-1 (E9-1-1) implementation. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsEnhancedEmergencyServiceDisclaimer -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This command removes the text of the enhanced emergency service disclaimer. Note that this does not remove the global disclaimer; it still exists. It simply sets the Body property to an empty string.
  
    
    

```

Remove-CsEnhancedEmergencyServiceDisclaimer -Identity global
```


## Detailed Description

In order for an Enterprise Voice implementation to provide E9-1-1 service, locations must be mapped to ports, subnets, switches, and wireless access points to identify the caller's location. When the caller is connecting from outside one of these mapped points, he must enter his location manually for it to be received by emergency services. This cmdlet removes the text string that will be displayed to users who choose not to enter their location information. This message will be displayed only if the LocationRequired property of the user's location policy is set to Disclaimer. (You can retrieve location policy settings by calling the **Get-CsLocationPolicy** cmdlet.) After calling this cmdlet, a blank message will be displayed to users in this case.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |This value is required and must be set to Global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer object. Accepts pipelined input of an enhanced emergency service disclaimer object.
  
    
    

## Return Types

This cmdlet does not return a value or an object. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer.
  
    
    

## See also


#### 


  
    
    
 [Set-CsEnhancedEmergencyServiceDisclaimer](set-csenhancedemergencyservicedisclaimer.md)
  
    
    
 [Get-CsEnhancedEmergencyServiceDisclaimer](get-csenhancedemergencyservicedisclaimer.md)
  
    
    
 [Get-CsLocationPolicy](get-cslocationpolicy.md)
