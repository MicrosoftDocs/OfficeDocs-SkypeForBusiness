---
title: "Invoke-CsBackupServiceSync"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f3de25c2-a1ef-4781-8b33-74f5dc1e6f8d
description: "Manually invokes backup synchronization between a Skype for Business Server 2015 pool and its designated backup pool. This allows administrators to synchronize data without waiting for Skype for Business Server 2015 replication. This cmdlet was introduced in Lync Server 2013."
---

# Invoke-CsBackupServiceSync
 
Manually invokes backup synchronization between a Skype for Business Server 2015 pool and its designated backup pool. This allows administrators to synchronize data without waiting for Skype for Business Server 2015 replication. This cmdlet was introduced in Lync Server 2013.
  
```
Invoke-CsBackupServiceSync -PoolFqdn <Fqdn> [-BackupModule <String>] [-Force <SwitchParameter>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 synchronizes the backup services for the pool atl-cs-001.litwareinc.com.
  
```
Invoke-CsBackupServiceSync -PoolFqdn "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Invoke-CsBackupServiceSync** cmdlet enables administrators to synchronize the data between a Registrar pool and its backup pool. The **Invoke-CsBackupServiceSync** cmdlet will only copy as much data as needed in order to bring the two pools into sync.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Invoke-CsBackupServiceSync** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool where backup service synchronization is being invoked. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _BackupModule_ <br/> |Optional  <br/> |System.String  <br/> |Indicates the type of data to be synchronized. Valid values are:  <br/> UserServices.PresenceFocus  <br/> ConfServices.DataConf  <br/> CentralMgmt.CMSMaster  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

String value. The **Invoke-CsBackupServiceSync** cmdlet can accept a pipelined string value representing the fully qualified domain name of a Skype for Business Server 2015 pool.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Backup-CsPool](backup-cspool.md)

