---
title: "Get-CsWindowsService"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9b119dac-c3e6-4031-8ae4-972fca1ef728
description: "Get-CsWindowsService returns detailed information about Skype for Business Server 2015 components that run as Windows services. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsWindowsService
 
 **Get-CsWindowsService** returns detailed information about Skype for Business Server 2015 components that run as Windows services. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsWindowsService [-ComputerName <String>] [-ExcludeActivityLevel <SwitchParameter>] [-Name <String>] [-Report <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns information about all the Skype for Business Server 2015 services installed on the local computer. This is done by calling the **Get-CsWindowsService** cmdlet without any parameters.
  
```
Get-CsWindowsService
```

### EXAMPLE 2

Example 2 also returns information about the Skype for Business Server 2015 services on the local computer; in this case, however, the data is displayed in list format. (Among other things, this enables you to view all the property values for each service. In the default, tabular view, only a subset of property values is displayed.) To carry out this task, the **Get-CsWindowsService** cmdlet is first called, then the resulting information is piped to the **Format-List** cmdlet.
  
```
Get-CsWindowsService | Format-List
```

### EXAMPLE 3

Example 3 returns information for a single Skype for Business Server 2015 service: the service with the name RTCSrv.
  
```
Get-CsWindowsService -Name "RTCSrv"
```

### EXAMPLE 4

In Example 4, detailed information is displayed for all the service roles handled by the RTCSrv service. To perform this task, the **Get-CsWindowsService** cmdlet is first used to return information about the RTCSrv service. This information is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to display all the roles handled by the RTCSrv service. Note that this command will return an error message if a service does not have a role name.
  
```
Get-CsWindowsService -Name "RTCSrv" | Select-Object -ExpandProperty RoleName
```

### EXAMPLE 5

The command shown in Example 5 returns information about the Skype for Business Server 2015 services installed on the remote computer atl-cs-001.litwareinc.com. This is done by including the ComputerName parameter followed by the FQDN of the remote computer.
  
```
Get-CsWindowsService -Computer atl-cs-001.litwareinc.com
```

### EXAMPLE 6

Example 6 returns information about all the Skype for Business Server 2015 services installed on the local computer. In addition, the Report parameter is included in order to save error information to a file named C:\Logs\Services.html. If the **Get-CsWindowsService** cmdlet encounters any problems in retrieving service data, information about that problem will be recorded in Services.html.
  
```
Get-CsWindowsService -Report C:\Logs\Services.html
```

### EXAMPLE 7

In Example 7, information is returned only for the Skype for Business Server 2015 services on the local computer that are currently running. To accomplish this, the command first calls the **Get-CsWindowsService** cmdlet to return a collection of all the Skype for Business Server 2015 services, running or not running. This collection is then piped to the **Where-Object** cmdlet, which picks out only those services where the Status property is equal to Running.
  
```
Get-CsWindowsService | Where-Object {$_.Status -eq "Running"}
```

### EXAMPLE 8

Example 8 shows how you can retrieve information for a particular service even if you do not know the actual name of that service (in this case, RTCASMCU). To perform this task, the **Get-CsWindowsService** cmdlet is first called without any parameters; that returns a collection of all the Skype for Business Server 2015 services on the local computer. This collection is then piped to the **Where-Object** cmdlet, which selects the one service where the DisplayName property includes (-like) the string value "Application Sharing". The end result: information is displayed for the Skype for Business Server 2015 Application Sharing Conferencing service.
  
```
Get-CsWindowsService | Where-Object {$_.DisplayName -like "*Application Sharing*"}
```

### EXAMPLE 9

Example 9 returns information about any services that host the Application Server role. To do this, the command first calls the **Get-CsWindowsService** cmdlet to return a collection of all the Skype for Business Server 2015 services on the local computer. This collection is then piped to the **Where-Object** cmdlet, which selects those services where the RoleName property includes (-contains) ApplicationServer.
  
```
Get-CsWindowsService | Where-Object {$_.RoleName -contains "ApplicationServer"}
```

## Detailed Description

Many Skype for Business Server 2015 components run as standard Windows services; for example, the Skype for Business Server 2015 Conferencing Attendant application is actually a service named RTCCAA. The **Get-CsWindowsService** cmdlet enables you to retrieve detailed information about these Skype for Business Server 2015 services and only these services. That's because the cmdlet has been designed to ignore any service that is not part of Skype for Business Server 2015.
  
The fact that the **Get-CsWindowsService** cmdlet automatically filters out non-Skype for Business Server 2015 services is one advantage the cmdlet offers over the generic **Get-Service** cmdlet that ships as part of Windows PowerShell. In addition to that, there is another reason to use the **Get-CsWindowsService** cmdlet if you need to retrieve information for a Skype for Business Server 2015 service: the **Get-CsWindowsService** cmdlet returns useful data that the **Get-Service** cmdlet does not return. For example, when returning information about the Skype for Business Server 2015 Conferencing Attendant service, the **Get-CsWindowsService** cmdlet reports back the number of concurrent calls being handled by the service (the service activity level). The **Get-Service** cmdlet does not.
  
By default the **Get-CsWindowsService** cmdlet runs against the local computer. However, by including the ComputerName parameter you can return information about the Skype for Business Server 2015 services running on a remote computer.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the remote computer from which service information is to be retrieved; if this parameter is not included, the **Get-CsWindowsService** cmdlet will return information about the Skype for Business Server 2015 services running on the local computer. The remote computer should be referenced by using its fully qualified domain name (FQDN); for example, atl-mcs-001.litwareinc.com. <br/> |
| _ExcludeActivityLevel_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If included, this parameter causes the **Get-CsWindowsService** cmdlet to return only the service status and not the service activity level. <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Name of the service you want to return information for. Note that you must use the service name (for example, RTCCAA) and not the service display name. You can only pass a single service name to the Name parameter; in addition you cannot use wildcards in the service name.  <br/> Note, too that the **Get-CsWindowsService** cmdlet can only return information for Skype for Business Server 2015 services; you cannot use this cmdlet to return information for other Windows services. For those services, you might be able to use the Windows PowerShell **Get-Service** cmdlet. <br/> If you do not include this parameter, the **Get-CsWindowsService** cmdlet will return information about all your Skype for Business Server 2015 services. <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Path to an HTML file where error information can be stored. If this parameter is included, any errors that occur during the running of this cmdlet will be logged to the specified file (for example, C:\Logs\Service_report.html).  <br/> |
   
## Input Types

None. The **Get-CsWindowsService** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsWindowsService** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.Core.NTService object.
  
## See also

#### 

[Start-CsWindowsService](start-cswindowsservice.md)
  
[Stop-CsWindowsService](stop-cswindowsservice.md)

