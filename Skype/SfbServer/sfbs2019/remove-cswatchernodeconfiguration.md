---
title: "Remove-CsWatcherNodeConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 599c6d58-da3d-4f0b-bc1f-22ac3e33ec7f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsWatcherNodeConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Removes an existing collection of watcher node configuration settings. Watcher nodes are computers that periodically use System Center Operations Manager and Lync Server 2013 synthetic transactions to verify that Lync Server components are working as expected. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsWatcherNodeConfiguration -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the watcher node configuration settings applied to the pool atl-cs-001.litwareinc.com.
  
```
Remove-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com"
```

### Example 2

Example 2 removes all the watcher nodes configured for use in the organization. To do this, the command first uses the **Get-CsWatcherNodeConfiguration** cmdlet to return a collection of all the watcher nodes. This collection is then piped to the **Remove-CsWatcherNodeConfiguration** cmdlet, which removes each watcher node in the collection. That effectively removes each watcher node in the organization. 
  
```
Get-CsWatcherNodeConfiguration | Remove-CsWatcherNodeConfiguration
```

### Example 3

In Example 3, all the watcher nodes that include the user sip:kenmyer@litwareinc.com as a test user are removed. To carry out this task, the command first calls the **Get-CsWatcherNodeConfiguration** cmdlet in order to return a collection of all the watcher nodes currently in use. This collection is then piped to the Where-Object cmdlet, which picks out only those settings where the TestUsers property includes (-contains) the user sip:kenmyer@litwareinc.com. That filtered collection is then piped to the **Remove-CsWatcherNodeConfiguration** cmdlet, which removes each item in the filtered collection. 
  
```
Get-CsWatcherNodeConfiguration | Where-Object {$_.TestUsers -contains "sip:kenmyer@litwareinc.com"} | Remove-CsWatcherNodeConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

If you are using Microsoft System Center Operations Manager to monitor Lync Server 2013 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions in order to verify that Lync Server is working as expected. Watcher nodes are assigned to pools, and are managed using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes; the only difference is that any synthetic transactions you want to run will need to be invoked manually rather than automatically invoked by Operations Manager. 
  
If you later decide to decommission a watcher node you can do so by using the **Remove-CsWatcherNodeConfiguration** cmdlet. Alternatively, you can temporarily disable (and then later re-enable) a watcher node by using the [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md) cmdlet. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsWatcherNodeConfiguration"}
  
 **Lync Server Control Panel:** The functions carried out by the **Remove-CsWatcherNodeConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name of the pool that has been assigned the watcher node being deleted. For example:  <br/> -Identity "atl-cs-001.litwareinc.com"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsWatcherNodeConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool#Decorated object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the Remove-CsWatcherNodeConfiguration cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)
  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)
  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)
  
[Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

