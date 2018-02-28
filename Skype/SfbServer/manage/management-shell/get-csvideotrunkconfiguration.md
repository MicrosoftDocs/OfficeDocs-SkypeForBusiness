---
title: "Get-CsVideoTrunkConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a315bd1a-d682-435c-89ee-9bc649f474a0
description: "Use the Get-CsVideoTrunkConfiguration to retrieve Video Trunk configuration settings. Video trunk settings define the Session Initiation Protocol (SIP) trunk between the Video Interoperability Server (VIS) and a Video Gateway."
---

# Get-CsVideoTrunkConfiguration
[]
Use the **Get-CsVideoTrunkConfiguration** to retrieve Video Trunk configuration settings. Video trunk settings define the Session Initiation Protocol (SIP) trunk between the Video Interoperability Server (VIS) and a Video Gateway.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Get-CsVideoTrunkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example returns information about all the Video Trunk configurations in the organization.
  
```
Get-CsVideoTrunkConfiguration
```

### Example 2

This example returns information for a collection of Video Trunk configuration settings scoped to the Seattle site.
  
```
Get-CsVideoTrunkConfiguration -Identity "site:Seattle"
```

### Example 3

This example returns all the Video Trunk configurations configured at the site scope. This is done by including the Filter parameter and the filter value "site:\*".
  
```
Get-CsVideoTrunkConfiguration -Filter "site:*"
```

### Example 4

This example returns information about all the Video Trunk configurations for which session timers have been enabled. This is done by first using **Get-CsVideoTrunkConfiguration** to return a collection of all the available configurations. That collection is then piped to the **Where-Object** cmdlet, which filters the output by the EnableSessionTimer property setting.
  
```
Get-CsVideoTrunkConfiguration | Where-Object {$_.EnableSessionTimer -eq $True}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Video Trunk configuration settings are scoped to appropriate Video Gateway instances, and will govern the behavior of the SIP Trunk between each Video Gateway instance and the paired Video Interop Server instance that together define the Video Trunk. The Video Interop Server in Skype for Business Server 2015 enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business Server 2015 infrastructure. The Video Interop Server is a Skype service that runs on a standalone pool and cannot be co-located on an FE pool.
  
To enable the Video Interop Server, you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and third party video devices such as an internal Skype endpoint receiving video from an third party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between third party VTCs and internal endpoints.
  
Video Trunks settings can be managed by using the **CsVideoTrunkConfiguration** cmdlets. These settings are used to manage the following Video Trunk characteristics.
  
- RTCP for active calls for active calls
    
- RTCP for calls on hold
    
- Secure Real-time Transport Protocol (SRTP) use when Transport Layer Security (TLS) is used for the SIP signaling
    
- Session timers usage on the Video Interop Server (VIS) for dialogs associated with a Video Trunk
    
By default, Skype for Business Server 2015 ships with a single, global collection of Video Trunk configuration settings. However, administrators can use the **New-CsVideoTrunkConfiguration** cmdlet to create additional settings at the site or the service scope (for the Video Gateway service only).
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |The  _Filter_ parameter enables you to use wildcard characters in order to return one or more collections of Video Interop Server configuration settings. For example, to return all the settings that have been configured at the site scope use the following syntax: `-Filter "site:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The  _Identity_ parameter specifies the Video Trunk configuration to retrieve. Video Trunk configuration settings can be configured at the global, site, or service scope (for the VideoGateway service only). To refer to the global instance, use this syntax: `-Identity "global"` <br/> To refer to a collection at the site scope: `-Identity "site:Redmond"` <br/> Wildcard characters such as the asterisk (\*) cannot be used with the Identity parameter. To do a wildcard search for policies, use the Filter parameter instead.  <br/> If neither the  _Identity_ nor the _Filter_ parameter is specified then the **Get-CsVideoTrunkConfiguration** cmdlet returns information about all the Video Trunk configurations in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Video Trunk configuration data from the local copy of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsVideoTrunkConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsVideoTrunkConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoTrunkConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsVideoTrunkConfiguration](new-csvideotrunkconfiguration.md)
  
[Set-CsVideoTrunkConfiguration](set-csvideotrunkconfiguration.md)
  
[Remove-CsVideoTrunkConfiguration](remove-csvideotrunkconfiguration.md)

