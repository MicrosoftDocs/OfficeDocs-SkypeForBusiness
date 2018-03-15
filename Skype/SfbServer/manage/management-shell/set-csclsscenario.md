---
title: "Set-CsClsScenario"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 00de6571-a1ad-4f69-a21e-8a9ae115882f
description: "Enables you to modify a centralized logging configuration scenario. A scenario represents a particular Skype for Business Server 2015 component or situation (such as IM and presence) that administrators can enable or disable for tracing. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsClsScenario
 
Enables you to modify a centralized logging configuration scenario. A scenario represents a particular Skype for Business Server 2015 component or situation (such as IM and presence) that administrators can enable or disable for tracing. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsClsScenario [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 create a new centralized logging scenario provider and then add that provider to the WAC scenario configured for the Redmond site. To do this, the first command in the example uses the **New-CsClsProvider** cmdlet to create a new provider with the name WebInfrastructure; this new provider is stored in a variable named $provider. The second command in the example then adds this new provider to the scenario site:Redmond/WAC. Because the command uses the syntax `@{Add=$provider}` the new provider will be added to the WAC scenario in addition to any other providers already configured for that
  
```
$provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"

Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Add=$provider}
```

### Example 2

The command shown in Example 2 is a variation of the command shown in Example 1. In Example 2, however, the new provider will replace any (and all) the existing providers configured for the WAC scenario. This is done by using the syntax  `@{Replace=$provider}`.
  
```
$provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"

Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Replace=$provider}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
Custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet and then adding the new scenario to a collection of centralized logging configuration settings. Any of your scenarios can then be modified by using the **Set-CsClsScenario** cmdlet.
  
 **Skype for Business Server Control Panel **: The functions carried out by the **Set-CsClsScenario** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the scenario to be modified. A scenario consists of two parts: the scope where the scenario is configured (that is, the collection of centralized logging configuration settings where the scenario can be found) and the scenario name. For example:  <br/>  `-Identity "site:Redmond/AddressBook"` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object rather than set individual parameter values.  <br/> |
| _Provider_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Logging provider for the scenario. New providers must be created using the **New-CsClsProvider** cmdlet. For example: <br/>  `$provider = New-CsClsProvider -Name "UserServices" -Type "WPP" -Level "Info" -Flags "All"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsClsScenario** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsClsScenario** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario#Decorated object.
  

