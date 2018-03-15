---
title: "Get-CsVideoTrunk"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dbc9cdd6-28bb-430d-af9c-2bfa44ced167
description: "Use the Get-CsVideoTrunk to list properties about the video trunks in your organization. Video trunks are Session Initiation Protocol (SIP) trunks between the Video Interop Server and a Video Gateway that are used to setup video calls between 3rd party video teleconferencing systems (VTCs) connected to the Video Gateway and Skype conferences or Skype endpoints."
---

# Get-CsVideoTrunk
 
Use the **Get-CsVideoTrunk** to list properties about the video trunks in your organization. Video trunks are Session Initiation Protocol (SIP) trunks between the Video Interop Server and a Video Gateway that are used to setup video calls between 3rd party video teleconferencing systems (VTCs) connected to the Video Gateway and Skype conferences or Skype endpoints.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Get-CsVideoTrunk [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example returns information about all the video trunks configured for use in the organization.
  
```
Get-CsVideoTrunk
```

### Example 2

This example returns information for a single video trunk with the identity "VideoTrunk:192.168.0.240".
  
```
Get-CsVideoTrunk -Identity "VideoTrunk:192.168.0.240"
```

### Example 3

This example uses the  _Filter_ parameter to return all the video trunks located on the IP subnet 192.168. The filter value "VideoTrunk:192.168*" limits the returned data to video trunks that having an Identity that begins with the string value "192.168".
  
```
Get-CsVideoTrunk -Filter "VideoTrunk:192.168*"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Video trunks are SIP trunks between the Video Interop Server and a Video Gateway that are used to setup video calls between 3rd party video teleconferencing systems (VTCs) connected to the Video Gateway and Skype conferences or Skype endpoints.
  
Trunk information is read-only. You cannot create, delete or modify trunks by using Windows PowerShell. Those operations can only be carried out by using Skype for Business Server 2015 Topology Builder.
  
To return a list of all the role-based access control (RBAC) roles that can run this cmdlet (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "Get-CsVideoTrunk"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a video trunk (or a collection of video trunks).  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the video trunk to be returned. For example:  <br/>  `-Identity "VideoTrunk:192.168.0.240"` <br/> You cannot use wildcards when specifying an Identity. Use the  _Filter_ parameter instead. <br/> If this parameter is not specified, then all the video trunks in the organization are returned.  <br/> |
| _PoolFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the trunk as defined in the topology. For example:  <br/>  `-PoolFqdn "atl-trunk-001.litwareinc.com"` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsVideoTrunk** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsVideoTrunk** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.DisplayVideoGateway#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsVideoGateway](set-csvideogateway.md)

