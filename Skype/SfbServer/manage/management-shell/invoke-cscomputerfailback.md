---
title: "Invoke-CsComputerFailBack"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b3fae621-ed11-4f65-99f9-a67bf4fdd684
description: "Use the Invoke-CsComputerFailBack to flag a server as available for load balancing in a Skype for Business Server 2015 pool. To successfully run this cmdlet you need to run it using an account that has administrator privileges on each server in the source and target pools."
---

# Invoke-CsComputerFailBack
 
Use the **Invoke-CsComputerFailBack** to flag a server as available for load balancing in a Skype for Business Server 2015 pool. To successfully run this cmdlet you need to run it using an account that has administrator privileges on each server in the source and target pools.
  
```
Invoke-CsComputerFailBack [-ComputerName <String>] [-Confirm [<SwitchParameter>]] [-NoStart <SwitchParameter>] [-Report <String>] [-SkipFabricHealthCheck <SwitchParameter>] [-WaitTime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example marks the computer "atl-mcs-001.litwareinc.com" as available to the pool and enables the services, but does not start them.
  
```
Invoke-CsComputerFailBack -ComputerName "atl-mcs-001.litwareinc.com" -NoStart
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Invoke-CsComputerFailBack** cmdlet functionality is not available in the Skype for Business Server Control Panel.
  
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerName_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the computer name to fail back. The computer should be referenced by using its fully qualified domain name (FQDN). For example,  `-ComputerName "atl-mcs-001.litwareinc.com"`. The computer name used during failback must be the same name used during failover.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _NoStart_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If the  _NoStart_ parameter is specified, the Skype for Business server is added back into the pool and marked as available, but all the Skype for Business services are not started. Only the Skype for Business service (rtcsrv) is verified by the cmdlet. This allows for follow-up scripting to start the remaining services and configure the server for your environment before users and data are assigned. <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the file path for the log file created when the cmdlet runs. For example: `-Report "C:\Logs\Server1FailbackLog.html"`. If this file already exists, it will be overwritten. By default, reports are written to the AppData\Local\Temp folder in your user profile.  <br/> |
| _SkipFabricHealthCheck_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _WaitTime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time in TimeSpan format that the cmdlet will wait for a confirmation of failback success. If the time is exceeded, the cmdlet will fail and Skype for Business services will not be started or enabled. The default is one hour.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Invoke-CsComputerFailBack** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Invoke-CsComputerFailOver](invoke-cscomputerfailover.md)

