---
title: "Get-CsVoiceRoute"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 422abb2d-bff3-4b9a-b18c-d8202b01f69b
description: "Returns information about the voice routes configured for use in an organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsVoiceRoute
 
Returns information about the voice routes configured for use in an organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsVoiceRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Retrieves the properties for all voice routes defined within the organization.
  
```
Get-CsVoiceRoute
```

### EXAMPLE 2

Retrieves the properties for the Route1 voice route.
  
```
Get-CsVoiceRoute -Identity Route1
```

### EXAMPLE 3

This command displays voice route settings where the Identity contains the string "test" anywhere within the value. To find the string test only at the end of the Identity, use the value \*test. Similarly, to find the string test only if it occurs at the beginning of the Identity, specify the value test\*.
  
```
Get-CsVoiceRoute -Filter *test*
```

### EXAMPLE 4

This command retrieves all voice routes that have not had any PSTN gateways assigned. First all voice routes are retrieved using the **Get-CsVoiceRoute** cmdlet. These voice routes are then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet narrows down the results of the Get operation. In this case we look at each voice route (that's what the $_ represents) and check the Count property of the PstnGatewayList property. If the count of PSTN gateways is 0, the list is empty and no gateways have been defined for the route.
  
```
Get-CsVoiceRoute | Where-Object {$_.PstnGatewayList.Count -eq 0}
```

## Detailed Description

Use this cmdlet to retrieve one or more existing voice routes. Voices routes contain instructions that tell Skype for Business Server 2015 how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX).
  
This cmdlet can be used to retrieve voice route information such as which PSTN gateways the route is associated with (if any), which PSTN usages are associated with the route, the pattern (in the form of a regular expression) that identifies the phone numbers to which the route applies, and caller ID settings. The PSTN usage associates the voice route to a voice policy.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter filters the results of the Get operation based on the wildcard value passed to this parameter.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string that uniquely identifies the voice route. If no identity is provided, all voice routes for the organization are returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice route from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route object.
  
## See also

#### 

[New-CsVoiceRoute](new-csvoiceroute.md)
  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)
  
[Set-CsVoiceRoute](set-csvoiceroute.md)
  
[Test-CsVoiceRoute](test-csvoiceroute.md)

