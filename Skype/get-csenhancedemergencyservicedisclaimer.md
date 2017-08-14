---
title: Get-CsEnhancedEmergencyServiceDisclaimer
ms.prod: SKYPEFORBUSINESS
ms.assetid: b5e3a01e-4056-47a0-9c3c-efdf55a08f69
---


# Get-CsEnhancedEmergencyServiceDisclaimer
[]
Retrieves the disclaimer text that is used globally to prompt for location information for an Enhanced 9-1-1 (E9-1-1) implementation. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsEnhancedEmergencyServiceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

This command retrieves the text of the enhanced emergency service disclaimer.
  
    
    

```

Get-CsEnhancedEmergencyServiceDisclaimer
```


## Detailed Description

In order for an Enterprise Voice implementation to provide E9-1-1 service, locations must be mapped to ports, subnets, switches, and wireless access points to identify the caller's location. When the caller is connecting from outside one of these mapped points, he must enter his location manually in order for it to be received by emergency services. This cmdlet retrieves a text string that will be displayed to users who decide not to enter their location information. This message will be displayed only if the LocationRequired property of the user's location policy is set to Disclaimer. (You can retrieve location policy settings by calling the **Get-CsLocationPolicy** cmdlet.)
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter allows for wildcard searches of the Identity. However, since the only valid value for Identity is Global, this parameter is not useful for this cmdlet.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |This will always be Global.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the disclaimer information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

Returns an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer.
  
    
    

## See also


#### 


  
    
    
 [Remove-CsEnhancedEmergencyServiceDisclaimer](remove-csenhancedemergencyservicedisclaimer.md)
  
    
    
 [Set-CsEnhancedEmergencyServiceDisclaimer](set-csenhancedemergencyservicedisclaimer.md)
  
    
    
 [Get-CsLocationPolicy](get-cslocationpolicy.md)
