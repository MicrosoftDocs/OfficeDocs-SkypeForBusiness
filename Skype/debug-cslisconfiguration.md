---
title: Debug-CsLisConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 8cc718d6-52ec-4ff3-a77e-8d6df1725fb0
---


# Debug-CsLisConfiguration
[]
Displays the Enhanced 9-1-1 (E9-1-1) Location Information service (LIS) configuration in XML format. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Debug-CsLisConfiguration [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

```


## Examples


  
    
    

### EXAMPLE 1

Running this command will display the entire LIS configuration to the Lync Server Management Shell window in XML format. By default, the output of the **Debug-CsLisConfiguration** cmdlet is displayed on one line, with an ellipsis (…) at the end of the line indicating that there's more than one line of data. Therefore, in this example we pipe the output to the **Format-Table** cmdlet, specifying the Wrap parameter, to display the full output wrapped to fit in the display window.
  
    
    

```

Debug-CsLisConfiguration | Format-Table -Wrap
```


## Detailed Description

The LIS configuration for an Enterprise Voice E9-1-1 implementation is stored in compressed format. This cmdlet un-compresses the configuration and displays it in XML format. This can make it quicker to debug issues with a configuration.
  
    
    
This cmdlet retrieves the location information from the Central Management store. When this information is created, it is stored in the location database; it does not move to the Central Management store until it is published with the **Publish-CsLisConfiguration** cmdlet. If the location information has not been published (or has been un-published with the **Unpublish-CsLisConfiguration** cmdlet), the **Debug-CsLisConfiguration** cmdlet will not return anything.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

Returns an object of type System.Management.Automation.PSCustomObject.
  
    
    

## See also


#### 


  
    
    
 [Publish-CsLisConfiguration](publish-cslisconfiguration.md)
  
    
    
 [Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)
  
    
    
 [Import-CsLisConfiguration](import-cslisconfiguration.md)
  
    
    
 [Export-CsLisConfiguration](export-cslisconfiguration.md)
  
    
    
 [Test-CsLisConfiguration](test-cslisconfiguration.md)
