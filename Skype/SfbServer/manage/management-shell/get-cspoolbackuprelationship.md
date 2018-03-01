---
title: "Get-CsPoolBackupRelationship"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 230bbb04-b4cb-410f-8284-00740558655d
description: "Returns information about the backup pool associated with a Skype for Business Server 2015 pool. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsPoolBackupRelationship
 
Returns information about the backup pool associated with a Skype for Business Server 2015 pool. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPoolBackupRelationship -PoolFqdn <Fqdn> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example returns information about the backup relationship assigned to the pool atl-cs-001.litwareinc.com.
  
```
Get-CsPoolBackupRelationship -PoolFqdn "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The G **et-CsPoolBackupRelationship** cmdlet returns the fully qualified domain name of the backup pool associated with a Registrar pool. Note that this is read-only information: there is no corresponding **Set-CsPoolBackupRelationship** cmdlet that lets you use the Windows PowerShell command-line interface to create a backup association. Instead, backup pools must be assigned using Skype for Business Server 2015 Topology Builder.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsPoolBackupRelationship** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool whose backup relationship is being checked. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the backup relationship data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPoolBackupRelationship** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPoolBackupRelationship** cmdlet returns instances of the Microsoft.Rtc.Management.Hadr.BackupService.BackupRelation object.
  

