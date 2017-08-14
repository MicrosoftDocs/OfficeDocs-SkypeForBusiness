---
title: Remove-CsNetworkSubnet
ms.prod: SKYPEFORBUSINESS
ms.assetid: 251ddb5c-4837-4810-b46f-d276f9535653
---


# Remove-CsNetworkSubnet
[]
Removes an existing network subnet. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsNetworkSubnet -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example removes the subnet with the Identity (the Subnet ID) 172.11.15.0.
  
    
    

```

Remove-CsNetworkSubnet -Identity 172.11.15.0
```


### EXAMPLE 2

Example 2 removes all subnets associated with the Vancouver site. To do this, we begin by calling the **Get-CsNetworkSubnet** cmdlet. This will retrieve a collection of all subnets defined within the Skype for Business Server 2015 deployment. This collection of subnets is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet takes that collection and narrows it down to only those subnets with a NetworkSiteID equal to (-eq) Vancouver. Now that the collection consists only of subnets associated with the Vancouver site, we pipe the collection to the **Remove-CsNetworkSubnet** cmdlet, which removes every item in the collection.
  
    
    

```
Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Remove-CsNetworkSubnet
```


## Detailed Description

Each subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. Use this cmdlet to remove a network subnet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique subnet ID of the subnet you want to remove. This value will be an IP address (such as 174.11.12.0).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType object. Accepts pipelined input of network subnet objects.
  
    
    

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.
  
    
    

## See also


#### 


  
    
    
 [New-CsNetworkSubnet](new-csnetworksubnet.md)
  
    
    
 [Set-CsNetworkSubnet](set-csnetworksubnet.md)
  
    
    
 [Get-CsNetworkSubnet](get-csnetworksubnet.md)
