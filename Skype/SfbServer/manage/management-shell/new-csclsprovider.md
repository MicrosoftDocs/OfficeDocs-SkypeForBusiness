---
title: "New-CsClsProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9b0a90c1-27ab-49c8-88f2-a381cf14625e
description: "Creates a new centralized logging trace provider. Trace providers are application components that generate trace messages or trace events useful in troubleshooting problems with Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013."
---

# New-CsClsProvider
 
Creates a new centralized logging trace provider. Trace providers are application components that generate trace messages or trace events useful in troubleshooting problems with Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsClsProvider -Flags <String> -Level <Placeholder | Fatal | Error | Warning | Info | Verbose | Debug | All> -Name <String> -Type <WPP | EventLog | IISLog> [-Guid <String>] [-Role <String>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 create a new centralized logging scenario provider and then add that provider to the WAC scenario configured for the Redmond site. To do this, the first command in the example uses the **New-CsClsProvider** cmdlet to create a new provider with the name WebInfrastructure; this new provider is stored in a variable named $provider. The second command in the example then adds this new provider to the scenario site:Redmond/WAC. Because the command uses the syntax @{Add=$provider} the new provider will be added to the WAC scenario in addition to any other providers already configured for that
  
```
$provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"

Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Add=$provider}
```

### Example 2

The command shown in Example 2 is a variation of the command shown in Example 1. In Example 2, however, the new provider will replace any (and all) the existing providers configured for the WAC scenario. This is done by using the syntax @{Replace=$provider}.
  
```
$provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"

Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Replace=$provider}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
Each centralized logging scenario requires one or more trace providers to generate the messages and events that are logged in the trace logs. Skype for Business Server 2015 ships with a large number of these providers predefined for you. The **New-CsClsProvider** cmdlet provides a way for developers who are Skype for Business Server 2015 to take advantage of centralized logging for custom new application/component.
  
It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet.
  
Skype for Business Server Control Panel: The functions carried out by the **New-CsClsProvider** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Flags_ <br/> |Required  <br/> |System.String  <br/> |Specifies individual protocols and subcomponents involved in the trace. For example, the SipStack provider includes the following flags: TF_COMPONENT, TF_RTCHTTP, TF_CONNECTION, TF_DIAG.  <br/> Most providers are configured to use all available flags.  <br/> |
| _Level_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLoggingConfig.ProviderLevel  <br/> |Tracing level for events recorded by the provider: Allowed values are:  <br/> \* Fatal  <br/> \* Error  <br/> \* Warning  <br/> \* Info  <br/> \* Verbose  <br/> \* Debug  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Unique name for the new provider.  <br/> |
| _Type_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLoggingConfig.ProviderType  <br/> |Type of tracing used by the provider. Allowed values are:  <br/> WPP (Windows software trace preprocessor)  <br/> EventLog  <br/> IISLog  <br/> |
| _Guid_ <br/> |Optional  <br/> |System.String  <br/> |Globally unique identifier assigned to the provider.  <br/> |
| _Role_ <br/> |Optional  <br/> |System.String  <br/> |Skype for Business Server 2015 server role for the provider. For example, FE for Front End server or Edge for Edge Server.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The New-CsClsProvider cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The New-CsClsProvider cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Provider object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsClsScenario](new-csclsscenario.md)
  
[Set-CsClsScenario](set-csclsscenario.md)

