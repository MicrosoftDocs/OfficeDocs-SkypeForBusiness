---
title: "Get-CsClsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5fef2e35-e23c-453d-97e5-cb9c4e7bfef7
description: "Returns information about the centralized logging configuration settings in use in the organization. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsClsConfiguration
 
Returns information about the centralized logging configuration settings in use in the organization. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsClsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the centralized logging configuration settings currently in use in the organization.
  
```
Get-CsClsConfiguration
```

### Example 2

In Example 2, information is returned for a single collection of centralized logging configuration settings: the collection applied to the Redmond site.
  
```
Get-CsClsConfiguration -Identity "site:Redmond"
```

### Example 3

Example 3 shows detailed information for the centralized logging scenarios available to the Redmond site. In order to do this, the command first retrieves all the centralized logging property values for the Redmond site. Those property values are then piped to the Select-Object cmdlet, which uses the ExpandProperty parameter to "expand" the values found in the Scenarios property. When you expand a property you simply display all the information stored in that property in an easy-to-read fashion.
  
```
Get-CsClsConfiguration -Identity "site:Redmond" | Select-Object -ExpandProperty Scenarios
```

### Example 4

In Example 4, information is returned for all the centralizing logging configuration settings where the ETL file rollover interval is greater than 1 hour. To carry out this task, the command first calls the **Get-CsClsConfiguration** cmdlet without any parameters; this returns a collection of all the centralized logging configuration settings in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the EtlFileRolloverMinutes property is greater than (-gt) 60 minutes.
  
```
Get-CsClsConfiguration | Where-Object {$_.EtlFileRolloverMinutes -gt 60}
```

### Example 5

The command shown in Example 5 is similar to the command shown in Example 4; in this case, however, information is returned only for those centralized logging configuration settings that include a "HybridVoice" scenario. To do this, the command first uses the **Get-CsClsConfiguration** cmdlet to return a collection of all the centralized logging configuration settings. That collection is then piped to the **Where-Object** cmdlet, which selects only those settings that have at least one scenario where the Name property includes (-match) the string value "HybridVoice".
  
```
Get-CsClsConfiguration | Where-Object {$_.Scenarios.Name -match "HybridVoice"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet.
  
Centralized logging is managed by using collections of centralized logging service configuration settings. When you install Skype for Business Server 2015, you install a global set of these configuration settings; in addition, administrators can add custom settings collections at the site scope. The **Get-CsClsConfiguration** cmdlet enables administrators to return information about all the central logging configuration settings currently in use in the organization.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsClsConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection (or collections) of centralized logging configuration settings. For example, to return a collection of all the settings configured at the site scope, use this syntax:  <br/>  `-Filter "site:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the unique identifier for the collection of centralized logging configuration settings you want to return. To refer to the global settings use this syntax:  <br/>  `-Identity "global"` <br/> To refer to a collection configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, then include the Filter parameter instead.  <br/> If this parameter is not specified, then the **Get-CsClsConfiguration** cmdlet returns a collection of all the centralized logging configuration settings in use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the centralized logging configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsClsConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsClsConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.CentralizedLoggingConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsClsConfiguration](new-csclsconfiguration.md)
  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)
  
[Set-CsClsConfiguration](set-csclsconfiguration.md)

