---
title: "New-CsClsScenario"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 79ff443f-82ff-4b49-bde5-98e51e8b1ed2
description: "Creates a new centralized logging configuration scenario. A scenario represents a particular Skype for Business Server 2015 component or situation (such as IM and presence) that administrators can enable or disable for tracing. This cmdlet was introduced in Lync Server 2013."
---

# New-CsClsScenario
 
Creates a new centralized logging configuration scenario. A scenario represents a particular Skype for Business Server 2015 component or situation (such as IM and presence) that administrators can enable or disable for tracing. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsClsScenario -Identity <XdsIdentity> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 create a new centralized logging scenario with the Identity global/RedmondHybridVoice. In order to carry out this task, the first command in the example uses the **New-CsClsProvider** cmdlet to create a provider to be assigned to the scenario; this new provider is stored in the variable $provider.
  
After the description and the provider have been created, the final command in the example calls the **New-CsClsScenario** cmdlet in order to create the scenario, using the data stored in $provider to assign a value to the Provider property.
  
```
$provider = New-CsClsProvider -Name "RedmondHybridVoice" -Type "WPP" -Level "Info" -Flags "All"

New-CsClsScenario -Identity "global/RedmondHybridVoice"-Provider $provider

```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
Custom scenarios can be created by using the New-CsClsScenario cmdlet and then adding the new scenario to a collection of centralized logging configuration settings.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **New-CsClsScenario** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new scenario. A scenario consists of two parts: the scope where the scenario is configured (that is, the collection of centralized logging configuration settings where the scenario can be found) and the scenario name. For example:  <br/>  `-Identity "site:Redmond/AddressBook"` <br/> If you use the Identity parameter then you cannot use either the name parameter or the Parent parameter in that same command.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Unique name for the new scenario. For example:  <br/>  `-Name "RedmondHybridVoice"` <br/> If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Scope of the centralized logging configuration settings where the new scenario will be located. For example, to add the new scenario to the global settings, use this syntax:  <br/>  `-Parent "global"` <br/> You can return identities for all your centralizing logging "parents" by using this command:  <br/>  `Get-CsClsConfiguration | Select-Object Identity` <br/> If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _Provider_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Logging provider for the scenario. New providers must be created using the New-CsClsProvider cmdlet. For example:  <br/>  `$provider = New-CsClsProvider -Name "UserServices" -Type "WPP" -Level "Info" -Flags "All"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsClsScenario** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsClsScenario** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario#Decorated object.
  

