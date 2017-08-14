---
title: Get-CsVideoInteropServerConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 72cdb754-76cb-4738-bae2-245d1619ef30
---


# Get-CsVideoInteropServerConfiguration
[]
Use the **Get-CsVideoInteropServerConfiguration** cmdlet to return information about Video Interop Server (VIS) configuration settings. VIS configuration settings are scoped to appropriate VIS instances, and will govern the behavior of those instances. The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool.
  
    
    

This cmdlet was introduced in Skype for Business Server 2015.
```

Get-CsVideoInteropServerConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

This example returns information about all the VIS configuration settings in the organization.
  
    
    

```

Get-CsVideoInteropServerConfiguration
```


### Example 2

This example returns information for the collection of VIS configurations that are scoped to the Redmond site.
  
    
    

```
Get-CsVideoInteropServerConfiguration -Identity "site:Redmond"
```


### Example 3

This example returns all the VIS collections configured at the site scope by including the  _Filter_ value "site:*".
  
    
    

```
Get-CsVideoInteropServerConfiguration -Filter "site:*"
```


### Example 4

This example returns information about all the VIS configurations where the enhanced video experience has been enabled. First, all the VIS configurations are returned by using **Get-CsVideoInteropServerConfiguration** to return a collection of all the available settings. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the _EnableEnhancedVideoExperience_ value is equal to True ($True).
  
    
    

```
Get-CsVideoInteropServerConfiguration | Where-Object {$_.EnableEnhancedVideoExperience -eq $True}
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool. 
  
    
    
To enable the Video Interop Server (VIS) you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and external video devices such as an internal Skype for Business endpoint receiving video from an external PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a VIS use a Session Initiation Protocol (SIP) trunk to connect video calls between external VTCs and internal endpoints. 
  
    
    
You can manage the Video Interop Server (VIS) by using VIS configuration settings and the **CsVideoInteropServerConfiguration** cmdlets. These settings are used to enable or disable the enhanced video experience (in which a single video stream is converted to multiple streams in order to accommodate the needs of devices that use different frame rates or video resolutions).
  
    
    
By default, Skype for Business Server ships with a single, global collection of Video Interop Server configuration settings. You can use the **New-CsVideoInteropServerConfiguration** cmdlet to create additional settings at the site or the service scope (for the VIS service only.)
  
    
    
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
    
    



```

Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return one or more collections of VIS configuration settings. For example, to return all the settings that have been configured at the site scope use the following syntax:  <br/>  `-Filter "site:*"` <br/> The  _Filter_ and the _Identity_ parameters are mutually exclusive. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity assigned to the VIS configuration when it was created. VIS settings can be configured at the global, site, or service scope (for the VideoInteropServer service only). To refer to the global instance, use this syntax:  <br/>  `-Identity "global"` <br/> Use this syntax to refer to a collection at the site scope:  <br/>  `-Identity "site:Redmond"` <br/> Wildcard characters such as the asterisk (*) cannot be used with the Identity parameter. To do a wildcard search for policies, use the Filter parameter instead.  <br/> If neither the  _Identity_ nor the _Filter_ parameter is specified, then the **Get-CsVideoInteropServerConfiguration** cmdlet returns all the VIS configurations in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the VIS configuration from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsVideoInteropServerConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsVideoInteropServerConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoInteropServer.VideoInteropServerConfiguration object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [New-CsVideoInteropServerConfiguration](new-csvideointeropserverconfiguration.md)
  
    
    
 [Remove-CsVideoInteropServerConfiguration](remove-csvideointeropserverconfiguration.md)
  
    
    
 [Set-CsVideoInteropServerConfiguration](set-csvideointeropserverconfiguration.md)
