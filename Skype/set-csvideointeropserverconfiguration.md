---
title: Set-CsVideoInteropServerConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: dd43e323-a37c-4006-8aac-61e5b119b432
---


# Set-CsVideoInteropServerConfiguration
[]
Use the **Set-CsVideoInteropServerConfiguration** cmdlet to modify an existing collection of Video Interop Server (VIS) configuration settings. VIS settings are scoped to appropriate VIS instances, and will govern the behavior of those instances. The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool.
  
    
    

This cmdlet was introduced in Skype for Business Server 2015.
```

Set-CsVideoInteropServerConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

This example disables enhanced video experience for the collection of VIS settings assigned to the Redmond site.
  
    
    

```

Set-CsVideoInteropServerConfiguration -Identity "site:Redmond" -EnableEnhancedVideoExperience $False
```


### Example 2

This example disables all enhanced video experience settings in the organization. The command uses the **Get-CsVideoInteropServerConfiguration** cmdlet to return a collection of all the available VIS settings. That collection is piped to the **Set-CsVideoInteropServerConfiguration** cmdlet, which disables the enhanced video experience for each item in the collection.
  
    
    

```
Get-CsVideoInteropServerConfiguration | Set-CsVideoInteropServerConfiguration -EnableEnhancedVideoExperience $False
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool. 
  
    
    
To enable the Video Interop Server (VIS) you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and external video devices such as an internal Skype for Business endpoint receiving video from an external PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a VIS use a Session Initiation Protocol (SIP) trunk to connect video calls between external VTCs and internal endpoints. 
  
    
    
You can manage the Video Interop Server (VIS) by using VIS configuration settings and the **CsVideoInteropServerConfiguration** cmdlets. These settings are used to enable or disable the enhanced video experience (in which a single video stream is converted to multiple streams in order to accommodate the needs of devices that use different frame rates or video resolutions).
  
    
    
By default, Skype for Business Server 2015 ships with a single, global collection of video interop configuration settings. However, administrators can use the **New-CsVideoInteropServerConfiguration** cmdlet to create additional settings at the site or the service scope (for the Video Interop server service only.) Both the global collection of settings and any custom settings that you create can be modified by using the **Set-CsVideoInteropServerConfiguration** cmdlet.
  
    
    
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
    
    



```

Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableEnhancedVideoExperience_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) the single video stream coming from a third party video system will be converted to multiple streams in order to meet the needs of devices using different video resolutions or frame rates .The default value is True ($True).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the video server configuration settings to be modified. To modify the global settings, use this syntax:  <br/>  `-Identity "global"` <br/> To manage settings at the site scope use syntax like the following:  <br/>  `-Identity "site:Redmond"` <br/> To modify settings configured at the service scope, use syntax similar to this:  <br/>  `-Identity "service:VideoInteropServer:atl-edge-001.litwareinc.com"` <br/> If this parameter is not included, the **Set-CsVideoInteropServerConfiguration** cmdlet will automatically modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Set-CsVideoInteropServerConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoInteropServer.VideoInteropServerConfiguration object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. The **Set-CsVideoInteropServerConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoInteropServer.VideoInteropServerConfiguration object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsVideoInteropServerConfiguration](get-csvideointeropserverconfiguration.md)
  
    
    
 [New-CsVideoInteropServerConfiguration](new-csvideointeropserverconfiguration.md)
  
    
    
 [Remove-CsVideoInteropServerConfiguration](remove-csvideointeropserverconfiguration.md)
