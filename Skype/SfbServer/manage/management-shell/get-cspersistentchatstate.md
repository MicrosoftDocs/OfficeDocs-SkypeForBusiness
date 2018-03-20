---
title: "Get-CsPersistentChatState"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 598086c9-a8c7-4b81-84ba-1807f1183024
description: "Returns the state of one or more Persistent Chat service pools. Persistent Chat pools can be in one of two states: Normal, in which the pool uses its primary databases; or FailedOver, in which the pool uses the backup databases defined in the topology. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsPersistentChatState
 
Returns the state of one or more Persistent Chat service pools. Persistent Chat pools can be in one of two states: Normal, in which the pool uses its primary databases; or FailedOver, in which the pool uses the backup databases defined in the topology. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPersistentChatState [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns the state of all the Persistent Chat servers configured for use in the organization.
  
```
Get-CsPersistentChatState
```

### Example 2

```
Get-CsPersistentChatState -Identity "PersistentChatServer:atl-gc-001.litwareinc.com"
```

### Example 3

Example 3 returns state information for all Persistent Chat servers in the domain litwareinc.com. To do this, the Filter parameter is included along with the filter value "*.litwareinc.com". That filter value causes the **Get-CsPersistentChatState** cmdlet to return information for all the Persistent Chat servers that have an Identity that ends with the string value ".litwareinc.com".
  
```
Get-CsPersistentChatState -Filter "*.litwareinc.com"
```

### Example 4

The command shown in Example 4 returns state information for all the Persistent Chat servers that are currently failed over. To carry out this task, the command first calls the **Get-CsPersistentChatState** cmdlet without any parameters; that returns a collection of all the Persistent Chat servers in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those servers where the PoolState property is equal to (-eq) "FailedOver".
  
```
Get-CsPersistentChatState | Where-Object {$_.PoolState -eq "FailedOver"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsPersistentChatState** cmdlet returns the state of one or more Persistent Chat pools. Persistent Chat pools can be in either the Normal state (in which the pool uses its primary databases) or in a FailedOver state, in which the pool uses its backup databases. You can use the [Set-CsPersistentChatState](set-cspersistentchatstate.md) cmdlet to change the state of a Persistent Chat pool; when you change the state of the pool, Skype for Business Server 2015 will automatically change the state of each individual server in the pool.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsPersistentChatState** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when retrieving one or more Persistent Chat states. For example, to return all the Persistent Chat states for the domain litwareinc.com, use this syntax:  <br/>  `-Filter "*.litwareinc.com"` <br/> You cannot use both the Filter parameter and the Identity parameter in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Persistent Chat pool. For example:  <br/>  `-Identity "PersistentChatServer:atl-gc-001.litwareinc.com`"  <br/> If this parameter is omitted then the **Get-CsPersistentChatState** cmdlet returns information for all your Persistent Chat states. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Persistent Chat state data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPersistentChatState** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPersistentChatState** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatState object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsPersistentChatState](set-cspersistentchatstate.md)

