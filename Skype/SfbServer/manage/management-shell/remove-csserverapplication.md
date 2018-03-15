---
title: "Remove-CsServerApplication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 55325d8c-9c67-4e88-868d-ce62bc11322e
description: "Removes an existing server application. Server applications are applications that are hosted by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsServerApplication
 
Removes an existing server application. Server applications are applications that are hosted by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsServerApplication -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

In Example 1, the server application that has the Identity service: EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor is removed. Because Identities must be unique, this command will never delete more than a single application.
  
```
Remove-CsServerApplication -Identity "service:EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor"
```

### EXAMPLE 2

In Example 2, all the non-critical server applications are removed. To carry out this task, the command first calls the **Get-CsServerApplication** cmdlet in order to return a collection of all the server applications currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks all the applications where the Critical property is equal to False. This filtered collection is then piped to the **Remove-CsServerApplication** cmdlet, which deletes each item in the collection.
  
```
Get-CsServerApplication | Where-Object {$_.Critical -eq $False} | Remove-CsServerApplication
```

### EXAMPLE 3

Example 3 deletes all the server applications that have been configured for use by the service EdgeServer:atl-cs-001.litwareinc.com. To do this, the **Get-CsServerApplication** cmdlet is used along with the Filter parameter; the filter value "service:EdgeServer:atl-cs-001.litwareinc.com/*" returns all the applications that have an Identity that begins with the characters "service:EdgeServer:atl-cs-001.litwareinc.com/". In turn, that collection is piped to the **Remove-CsServerApplication** cmdlet, which deletes each application from the EdgeServer:atl-cs-001.litwareinc.com.
  
```
Get-CsServerApplication -Filter "service:EdgeServer:atl-cs-001.litwareinc.com/*" | Remove-CsServerApplication
```

## Detailed Description

Server applications refer to the individual programs that run under Skype for Business Server 2015. The **Remove-CsServerApplication** cmdlet provides a way for administrators to remove any application running as part of Skype for Business Server 2015. Note that deleting a server application is not the same thing as uninstalling that application. When you run the **Remove-CsServerApplication** cmdlet, the application no longer runs under Skype for Business Server 2015. However, the software itself is not uninstalled, and the application can be re-enabled by running the **New-CsServerApplication** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the server application to be removed. Server application Identities are composed of the service where the application is hosted plus the application name. For example, the server application named QoEAgent might have an Identity similar to this: service:Registrar:atl-cs-001.litwareinc.com/QoEAgent.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application object. The **Remove-CsServerApplication** cmdlet accepts pipelined instances of the server application object.
  
## Return Types

The **Remove-CsServerApplication** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application object.
  
## See also

#### 

[Get-CsServerApplication](get-csserverapplication.md)
  
[New-CsServerApplication](new-csserverapplication.md)
  
[Set-CsServerApplication](set-csserverapplication.md)

