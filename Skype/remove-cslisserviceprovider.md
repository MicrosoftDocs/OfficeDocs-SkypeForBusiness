---
title: Remove-CsLisServiceProvider
ms.prod: SKYPEFORBUSINESS
ms.assetid: d26302bf-7794-4125-af80-ba7c92096b6d
---


# Remove-CsLisServiceProvider
[]
Removes an object containing information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to verify locations. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsLisServiceProvider [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example removes the service provider web service from the E9-1-1 implementation. There will only be, at most, one service provider defined, which will be removed by this cmdlet.
  
    
    

```

Remove-CsLisServiceProvider
```


## Detailed Description

In an Enterprise Voice implementation with E9-1-1, emergency calls must first be routed through an E9-1-1 Network Routing Provider to ensure that the calls are routed to the appropriate Public Safety Answering Point (PSAP). (A PSAP is the agency in the United States that directs the calls to the nearest emergency services, such as police, fire, and ambulance services.) In order to do this, the provider must have a list of locations from the organization that it can then match against the Master Street Address Guide to ensure all locations are valid. This cmdlet removes an entry for a provider; after running this cmdlet there will be no web service access to the provider.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

Accepts pipelined input of a Location Information Server (LIS) service provider object.
  
    
    

## Return Types

This cmdlet does not return an object or a value. It removes an object of type System.Management.Automation.PSCustomObject.
  
    
    

## See also


#### 


  
    
    
 [Set-CsLisServiceProvider](set-cslisserviceprovider.md)
  
    
    
 [Get-CsLisServiceProvider](get-cslisserviceprovider.md)
