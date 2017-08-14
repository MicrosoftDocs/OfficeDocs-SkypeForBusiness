---
title: Remove-CsRoutingConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 80239fed-89ef-4ccc-be9b-d9149182d0c3
---


# Remove-CsRoutingConfiguration
[]
Resets the routing configuration to its default settings. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example resets the Global (and only) routing configuration to the default settings. This action deletes all defined voice routes, so we added the Confirm parameter in order to receive a prompt asking whether we really want to perform this action before the removal takes place.
  
    
    

```

Remove-CsRoutingConfiguration -Identity Global -Confirm
```


## Detailed Description

Voice routes contain instructions that tell Skype for Business Server 2015 how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet removes the global (and only) routing configuration, which is a container for all voice routes defined for a Skype for Business Server 2015 deployment. "Removing" the routing configuration doesn't actually remove it; the Global (and only) instance is still there. However, it does set the list of voice routes to the default settings. 
  
    
    
WARNING: Removing the routing configuration (in other words, setting the list of voice routes to the default) deletes all defined voice routes for a Skype for Business Server 2015 deployment and replaces them with a single route with default settings.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the routing configuration to remove. This value must be Global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.Policy.Voice.PSTNRoutingSettings object. Accepts pipelined input of a routing configuration object.
  
    
    

## Return Types

This cmdlet removes (resets) an object of type Microsoft.Rtc.Management.Policy.Voice.PSTNRoutingSettings.
  
    
    

## See also


#### 


  
    
    
 [New-CsRoutingConfiguration](new-csroutingconfiguration.md)
  
    
    
 [Set-CsRoutingConfiguration](set-csroutingconfiguration.md)
  
    
    
 [Get-CsRoutingConfiguration](get-csroutingconfiguration.md)
  
    
    
 [Remove-CsVoiceRoute](remove-csvoiceroute.md)
  
    
    
 [Get-CsVoiceRoute](get-csvoiceroute.md)
