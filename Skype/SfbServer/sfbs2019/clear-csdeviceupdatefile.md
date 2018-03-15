---
title: "Clear-CsDeviceUpdateFile"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 34c5bb61-fcba-4e93-bb21-83b9611f3045
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Clear-CsDeviceUpdateFile
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Deletes any rejected device update files that are no longer associated with a device. This cmdlet was introduced in Lync Server 2010.
  
```
Clear-CsDeviceUpdateFile -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 deletes all the device update files from the service WebServer:atl-cs-001.litwareinc.com that are no longer associated with a device.
  
```
Clear-CsDeviceUpdateFile -Identity "service:WebServer:atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="sectionSection1"> </a>

Each time new device updates are uploaded to the system, a corresponding device update rule is created. By default, these new device update rules are assigned to the Pending state; that means that the rules can be downloaded and installed on test devices, but not on production devices. In turn, this gives you an opportunity to test the updates before making them available to users. If testing is successful, you can then run the **Approve-CsDeviceUpdateRule** cmdlet to make these device updates available to users. 
  
If testing is not successful then you can use the **Reset-CsDeviceUpdateRule** cmdlet or the **Restore-CsDeviceUpdateRule** cmdlet to reject an update. When these cmdlets are run, the device update is disassociated from its device update rule. At that point, administrators can then use the **Clear-CsDeviceUpdateFile** cmdlet to remove the disassociated updates from the server. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Clear-CsDeviceUpdateFile** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Clear-CsDeviceUpdateFile"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the service hosting the device update files. For example, this syntax clears device update files from the Web Services service for the pool atl-cs-001.litwareinc.com: -Identity "service:WebServer:atl-cs-001.litwareinc.com".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Clear-CsDeviceUpdateFile** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

None. The **Clear-CsDeviceUpdateFile** cmdlet does not return any values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Clear-CsDeviceUpdateLog](clear-csdeviceupdatelog.md)
  
[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)

