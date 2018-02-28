---
title: "Get-CsDeviceUpdateRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 14291802-a833-4f5f-8b4b-a465de6f7f2b
description: "Returns information about the device update rules configured for use in your organization. Device update rules are used to associate firmware updates with devices that run Skype for Business Phone Edition. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsDeviceUpdateRule
[]
Returns information about the device update rules configured for use in your organization. Device update rules are used to associate firmware updates with devices that run Skype for Business Phone Edition. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsDeviceUpdateRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command in Example 1 returns information about all the device update rules that have been applied in your organization. Calling the **Get-CsDeviceUpdateRule** cmdlet without any additional parameters always returns the complete collection of device update rules.
  
```
Get-CsDeviceUpdateRule
```

### EXAMPLE 2

The command shown in Example 2 returns information about the device update rule with the Identity "WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9".
  
```
Get-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9
```

### EXAMPLE 3

Example 3 returns information about all the device update rules configured for the service WebServer:atl-cs-001.litwareinc.com. To accomplish this task, the Filter parameter is used along with the filter value "WebServer:atl-cs-001.litwareinc.com\*". That filter limits the returned data to device update rules that have an Identity that begins with the string value "service:WebServer:atl-cs-001.litwareinc.com."
  
```
Get-CsDeviceUpdateRule -Filter service:WebServer:atl-cs-001.litwareinc.com*
```

### EXAMPLE 4

Example 4 returns all the device update rules where the Brand property is equal to "LG-Nortel". To do this, the **Get-CsDeviceUpdateRule** cmdlet is called in order to return a collection of all the device update rules in the organization. That collection is then piped to the **Where-Object** cmdlet, which selects only those rules where the Brand is equal to "LG-Nortel".
  
```
Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "LG-Nortel"}
```

### EXAMPLE 5

Example 5 returns a collection of all the device update rules that have not been approved. This is done by using the **Get-CsDeviceUpdateRules** cmdlet to return a collection of all the rules and then piping that collection to the **Where-Object** cmdlet. In turn, the **Where-Object** cmdlet selects only those rules where the Approved property is equal to a null value. If the Approved property is null, it means that these rules are not approved.
  
```
Get-CsDeviceUpdateRule | Where-Object {$_.ApprovedVersion -eq $Null}
```

### EXAMPLE 6

This command returns a collection of all the device update rules that meet two criteria: the rule has been approved and the rule relates to LG-Nortel devices. To accomplish this task, the **Get-CsDeviceUpdateRule** cmdlet is first called to return a collection of all the device update rules in the organization. That collection is then piped to the **Where-Object** cmdlet, which filters the collection on two criteria: the Approved property must not be null (that is, this property must have a value of some kind); and the Brand must be equal to "LG-Nortel".
  
```
Get-CsDeviceUpdateRule | Where-Object {$_.ApprovedVersion -ne $Null -and $_.Brand -eq "LG-Nortel"}
```

## Detailed Description

Skype for Business Server 2015 uses device update rules as a way to provide firmware updates to devices that run Skype for Business Phone Edition. Periodically, administrators upload a set of device update rules to Skype for Business Server 2015; after those rules have been tested and approved, they are automatically downloaded and applied to the appropriate devices as those devices connect to the system. By default devices check for new update rules each time they turn on and connect to Skype for Business Server 2015. Devices also check for updates every 24 hours after that initial sign on.
  
Device update rules can be imported (and applied to) the Web Services service. The **Get-CsDeviceUpdateRule** cmdlet enables you to return information about the device update rules that have been imported for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Identity of a device update rule or set of rules. For example, to return all the device update rules for WebServer:atl-cs-001.litwareinc.com use this filter value: "service:WebServer:atl-cs-001.litwareinc.com\*".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the device update rule. The Identity of a device update rule is composed of two parts: the service scope where the rule has been applied (for example, service:WebServer:atl-cs-001.litwareinc.com) and the globally unique identifier (GUID) that was pre-assigned to the rule (for example, d5ce3c10-2588-420a-82ac-dc2d9b1222ff9). Based on this, the Identity for a given device update rule will look something like this: "service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 ".  <br/> Wildcards are not allowed when specifying an Identity. Use the Filter parameter if you want to use wildcards when specifying a rule.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the device update rule data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsDeviceUpdateRule** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsDeviceUpdateRule** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdate.Rule object.
  
## See also

#### 

[Approve-CsDeviceUpdateRule](approve-csdeviceupdaterule.md)
  
[Remove-CsDeviceUpdateRule](remove-csdeviceupdaterule.md)
  
[Reset-CsDeviceUpdateRule](reset-csdeviceupdaterule.md)
  
[Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md)

