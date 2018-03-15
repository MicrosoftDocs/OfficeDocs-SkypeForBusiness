---
title: "Clear-CsDeviceUpdateLog"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9e549484-b79b-47ef-b83b-13a6e20b0c80
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Clear-CsDeviceUpdateLog
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Deletes all the Device Update Web service log and audit files that are older than the specified number of days. This cmdlet was introduced in Lync Server 2010.
  
```
Clear-CsDeviceUpdateLog -DaysBack <Int32> -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 connects to the Device Update Web service with the Identity "service:WebServer:atl-cs-001.litwareinc.com" and deletes all the device and audit logs that are more than 10 days old.
  
```
Clear-CsDeviceUpdateLog -Identity "service:WebServer:atl-cs-001.litwareinc.com" -DaysBack 10
```

## Detailed Description
<a name="sectionSection1"> </a>

The Device Update Web service keeps an extensive collection of log files; this collection includes both audit logs conducted by the service itself as well as log files uploaded from client devices such as cell phones. Depending on the amount of device update activity, and depending on the number of client devices used in your organization, your server could soon become "cluttered" with Device Update Web service logs. The **Clear-CsDeviceUpdateLog** cmdlet provides a way for you to reduce the number of log files stored on the server: all you have to do is run the cmdlet and specify the maximum age (in days) of the files that should not be deleted. Any log files older than that maximum age will be removed from the system. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Clear-CsDeviceUpdateLog** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Clear-CsDeviceUpdateLog"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DaysBack_ <br/> |Required  <br/> |System.Int32  <br/> |Maximum age (in days) of the log files to be maintained. All log files older than the value specified using the DaysBack parameter will be deleted. For example, if you set DaysBack to 7 then any log files more than seven days old will be removed.  <br/> This parameter can be set to any integer value between 1 and 30, inclusive.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the service hosting the Device Update Web service log files. For example, this syntax clears Device Update Web service log files from the Web Services for the pool atl-cs-001.litwareinc.com: -Identity "service:WebServer:atl-cs-001.litwareinc.com".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Clear-CsDeviceUpdateLog** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

None. The **Clear-CsDeviceUpdateLog** cmdlet does not return any values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Clear-CsDeviceUpdateFile](clear-csdeviceupdatefile.md)
  
[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)

