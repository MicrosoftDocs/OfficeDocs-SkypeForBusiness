---
title: "Remove-CsAVEdgeConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 98bceec5-ed9d-4574-b6bf-f51e0f414ca7
description: "Enables you to remove an existing collection of configuration settings applied to computers running the Access Edge service (these computers are also known as A/V Edge servers). An A/V Edge server enables internal users to share audio and video data with external users (that is, users who are not logged on to your internal network). This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsAVEdgeConfiguration
[]
Enables you to remove an existing collection of configuration settings applied to computers running the Access Edge service (these computers are also known as A/V Edge servers). An A/V Edge server enables internal users to share audio and video data with external users (that is, users who are not logged on to your internal network). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsAVEdgeConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 removes the A/V Edge configuration settings that have the Identity site:Redmond. After the settings are removed, A/V Edge servers in the Redmond site will be governed by the global configuration settings.
  
```
Remove-CsAVEdgeConfiguration -Identity site:Redmond
```

### EXAMPLE 2

In Example 2, all of the A/V Edge configuration settings that have been applied at the service scope are removed. To do this, the command first calls the **Get-CsAVEdgeConfiguration** cmdlet along with the Filter parameter; the filter value "service:*" ensures that only settings configured at the service scope are returned. This filtered collection is then piped to the **Remove-CsAVEdgeConfiguration** cmdlet, which deletes each item in the collection.
  
```
Get-CsAVEdgeConfiguration -Filter "service:*" | Remove-CsAVEdgeConfiguration
```

### EXAMPLE 3

The command shown in Example 3 deletes all of the A/V Edge configuration settings where the value of the MaxBandwidthPerUserKB property is less than 5,000 kilobits per second. To carry out this task, the command first uses the **Get-CsAVEdgeConfiguration** cmdlet without any additional parameters in order to return a collection of all the A/V Edge settings currently in use in the organization. This collection is piped to the **Where-Object** cmdlet, which selects only those settings where the MaxBandwidthPerUserKB property is less than 5000. The filtered collection is then piped to the **Remove-CsAVEdgeConfiguration** cmdlet, which deletes each item in that collection.
  
```
Get-CsAVEdgeConfiguration | Where-Object {$_.MaxBandwidthPerUserKB -lt 5000} | Remove-CsAVEdgeConfiguration
```

## Detailed Description

An A/V Edge server provides a way for audio and video traffic to be exchanged across an organization's firewall. Among other things, this enables users to use Skype for Business Server 2015 across the Internet, and then exchange audio and video data with users who have logged onto the system from inside the firewall. Edge Server configuration settings can be assigned at the global scope, the site scope, and the service scope. The A/V Edge configuration settings enable administrators to do such things as manage the amount of time that user authentication is valid before it must be renewed, and to limit the amount of bandwidth that can be used by a single user or a single port.
  
The **Remove-CsAVEdgeConfiguration** cmdlet enables you to delete A/V Edge configuration settings that have been applied to either the site or the service scope. The cmdlet can also be run against the global settings; however, those global settings will not be deleted. Instead, the properties contained within the global collection will all be reset to their default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of A/V Edge configuration settings to be removed. To "remove" the global collection, use the following syntax:  `-Identity global`. (As noted previously, the global settings cannot be removed; the properties can only be reset to their default values.) To remove a site collection, use syntax similar to this:  `-Identity site:Redmond`. Settings configured at the service scope should be referred to using syntax similar to this:  <br/>  `-Identity service:EdgeServer:atl-cs-001.litwareinc.com` <br/> You cannot use wildcards when specifying a policy Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings object. The **Remove-CsAVEdgeConfiguration** cmdlet accepts pipelined input of media relay settings objects. These objects retrieved by running the **Get-CsAVEdgeConfiguration** cmdlet.
  
## Return Types

The **Remove-CsAVEdgeConfiguration** cmdlet does not return a value or object. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings object.
  
## See also

#### 

[Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)
  
[New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)
  
[Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

