---
title: Get-CsTelemetryConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 3342e0f2-8892-4dfc-9ff3-587444159289
---



# Get-CsTelemetryConfiguration
[]
Use the **Get-CsTelemetryConfiguration** cmdlet to return the settings on existing telemetry configurations.
  
    
    

Telemetry returns a small set of Skype for Business operational data to Microsoft for quality tracking and product improvement. The data includes sign-in information, meeting joins, and other activity data.
```

Get-CsTelemetryConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

This example returns the settings for the configuration scoped to the Redmond site.
  
    
    

```

Get-CsTelemetryConfiguration -Identity Site:Redmond
```


## Detailed Description
<a name="DetailedDescription"> </a>


> [!NOTE]
> For privacy information, see the  [Skype for Business Privacy Statement](http://go.microsoft.com/fwlink/?LinkID=517480&amp;clcid=0x409). 
  
    
    


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return one or more collections of telemetry configuration settings. For example, to return all the settings that have been configured at the site scope use the following syntax: `-Filter "site:*"`. The  _Filter_ and the _Identity_ parameters are mutually exclusive. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier that includes the scope of the telemetry configuration. Telemetry configurations can be scoped at the Global, Site, or Service level. For example, "site:Redmond" (for site). The format of the service scope is "Service:<Identity>", where identity is derived from the topology. You can use the following cmds to identify the relevant services.  <br/> ```Get-CsService -WebServer | fl IdentityGet-CsService -PoolFqdn <pool> | fl Identity```The first command will give you all of the WebServices in the topology, regardless of the pool. The second will give you all of the services on the pool, regardless of their role. You can combine the two commands to zero in on a single role in a single pool.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.SignInTelemetry.SignInTelemetryConfiguration
  
    
    
