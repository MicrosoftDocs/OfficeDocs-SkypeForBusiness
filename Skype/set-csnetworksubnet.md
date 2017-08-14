---
title: Set-CsNetworkSubnet
ms.prod: SKYPEFORBUSINESS
ms.assetid: 9e85cdbb-b5fb-48d6-8f95-6e7cba9d9597
---


# Set-CsNetworkSubnet
[]
Modifies an existing network subnet. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsNetworkSubnet [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

This example modifies the subnet with the Identity (the Subnet ID) 172.11.15.0. The subnet is modified with a new MaskBits value (25) and a new NetworkSiteID (Chicago).
  
    
    

```

Set-CsNetworkSubnet -Identity 172.11.15.0 -MaskBits 25 -NetworkSiteID Chicago
```


### EXAMPLE 2

Example 2 moves all subnets on the Vancouver site to the Chicago site. To do this, we begin by calling the **Get-CsNetworkSubnet** cmdlet. This will retrieve a collection of all subnets defined within the Skype for Business Server 2015 deployment. This collection of subnets is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet takes that collection and narrows it down to only those subnets with a NetworkSiteID equal to (-eq) Vancouver. Now that the collection consists only of subnets associated with the Vancouver site, we pipe the collection to the **Set-CsNetworkSubnet** cmdlet. We supply one parameter to the **Set-CsNetworkSubnet** cmdlet: NetworkSiteID. By passing the parameter a value of Chicago, we're instructing the **Set-CsNetworkSubnet** cmdlet to change the network site ID of every member of the collection to Chicago.
  
    
    

```
Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Set-CsNetworkSubnet -NetworkSiteID Chicago
```


## Detailed Description

Each subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. Use this cmdlet to modify the associated network site, change the description of the subnet, or modify the mask bits for the subnet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |String  <br/> |A description of the subnet being modified.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |The unique subnet ID of the subnet you want to modify. This value will be either an IP address (such as 174.11.12.0) or a URL beginning with http: or https:.  <br/> |
| _Instance_ <br/> |Optional  <br/> |SubnetType  <br/> |A reference to the network subnet object that you want to modify. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType, which can be retrieved by calling the **Get-CsNetworkSubnet** cmdlet. <br/> |
| _MaskBits_ <br/> |Optional  <br/> |Int32  <br/> |The bitmask to be applied to the subnet.  <br/> |
| _NetworkSiteID_ <br/> |Optional  <br/> |String  <br/> |The site ID of the network site to which this subnet is to be applied. You can retrieve site IDs for your deployment by calling the **Get-CsNetworkSite** cmdlet. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType object. Accepts pipelined input of network subnet objects.
  
    
    

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.
  
    
    

## See also


#### 


  
    
    
 [New-CsNetworkSubnet](new-csnetworksubnet.md)
  
    
    
 [Remove-CsNetworkSubnet](remove-csnetworksubnet.md)
  
    
    
 [Get-CsNetworkSubnet](get-csnetworksubnet.md)
