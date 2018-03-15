---
title: "Invoke-CsPoolFailOver"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b5c30438-0553-41f4-b856-68c1ec0deff7
description: "Invokes the failover process for a Skype for Business Server 2015 pool. Failover refers to the process that occurs when a pool fails and the current users of that pool are then signed on to a backup pool. This cmdlet was introduced in Lync Server 2013."
---

# Invoke-CsPoolFailOver
 
Invokes the failover process for a Skype for Business Server 2015 pool. Failover refers to the process that occurs when a pool fails and the current users of that pool are then signed on to a backup pool. This cmdlet was introduced in Lync Server 2013.
  
```
Invoke-CsPoolFailOver -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-DatabaseCommandTimeoutInSeconds <Int32>] [-DisasterMode <SwitchParameter>] [-FlushStorageService <SwitchParameter>] [-Force <SwitchParameter>] [-ServicesStopDelayMins <Int32>] [-SkipDataVerification <SwitchParameter>] [-WaitTime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 invokes pool failover for the pool atl-cs-001.litwareinc.com.
  
```
Invoke-CsPoolFailOver -PoolFqdn "atl-cs-001.litwareinc.com"
```

### Example 2

Example 2 invokes disaster mode failover for the pool atl-cs-001.litwareinc.com.
  
```
Invoke-CsPoolFailOver -PoolFqdn "atl-cs-001.litwareinc.com" -DisasterMode
```

## Detailed Description
<a name="DetailedDescription"> </a>

The pool failover process provides a way for administrators to quickly restore service to users if the Registrar pool they have logged on to should suddenly become unavailable. If a pool fails, users will automatically be signed off from Skype for Business Server 2015; if they immediately try to log back on, they will be redirected to their specified backup pool.
  
To restore service to these users, administrators can run the **Invoke-CsPoolFailOver** cmdlet against the pool that is not currently available. Doing this will allow users to sign on to Skype for Business Server 2015 using the designated backup pool, and give these users access to all Skype for Business Server 2015 services and functionality. Note that users will not be rehomed on the backup pool; they will simply be allowed to log on and make use of that pool until their home pool has been restored. For example, if Pool A fails, users will be able to log on to Pool B (with complete functionality) until Pool A has been restored.
  
When the failed pool is once more up and running, administrators can then run the **Invoke-CsPoolFailBack** cmdlet in order to "fail back" users of that pool. If a user is currently logged on to the backup pool then he or she will be redirected back to their home pool after service has been restored.
  
Pool failover can only be invoked if you have assigned a backup pool to the failed pool.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Invoke-CsPoolFailOver** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool being failed over from. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DatabaseCommandTimeoutInSeconds_ <br/> |Optional  <br/> |System.Int32  <br/> |The amount of time to wait, in seconds, for database commands to time out.  <br/> |
| _DisasterMode_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, indicates that failover is being performed in "disaster mode." If a pool is no longer accessible the only way to restore full functionality to users in that pool is to fail over the pool by using the DisasterMode parameter.  <br/> If this parameter is not present that means that the pool is still up and running and that failover occurred by administrator choice; for example, the pool might temporarily be failed over in order to do hardware or software upgrades on the server.  <br/> |
| _FlushStorageService_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, the **Invoke-CsPoolFailOver** cmdlet will both fail over all the users in the pool, and call the [Invoke-CsStorageServiceFlush](invoke-csstorageserviceflush.md) cmdlet to flush the storage service database on each Front End server in the pool. Flushing a database involves writing all the queued data to disk, and then clearing the database cache. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _ServicesStopDelayMins_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies a number of minutes to wait for the services to stop.  <br/> |
| _SkipDataVerification_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When included in a command, Invoke-CsPoolFailback will proceed with the failback operation without first verifying data integrity.  <br/> |
| _WaitTime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time (in seconds) that the cmdlet will wait before assuming that the data has been synced from the failed-over pool to the backup pool.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _HealthCheckOnly_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _IgnoreBackupServiceErrorState_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _IgnoreCMSDelay_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _IgnoreTargetPoolFEsNotRunning_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _NoPerformanceCounters_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _PrepareForFailoverOnly_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _PromptOnError_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _ServersToIgnore_ <br/> |Optional  <br/> |System.String   <br/> |PARAMVALUE: String   <br/> |
| _SkipFabricHealthCheck_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Invoke-CsPoolFailOver** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Invoke-CsPoolFailBack](invoke-cspoolfailback.md)

