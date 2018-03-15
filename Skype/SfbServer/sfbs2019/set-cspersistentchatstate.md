---
title: "Set-CsPersistentChatState"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9b82fe41-214d-4376-b026-bb1434d04118
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsPersistentChatState
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies the state of a Persistent Chat service pool. Persistent Chat pools can be in one of two states: Normal, in which the pool uses its primary databases; or FailedOver, in which the pool uses the backup databases defined in the topology. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsPersistentChatState [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 sets the pool state for the Persistent Chat server atl-gc-001.litwareinc.com to FailedOver.
  
```
Set-CsPersistentChatState -Identity "PersistentChatServer:atl-gc-001.litwareinc.com" -PoolState "FailedOver"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The [Get-CsPersistentChatState](get-cspersistentchatstate.md) cmdlet returns the state of one or more Persistent Chat pools. Persistent Chat pools can be in either the Normal state (in which the pool uses its primary databases) or in a FailedOver state, in which the pool uses its backup databases. You can use the **Set-CsPersistentChatState** cmdlet to change the state of a Persistent Chat pool; when you change the state of the pool, Lync Server 2013 will automatically change the state of each individual server in the pool. To change the state of an individual chat server, use the [Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md) cmdlet. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsPersistentChatState"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsPersistentChatState** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the Persistent Chat pool where the new service state will be applied. For example:  <br/> -Identity PersistentChatServer:atl-persistentchat-001.litwareinc.com  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _PoolState_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PoolState  <br/> |Current state of the Persistent Chat pool. Valid values are:  <br/> \* Normal  <br/> \* FailedOver  <br/> The default value is Normal.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsPersistentChatState** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatstate object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPersistentChatState** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatState object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatState](get-cspersistentchatstate.md)
  
[Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md)

