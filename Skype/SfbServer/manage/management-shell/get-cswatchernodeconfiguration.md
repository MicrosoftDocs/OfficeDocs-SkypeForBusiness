---
title: "Get-CsWatcherNodeConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 4/4/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 20dae017-375c-4361-8d65-b56f4c09b375
description: "Returns information about the watcher node configuration settings in use in your organization. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Skype for Business Server 2015 synthetic transactions to verify that Skype for Business Server 2015 components are working as expected. The watcher node configuration settings let you know which pools have been associated with a watcher node. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsWatcherNodeConfiguration
[]
Returns information about the watcher node configuration settings in use in your organization. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Skype for Business Server 2015 synthetic transactions to verify that Skype for Business Server 2015 components are working as expected. The watcher node configuration settings let you know which pools have been associated with a watcher node. This cmdlet was introduced in Lync Server 2013.
  
> [!NOTE]
> This command must be run on the dedicated Trusted Application Server previously configured as a watcher node using the **New-CsWatcherNodeConfiguration** command otherwise the output will display a null result.
  
```
Get-CsWatcherNodeConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the watcher nodes currently configured for use in the organization.
  
```
Get-CsWatcherNodeConfiguration
```

### Example 2

In Example 2, information is returned for the watcher node associated with the pool.
  
```
Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com"
```

### Example 3

The command shown in Example 3 returns information about all the watcher nodes where the test users include the user with the SIP address sip:kenmyer@litwareinc.com. To do this, the command first uses the **Get-CsWatcherNodeConfiguration** cmdlet to return a collection of all the watcher nodes in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those nodes where the TestUsers property contains the SIP address sip:kenmyer@litwareinc.com.
  
```
Get-CsWatcherNodeConfiguration | Where-Object {$_.TestUsers -contains "sip:kenmyer@litwareinc.com"}
```

### Example 4

In Example 4, information is returned for all the watcher nodes that include the PSTN test type. To carry out this task, the command first calls the **Get-CsWatcherNodeConfiguration** cmdlet in order to return a collection of all the watcher nodes in the organization. That collection is then piped to the **Where-Object** cmdlet, which selects only those watcher nodes where the ExtendedTests property includes (-matches) the string value "TestType=PSTN".
  
```
Get-CsWatcherNodeConfiguration | Where-Object {$_.ExtendedTests -match "TestType=PSTN"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

If you are using Microsoft System Center Operations Manager to monitor Skype for Business Server 2015 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions in order to verify that Skype for Business Server 2015 is working as expected. Watcher nodes are assigned to pools, and are managed using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes; the only difference is that any synthetic transactions you want to run will need to be invoked manually rather than automatically invoked by Operations Manager.
  
The **Get-CsWatcherNodeConfiguration** cmdlet returns information about all the watcher nodes that have been configured for use in your organization.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsWatcherNodeConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return one or more watcher nodes. For example, to return all of the watcher nodes for the domain litwareinc.com use this syntax:  <br/>  `-Filter "*.litwareinc.com"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name of the pool that the watcher node has been assigned to. For example:  <br/>  `-Identity "atl-cs-001.litwareinc.com"` <br/> If this parameter is not specified then the **Get-CsWatcherNodeConfiguration** cmdlet will return information about all the watcher nodes configured for use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the watcher node configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsWatcherNodeConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsWatcherNodeConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)
  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)
  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)
  
[Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

