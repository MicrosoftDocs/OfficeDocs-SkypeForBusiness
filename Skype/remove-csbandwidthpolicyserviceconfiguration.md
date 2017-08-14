---
title: Remove-CsBandwidthPolicyServiceConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: cf920168-3f65-4747-86cd-d3e287c84349
---


# Remove-CsBandwidthPolicyServiceConfiguration
[]
Removes an existing bandwidth policy service configuration. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsBandwidthPolicyServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example removes the bandwidth policy service configuration defined for the Redmond site ( `-Identity site:Redmond`).
  
    
    

```

Remove-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond
```


### EXAMPLE 2

Example 2 removes all bandwidth policy service configurations where logging is disabled. To accomplish this, the example begins with a call to the **Get-CsBandwidthPolicyServiceConfiguration** cmdlet. This will return a collection of all bandwidth policy service configurations in the Skype for Business Server 2015 deployment. This collection is then piped to the **Where-Object** cmdlet, which narrows the collection down to only those configurations where the EnableLogging property is equal to (-eq) False ($False). This leaves a collection of configurations that have logging disabled. This collection is then piped to the **Remove-CsBandwidthPolicyServiceConfiguration** cmdlet, which removes every item in the collection.
  
    
    

```
Get-CsBandwidthPolicyServiceConfiguration | Where-Object {$_.EnableLogging -eq $False} | Remove-CsBandwidthPolicyServiceConfiguration
```


## Detailed Description

Call admission control (CAC) is a way of determining whether to allow real-time communications sessions, such as voice or video calls, to be established based on bandwidth constraints. Within the Skype for Business Server 2015 implementation of CAC, regions, sites, and subnets are defined within a network along with the relationships and links between those entities in order to place bandwidth constraints between them. Bandwidth Policy service is the component that performs CAC functionality in the Skype for Business Server 2015 deployment, enabling the decision as to whether sufficient bandwidth exists for a call to be established. This cmdlet removes a bandwidth policy service configuration defined at the site level. You can also use the cmdlet to "remove" the global bandwidth policy service; however, the global service will not actually be removed, it will simply be reset to its default values.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the configuration you want to remove. This identifier will consist of the scope (for the global configuration) or the scope and name (for a site-level configuration, such as site:Redmond).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration object. Accepts pipelined input of bandwidth policy service configuration objects.
  
    
    

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration.
  
    
    

## See also


#### 


  
    
    
 [New-CsBandwidthPolicyServiceConfiguration](new-csbandwidthpolicyserviceconfiguration.md)
  
    
    
 [Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)
  
    
    
 [Get-CsBandwidthPolicyServiceConfiguration](get-csbandwidthpolicyserviceconfiguration.md)
