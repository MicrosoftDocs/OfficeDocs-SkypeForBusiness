---
title: "Stop-CsWindowsService"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 60318b9f-2291-4b99-a271-d206e4074b70
description: "Stop-CsWindowsService enables you to stop a Skype for Business Server 2015 service. This cmdlet was introduced in Lync Server 2010."
---

# Stop-CsWindowsService
 
 **Stop-CsWindowsService** enables you to stop a Skype for Business Server 2015 service. This cmdlet was introduced in Lync Server 2010.
  
```
Stop-CsWindowsService [-ComputerName <String>] [-Name <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 stops the Response Group application service on the local computer. The Response Group application service is identified by including the Name parameter and the name of that service: RTCRGS.
  
```
Stop-CsWindowsService -Name "RTCRGS"
```

### EXAMPLE 2

Example 2 also stops the Response Group application service; in this example, however, that service is located on the remote computer atl-cs-001.litwareinc.com. To stop a service on a remote computer, include the ComputerName parameter followed by the FQDN of the remote computer.
  
```
Stop-CsWindowsService -Name "RTCRGS" -ComputerName atl-cs-001.litwareinc.com
```

### EXAMPLE 3

Example 3 demonstrates how you can stop a service even if you do not know the service name (in this example, RTCCPS). To do this, the command first calls the **Get-CsWindowsService** cmdlet without any parameters in order to return a collection of all the Skype for Business Server 2015 services on the local computer. This complete collection is then piped to the **Where-Object** cmdlet, which selects only those services where the DisplayName property includes the string value "Call Park". The filtered collection is then piped to the **Stop-CsWindowsService** cmdlet, which stops the Call Park application service.
  
```
Get-CsWindowsService | Where-Object {$_.DisplayName -like "*Call Park*"} | Stop-CsWindowsService
```

## Detailed Description

Many Skype for Business Server 2015 components run as standard Windows services; for example, the Conferencing Attendant application is actually a service named RTCCAA. If you need to stop a Skype for Business Server 2015 service, you can do so by using the **Stop-CsWindowsService** cmdlet.
  
Keep in mind that the **Stop-CsWindowsService** cmdlet can only stop Skype for Business Server 2015 services; an error will occur if you attempt to stop a non-Skype for Business Server 2015 service (such as the print spooler) using this cmdlet.
  
Functionally, the **Stop-CsWindowsService** cmdlet is very similar to the generic Windows PowerShell **Stop-** Service cmdlet; if you wanted to, you could use the **Stop-Service** cmdlet to stop a Skype for Business Server 2015 service. However, the **Stop-CsWindowsService** cmdlet includes a ComputerName parameter that makes it easy to stop a service on a remote computer: you simply include the ComputerName parameter followed by the fully qualified domain name (FQDN) of the remote computer. The **Stop-Service** cmdlet does not have a comparable parameter. In addition, the **Stop-CsWindowsService** cmdlet has a Report parameter that enables you to keep a log of any errors that might occur when calling that cmdlet.
  
The **Stop-CsWindowsService** cmdlet does exactly what the name implies: it stops any service you ask it to stop. This includes services that have dependent services (services that can only run if the service you are attempting to stop is running). By default, if you try to stop a service that has dependent services, the **Stop-CsWindowsService** cmdlet will not only stop the service in question, but will stop all those dependent services as well. Because that could result in unexpected consequences, you can include the Graceful parameter when calling the **Stop-CsWindowsService** cmdlet. When you include the Graceful parameter, the **Stop-CsWindowsService** cmdlet will prevent the service from accepting any new requests. All existing service requests will remain as is; however, new requests will be rejected. As existing requests finish, those requests will not be replaced. Eventually, all the existing requests will be filled and the service will then shut down.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the remote computer running the service to be stopped; if this parameter is not included, then the **Stop-CsWindowsService** cmdlet will stop the specified service on the local computer. The remote computer should be referenced using its FQDN; for example, atl-mcs-001.litwareinc.com. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Graceful_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Instead of immediately shutting down a service, waits until all existing service requests have been filled. (However, all new service requests will be rejected.) The service will not completely shut down until all the existing requests have been filled.  <br/> |
| _InputObject_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deployment.Core.NTService  <br/> |Enables you to stop a service using an object reference rather than a service name. For example, if you use the **Get-CsWindowsService** cmdlet to return information about a service, and if you store the returned object in a variable named $x, you can then stop the service using this command: <br/>  `$x = Get-CsWindowsService -Name "RTCCPS"` <br/>  `Stop-CsWindowsService -InputObject $x.Name` <br/> |
| _LeaveClsAgentRunning_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, stops all the Skype for Business Server 2015 services except for the centralized logging agent service.  <br/> |
| _LeaveWebServerRunning_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, shuts down all services except the Web Server service on the specified computer.  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Name of the Skype for Business Server 2015 service you want to stop. Note that you must use the service name (for example, RTCCAA) and not the service display name. You can only pass a single service name to the Name parameter, and you cannot use wildcards in the service name. You can use the **Get-CsWindowsService** cmdlet to retrieve service names. <br/> Keep in mind that the **Stop-CsWindowsService** cmdlet can only stop Skype for Business Server 2015 services; you cannot use this cmdlet to stop other Windows services. For those services, you might be able to use the Windows PowerShell **Stop-Service** cmdlet. <br/> |
| _NoWait_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, causes the command to run and then immediately return control to the Windows PowerShell prompt. If not present, control will not be returned until the command has completed and a status report has been written to the screen.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Path to an HTML file where error information can be written. If this parameter is included, any errors that occur during the running of this cmdlet will be logged to the specified file (for example, C:\Logs\Service_report.html).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _LeaveBackupServiceRunning_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
   
## Input Types

Microsoft.Rtc.Management.Deployment.Core.NTService object. The **Stop-CsWindowsService** cmdlet accepts pipelined instances of the Windows service object.
  
## Return Types

None. Instead, the **Stop-CsWindowsService** cmdlet stops instances of the Microsoft.Rtc.Management.Deployment.Core.NTService object.
  
## See also

#### 

[Get-CsWindowsService](get-cswindowsservice.md)
  
[Start-CsWindowsService](start-cswindowsservice.md)

