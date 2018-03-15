---
title: "Invoke-CsComputerFailOver"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 87e2c48c-975c-4cb6-aa5b-bbed7e989941
description: "Use the Invoke-CsComputerFailOver to force a computer in a Skype for Business Server 2015 pool to failover to other servers within the pool. To successfully run this cmdlet you need to run it using an account that has administrator privileges on each server in the source and target pools."
---

# Invoke-CsComputerFailOver
 
Use the **Invoke-CsComputerFailOver** to force a computer in a Skype for Business Server 2015 pool to failover to other servers within the pool. To successfully run this cmdlet you need to run it using an account that has administrator privileges on each server in the source and target pools.
  
```
Invoke-CsComputerFailOver [-ComputerName <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NoStop <SwitchParameter>] [-Report <String>] [-SkipFabricHealthCheck <SwitchParameter>] [-WaitTime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example directs that the users assigned to server "atl-mcs-001.litwareinc.com" will be moved to other servers in the pool. The log output path is specified and the cmdlet will wait 1 hour 30 minutes before timing out.
  
```
Invoke-CsComputerFailOver -ComputerName "atl-mcs-001.litwareinc.com" -Report "C:\Logs\S1_FailOverLog.html" -WaitTime 1:30:00 
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Invoke-CsComputerFailOver** cmdlet migrates the users and data, and drains the existing conferences and sessions before the Skype for Business services are stopped and disabled to prevent accidental restart when computer is rebooted.
  
The **Invoke-CsComputerFailOver** cmdlet functionality is not available in the Skype for Business Server Control Panel.
  
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerName_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the computer name to fail over. The computer should be referenced by using its fully qualified domain name (FQDN). For example,  `-ComputerName "atl-mcs-001.litwareinc.com"`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If the  _Force_ parameter is specified, the server is failed over without verifying the pool's capacity to absorb the failed over server's workload. <br/> |
| _NoStop_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If specified, Skype for Business Server services will not be stopped as part of the failover. This maintains the failed over server's state for additional scripting or troubleshooting.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the file path for the log file created when the cmdlet runs. For example: `-Report "C:\Logs\S1_FailOverLog.html"`. If this file already exists, it will be overwritten. By default, reports are written to the "AppData\Local\Temp" folder in your user profile.  <br/> |
| _SkipFabricHealthCheck_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _WaitTime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time in TimeSpan format that the cmdlet will wait for confirmation that users and data have been migrated, and all conferences and sessions have been drained. If the wait time is exceeded, the cmdlet fails and no action is taken on the specified server. The default is one hour.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Invoke-CsComputerFailOver** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Invoke-CsComputerFailBack](invoke-cscomputerfailback.md)

