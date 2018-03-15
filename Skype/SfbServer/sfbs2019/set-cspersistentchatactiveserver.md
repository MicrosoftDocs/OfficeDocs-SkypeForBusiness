---
title: "Set-CsPersistentChatActiveServer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 88c0af42-cb47-4c34-bf54-9c134dcbb843
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsPersistentChatActiveServer
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Manages the list of active Persistent Chat servers. An active server is Persistent Chat server (in a specified Persistent Chat service pool) that is fully operational and can accept new client connections. Servers in the pool that have not been marked as active servers might be operational, but are currently unable to accept new client connections. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsPersistentChatActiveServer -ActiveServers <PSListModifier> <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 adds the server atl-gc-001.litwareinc.com to the collection of active Persistent Chat servers.
  
```
Set-CsPersistentChatActiveServer -Identity "global" -ActiveServers @{Add="atl-gc-001.litwareinc.com"}
```

### Example 2

Example 2 removes the server atl-gc-001.litwareinc.com from the collection of active Persistent Chat servers.
  
```
Set-CsPersistentChatActiveServer -Identity "global" -ActiveServers @{Remove="atl-gc-001.litwareinc.com"}
```

### Example 3

The command shown in Example 3 removes all the active Persistent Chat servers. Removing all the active servers is typically done in a failback or failover scenario.
  
```
Set-CsPersistentChatActiveServer -Identity "global" -ActiveServers $Null
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Set-CsPersistentChatActiveServer** cmdlet allows administrators to essentially enable or disable the Persistent Chat service on one or more servers in a Persistent Chat pool. Servers that appear on the active servers list are able to accept new client connections. Servers that do not appear on the list are not able to accept new client connections. (However, the server will continue to any client connections that were made before the server was removed from the list.) To enable the Persistent Chat service on a Persistent Chat server, add that server to the active server list. To disable the service, remove the server from the active server list. 
  
To enable/disable the Persistent Chat service on all the servers in a pool, use the **Set-CsPersistentChatState** cmdlet. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsPersistentChatActiveServer"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsPersistentChatActiveServer** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ActiveServers_ <br/> |Required  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of fully-qualified domain names representing the active Persistent Chat servers.  <br/> |
| _Swap_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, swaps the active state for all the Persistent Chat servers in the specified pool: active servers will be marked as inactive, and inactive servers will be marked as active.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique Identity for the collection of active servers. Note that you can only have a single, global collection of Persistent Chat servers.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Set-CsPersistentChatActiveServer** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsPersistentChatState](set-cspersistentchatstate.md)

