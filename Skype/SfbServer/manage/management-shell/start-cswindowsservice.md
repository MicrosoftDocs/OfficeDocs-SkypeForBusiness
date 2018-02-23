---
title: "Start-CsWindowsService"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7491b91f-d342-4f9a-878b-d20b35294a9c
description: "The Start-CsWindowsService cmdlet enables you to start a Skype for Business Server 2015 service. This cmdlet was introduced in Lync Server 2010."
---

# Start-CsWindowsService
[]
The **Start-CsWindowsService** cmdlet enables you to start a Skype for Business Server 2015 service. This cmdlet was introduced in Lync Server 2010.
  
```
Start-CsWindowsService [-ComputerName <String>] [-Name <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 starts all the Skype for Business Server 2015 services on the local computer. This is done by calling the **Start-CsWindowsService** cmdlet without any parameters. Note that you will not receive an error if you try to start a service that has already been started.
  
```
Start-CsWindowsService
```

### EXAMPLE 2

Example 2 starts the Response Group application service on the local computer. To do this, the command uses the Name parameter followed by the service name: RTCRGS.
  
```
Start-CsWindowsService -Name "RTCRGS"
```

### EXAMPLE 3

The command shown in Example 3 also starts the Response Group application service; in this case, however, the service is started on the remote computer atl-cs-001.litwareinc.com. To start a service on a remote computer, include the ComputerName parameter followed by the FQDN of the remote computer.
  
```
Start-CsWindowsService -Name "RTCRGS" -ComputerName atl-cs-001.litwareinc.com
```

### EXAMPLE 4

In Example 4, the command searches the local computer for all the Skype for Business Server 2015 services that are not currently running, then starts each of these inactive services. To do this, the command first calls the **Get-CsWindowsService** cmdlet to return a collection of all the Skype for Business Server 2015 services. This collection is then piped to the **Where-Object** cmdlet, which selects only those services where the Status property is not equal to Running. This filtered collection is then piped to the **Start-CsWindowsService** cmdlet, which starts each service in the collection.
  
```
Get-CsWindowsService | Where-Object {$_.Status -ne "Running"} | Start-CsWindowsService
```

## Detailed Description

Many Skype for Business Server 2015 components run as standard Windows services; for example, the Conferencing Attendant application is actually a service named RTCCAA. If one of your Skype for Business Server 2015 services is currently stopped, you can restart that service by using the **Start-CsWindowsService** cmdlet.
  
Note, however, that the **Start-CsWindowsService** cmdlet can only start Skype for Business Server 2015 services; an error will occur if you attempt to start a non-Skype for Business Server 2015 service (such as the print spooler) using this cmdlet.
  
Functionally, the **Start-CsWindowsService** cmdlet is very similar to the generic Windows PowerShell **Start-** Service cmdlet; if you wanted to, you could use the **Start-Service** cmdlet to start a Skype for Business Server 2015 service. On the other hand, the **Start-CsWindowsService** cmdlet includes a ComputerName parameter that makes it easy to start a service on a remote computer: you simply include the ComputerName parameter followed by the fully qualified domain name (FQDN) of the remote computer. The **Start-Service** cmdlet does not have a comparable parameter. In addition, the cmdlet's Report parameter enables you to keep a log of any errors that might occur when calling **Start-CsWindowsService**.
  
Like other Windows services, some Skype for Business Server 2015 services have a dependency on another service; for example, the Skype for Business Server 2015 Conferencing Attendant service cannot run unless the Application service is already running. If you try to start a service that depends on another service, the **Start-CsWindowsService** cmdlet will start both of those services. That means that, if you try to start the Conferencing Attendant service, the cmdlet will first start the Application service and then start the Conferencing Attendant service. However, the **Start-CsWindowsService** cmdlet will not automatically start any dependent services of a service: if you start the Application service, the command will not automatically start the Conferencing Attendant service as well.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the remote computer hosting the service to be started; if this parameter is not included, then the **Start-CsWindowsService** cmdlet will start the specified service (or services) on the local computer. The remote computer should be referenced using its FQDN; for example, atl-cs-001.litwareinc.com. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InputObject_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deployment.Core.NTService  <br/> |Enables you to start a service using an object reference rather than a service name. For example, if you use the **Get-CsWindowsService** cmdlet to return information about a service, and if you store the returned object in a variable named $x, you can then start the service using this command: <br/>  `$x = Get-CsWindowsService -Name "RTCCPS"` <br/>  `Start-CsWindowsService -InputObject $x.Name` <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Name of the Skype for Business Server 2015 service you want to start. Note that you must use the service name (for example, RTCCAA) and not the service display name. You can only pass a single service name to the Name parameter, and you cannot use wildcards in the service name. Service names can be retrieved using the **Get-CsWindowsService** cmdlet. <br/> Keep in mind that the **Start-CsWindowsService** cmdlet can only start Skype for Business Server 2015 services; you cannot use this cmdlet to start other Windows services. For those services, you might be able to use the Windows PowerShell **Start-Service** cmdlet. <br/> |
| _NoWait_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, causes the command to run and then immediately return control to the Windows PowerShell prompt. If not present, control will not be returned until the command has completed and a status report has been written to the screen.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Path to an HTML file where error information can be stored. If this parameter is included, any errors that occur during the running of this cmdlet will be logged to the specified file (for example, C:\Logs\Service_report.html).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Microsoft.Rtc.Management.Deployment.Core.NTService object. The **Start-CsWindowsService** cmdlet accepts pipelined instances of the Windows service object.
  
## Return Types

None. Instead, the **Start-CsWindowsService** cmdlet starts instances of the Microsoft.Rtc.Management.Deployment.Core.NTService object.
  
## See also

#### 

[Get-CsWindowsService](get-cswindowsservice.md)
  
[Stop-CsWindowsService](stop-cswindowsservice.md)

