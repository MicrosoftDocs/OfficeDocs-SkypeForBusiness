---
title: "Get-CsDatabaseMirrorState"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 458f5367-ee04-4281-971f-08f79a625509
description: "Returns information about whether database mirroring has been implemented for a specified database on a specified pool. Database mirroring enables you to simultaneously maintain two copies of a database, with each copy residing on a different server. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsDatabaseMirrorState
[]
Returns information about whether database mirroring has been implemented for a specified database on a specified pool. Database mirroring enables you to simultaneously maintain two copies of a database, with each copy residing on a different server. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsDatabaseMirrorState -PoolFqdn <Fqdn> [-DatabaseType <Application | Archiving | Monitoring | User | Provision | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt | SigninTelemetry | ActiveMonitoring>] [-LocalStore <SwitchParameter>] [-Report <String>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns the state of the database mirror assigned to the monitoring database for the pool atl-cs-001.litwareinc.com.
  
```
Get-CsDatabaseMirrorState -PoolFqdn "atl-cs-001.litwareinc.com" -DatabaseType Monitoring
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsDatabaseMirrorState** cmdlet returns information about the mirror databases configured for a pool; this includes information about the mirror databases that might (or might not) have been configured for the Front End server database, the Location Information Service database, the call detail recording and Quality of Experience databases, and so on. For each database the cmdlet will report back the synchronization status for both the primary database and the mirror database. In some cases you will see output similar to this, including the property value DatabaseInaccessibleOrMirroringNotEnabled:
  
DatabaseName : lcscdr
  
StateOnPrimary : DatabaseInaccessibleOrMirroringNotEnabled
  
StateOnMirror : DatabaseInaccessibleOrMirroringNotEnabled
  
MirroringStatusOnPrimary :
  
MirroringStatusOnSecondary :
  
That typically means that no mirror database has been assigned to the primary database (in this case, the database lcscdr, used for maintaining call detail data).
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsDatabaseMirrorState** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool whose database mirroring state is being checked. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _DatabaseType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deployment.DatabaseNameType  <br/> |Type of database whose mirror state is being checked. Allowed values are:  <br/> ActiveMonitoring  <br/> Application  <br/> Archiving  <br/> CentralMgmt  <br/> Edge  <br/> Lyss  <br/> Monitoring  <br/> PersistentChat  <br/> PersistentChatCompliance  <br/> Provision  <br/> Registrar  <br/> SigninTelemetry  <br/> User  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the backup mirror state from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\Logs\DatabaseMirrorState.html"` <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsDatabaseMirrorState** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsDatabaseMirrorState** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.DatabaseMirrorState class.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Install-CsMirrorDatabase](install-csmirrordatabase.md)
  
[Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)

