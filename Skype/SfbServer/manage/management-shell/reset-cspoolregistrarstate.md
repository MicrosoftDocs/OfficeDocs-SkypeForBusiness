---
title: "Reset-CsPoolRegistrarState"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1bdbd5d7-cc72-46c5-ac20-ddc0d5723fe0

description: "Resets the Registrar and Windows fabric services for the specified Registrar pool. This cmdlet was introduced in Lync Server 2013."
---

# Reset-CsPoolRegistrarState
 
Resets the Registrar and Windows fabric services for the specified Registrar pool. This cmdlet was introduced in Lync Server 2013.
  
```
Reset-CsPoolRegistrarState -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MachineFqdn <Fqdn>] [-NoReStart <SwitchParameter>] [-ResetLocalDatabases <SwitchParameter>] [-ResetType <ServiceReset | QuorumLossRecovery | FullReset | MachineStateRemoved>] [-ServicesStopDelayMins <Int32>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 performs a service reset for the Registrar pool atl-cs-001.litwareinc.com. Note that, after issuing this command, you will be prompted as to whether or not you want to proceed with the service reset. 
  
```
Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType ServiceReset
```

### Example 2

Example 2 also performs a service reset for the Registrar pool atl-cs-001.litwareinc.com. In this case, however, the Confirm parameter has been included along with the parameter value $False (-Confirm:$False). This causes the confirmation prompt which generally appears when you call the **Reset-CsPoolRegistrarState** cmdlet to be suppressed. As a result, you will not be prompted as to whether or not you want to proceed with the service reset. Instead, the command will run as soon as you press ENTER.
  
```
Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType ServiceReset -Confirm:$False
```

### Example 3

In Example 3, a quorum loss recovery reset is carried on the pool atl-cs-001.litwareinc.com. A quorum loss recovery is reset is typically used when the number of active Front End servers in a pool falls below the quorum state (that is, when fewer than 85% of the Front End servers in a pool are currently active). Note that only those services that are in a quorum loss will have to reload user data from the backup store. Other services will be unaffected by this command/ 
  
```
Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType QuorumLossRecovery
```

### Example 4

In Example 4, a full reset is done for the pool atl-cs-001.litwareinc.com. In a full reset, the Front End and Windows Fabric services are stopped and a set of items (including the files LyncServer-MachineSet.xml and Settings.xml) are removed. After these items have been removed, the Front End and Windows Fabric services are restarted. 
  
Note that using the FullReset option when attempting to restart a pool will sometimes result in failure, and the pool will not actually restart. Because of that, it is recommended that you first try to restart the pool using one of the other ResetType options. If that fails, please consult Microsoft support personnel before using the FullReset option.
  
```
Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType FullReset
```

### Example 5

Example 5 is a variation of the command shown in Example 4. In this case, however, the NoReStart parameter is included; this prevents the **Reset-CsPoolRegistrarState** cmdlet from restarting the services (such as the Windows Fabric service) that are stopped when the pool is reset. It will be up to administrators to manually restart these services.
  
Note that using the FullReset option when attempting to restart a pool will sometimes result in failure, and the pool will not actually restart. Because of that, it is recommended that you first try to restart the pool using one of the other ResetType options. If that fails, please consult Microsoft support personnel before using the FullReset option.
  
```
Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType FullReset -NoReStart
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Reset-CsPoolRegistrarState** cmdlet enables you to reset the Windows Fabric service (FabricHostSvc) and the Skype for Business Server 2015 Registrar service (RtcSrv) for a Registrar pool; this might be required if the pool has become non-responsive or fails to start. (Typically that means that the Registrar service will remain stuck in the Start Pending state.) Running this cmdlet will, by default, stop and then restart all the relevant services on the pool. However, you can use the NoReStart parameter to cause the **Reset-CsPooRegistrarState** cmdlet to stop those the services without restarting them. You can then choose to manually restart all (or some) of those services.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Reset-CsPoolRegistrarState** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the Registrar pool being reset. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _MachineFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the computer to be removed from the pool. This parameter is only used when performing a MachineStateRemoved reset.  <br/> |
| _NoReStart_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, services (such as RtcSrv and FabricHostSvc) that are stopped when the cmdlet runs are not restarted.  <br/> |
| _ResetLocalDatabases_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, stops and restarts the local Skype for Business Server 2015 databases in addition to the local Skype for Business Server 2015 services.  <br/> |
| _ResetType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Hadr.ResetPoolFabricStateCmdlet+PoolResetType  <br/> |Type of reset to be performed. Allowed values are:  <br/> ServiceReset - The RtcSrv and FabricHostSvc services are stopped and restarted. A service reset will be performed if the ResetType is not specified.  <br/> QuorumLossRecovery - Reloads user data from the backup store for any routing groups currently in quorum loss. (A quorum loss occurs when neither a database nor its replicas are available.) Data not yet written to the database could be lost when you do this type of reset.  <br/> FullReset - performs the same type of reset as QuorumLossRecovery but, in addition, rebuilds the local Skype for Business Server 2015 databases. This type of reset can be potentially long and resource-intensive.  <br/> > [!NOTE]> Using the FullReset value can cause previously disabled nodes to be reenabled. For example, if you use the FullReset value while one of the Front End Servers in the pool is disabled, that Front End Server will be brought back online.           > [!NOTE]> Using the  _FullReset_ value when attempting to restart a pool will sometimes result in failure, and the pool will not actually restart. Because of that, it is recommended that you first try to restart the pool using one of the other ResetType options. If that fails, please consult Microsoft support personnel before using the FullReset option. Typically FullReset is only used when changing a topology from a pool with a single Front End server to a pool with multiple Front End servers.          MachineStateRemoved -- Removes the specified server from the pool. This type of reset should be used only when the server in question (or its databases) have been permanently lost.  <br/> |
| _ServicesStopDelayMins_ <br/> |Optional  <br/> |System.Int32  <br/> |PARAMVALUE: Int32  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Reset-CsPoolRegistrarState** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

String values. The **Reset-CsPoolRegistrarState** cmdlet does not return objects.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPoolFabricState](get-cspoolfabricstate.md)

