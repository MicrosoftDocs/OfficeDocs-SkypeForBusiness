---
title: Remove-CsNetworkConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: d6945015-67f7-4f04-87ae-7cb977650d96
---


# Remove-CsNetworkConfiguration
[]
Resets all the network configuration settings for a Skype for Business Server 2015 deployment to the default values. This deletes an entire call admission control (CAC) deployment and related E9-1-1 configuration. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsNetworkConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example removes all CAC, location, E9-1-1 network, and media bypass settings. The Confirm parameter is used so you'll be prompted to verify you really want to do this before everything is deleted.
  
    
    

```

Remove-CsNetworkConfiguration -Identity Global -Confirm
```


## Detailed Description

WARNING: Running this cmdlet will delete an entire network configuration, including CAC, E9-1-1 regions and sites, and media bypass.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |This will always be Global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. It is recommended that you always use this parameter with this cmdlet.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object. Accepts pipelined input of a network configuration object.
  
    
    

## Return Types

This cmdlet does not return an object. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object.
  
    
    

## See also


#### 


  
    
    
 [Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)
  
    
    
 [Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)
  
    
    
 [Get-CsNetworkSite](get-csnetworksite.md)
  
    
    
 [Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
  
    
    
 [Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)
  
    
    
 [Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)
  
    
    
 [Get-CsNetworkRegion](get-csnetworkregion.md)
  
    
    
 [Get-CsNetworkSubnet](get-csnetworksubnet.md)
  
    
    
 [Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
