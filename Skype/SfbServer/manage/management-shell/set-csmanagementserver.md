---
title: "Set-CsManagementServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6607580d-f111-4dff-961a-71525bf2e482
description: "Modifies the replication port used by the Skype for Business Server 2015 Central Management service. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsManagementServer
[]
Modifies the replication port used by the Skype for Business Server 2015 Central Management service. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsManagementServer [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplicationServicePort <UInt16>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 connects to the Central Management service with the Identity ManagementServer:atl-cs-001.litwareinc.com and sets the replication service port to port 5076.
  
```
Set-CsManagementServer -Identity "ManagementServer:atl-cs-001.litwareinc.com" -ReplicationServicePort 5076
```

## Detailed Description

The Central Management service is responsible for replicating data between the Central Management store and computers running Skype for Business Server 2015 services or server roles. The Central Management service runs on a single Front End pool (or a single Standard Edition server) and facilitates replication throughout the Skype for Business Server 2015 infrastructure. 
  
The **Set-CsManagementServer** cmdlet enables you to specify the port that the Central Management service uses for replication.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the Central Management service. For example:  `-Identity "ManagementServer:atl-cs-001.litwareinc.com"`.  <br/> Note that you can leave off the prefix "ManagementServer:" when specifying a Central Management Server. For example:  `-Identity "atl-cs-001.litwareinc.com"`.  <br/> |
| _ReplicationServicePort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for the replication port used by the Central Management service.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Set-CsManagementServer** cmdlet does not accept pipelined input.
  
## Return Types

The **Set-CsManagementServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayManagementServer object.
  
## See also

#### 

[Get-CsService](get-csservice.md)
  
[Move-CsManagementServer](move-csmanagementserver.md)

