---
title: Remove-CsClsScenario
ms.prod: SKYPEFORBUSINESS
ms.assetid: 747bd4d6-797e-4088-9303-6ceb65f66183
---


# Remove-CsClsScenario
[]
Removes the specified centralized logging configuration scenario. A scenario represents a particular Skype for Business Server 2015 component or situation (such as IM and presence) that administrators can enable or disable for tracing. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Remove-CsClsScenario -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 removes the WAC scenario from the global collection of centralized logging configuration settings.
  
    
    

```

Remove-CsClsScenario -Identity "site:Redmond/WAC"
```


### Example 2

In Example 2, the HybridVoice scenario is removed from all the centralized logging configuration settings in use in the organization. To do this, the **Get-CsClsScenario** cmdlet is first called without any parameters in order to return a collection of all the available scenarios. That collection is then piped to the Where-Object cmdlet, which picks out all the scenarios where the Name property is equal to (-eq) HybridVoice. The HybridVoice scenarios are then piped to, and deleted by, the **Remove-CsClsScenario** cmdlet.
  
    
    

```
Get-CsClsScenario | Where-Object {$_.Name -eq "HybridVoice" | Remove-CsClsScenario
```


## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the  [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
    
    
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
    
    
The **Remove-CsClsScenario** cmdlet provides a way for you to remove scenarios from your centralized logging configuration settings.
  
    
    
 **Skype for Business Server Control Panel **: The functions carried out by the **Remove-CsClsScenario** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the scenario to be removed. A scenario consists of two parts: the scope where the scenario is configured (that is, the collection of centralized logging configuration settings where the scenario can be found) and the scenario name. For example:  <br/>  `-Identity "site:Redmond/AddressBook"` <br/> You can also specify just the scenario scope; for example:  <br/>  `-Identity "site:Redmond"` <br/> If you do that, however, the entire collection of centralized logging configuration settings for the specified scope will be removed, and not just the scenarios.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Remove-CsClsScenario** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario#Decorated object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsClsScenario** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario#Decorated object.
  
    
    

