---
title: "Set-CsServerApplication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b0f75629-b6c3-4958-b466-6c8a2f104819
description: "Modifies the property values of an existing server application. Server applications are applications that are hosted by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsServerApplication
 
Modifies the property values of an existing server application. Server applications are applications that are hosted by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsServerApplication [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 enables the server application that has the Identity Registrar:atl-cs-001.litwareinc.com/ExumRouting. Because Identities must be unique, this command will only enable a single server application.
  
```
Set-CsServerApplication -Identity "Registrar:atl-cs-001.litwareinc.com/ExumRouting" -Enabled $True
```

### EXAMPLE 2

Example 2 enables all the server applications that are currently disabled. To do this, the command first calls the **Get-CsServerApplication** cmdlet in order to return a collection of all the server applications currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those applications where the Enabled property is equal to False. In turn, the filtered collection is piped to the **Set-CsServerApplication** cmdlet, which takes each item in the collection and sets the Enabled property to True.
  
```
Get-CsServerApplication | Where-Object {$_.Enabled -eq $False} | Set-CsServerApplication -Enabled $True
```

## Detailed Description

Server applications refer to the individual programs that run under the Skype for Business Server 2015. The **Set-CsServerApplication** cmdlet provides a way for administrators to modify the property values of any application running as part of Skype for Business Server 2015.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Critical_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True (the default value), then Skype for Business Server 2015 will not start unless the application in question can be started. If False, then Skype for Business Server 2015 will start regardless of whether or not the application can be started.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Set this value to True to enable the application. Set the value to False to disable the application.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the server application to be modified. Server application Identities are composed of the service where the application is hosted plus the application name. For example, the server application named QoEAgent might have an Identity similar to this: Registrar:atl-cs-001.litwareinc.com/QoEAgent.  <br/> |
| _Instance_ <br/> |Optional  <br/> |ServerApplication.Application object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |Indicates the order of execution for server applications. The application with priority 0 is started first; the application with priority 1 is started second; and so on. Note that each service that hosts a server application has its own unique set of priorities. For example, the Registrar service might host three applications with corresponding priorities 0, 1, and 2. Similarly, the Edge Server service might have four applications; these applications will have the priorities 0, 1, 2, and 3.  <br/> If you do not specify a priority then the application will automatically be added to the bottom of the priority list. If you add or remove an application, the priorities of the other applications will be adjusted accordingly. For example, if you delete an application that has a priority of 0, then the application that previously had the priority 1 will automatically have its priority set to 0.  <br/> |
| _Script_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to associate the server application with a script. To add a script to a server application, use syntax similar to this:  <br/>  `-Script "Update.ps1"` <br/> To remove a script, simply set the Script property to a null value:  <br/>  `-Script $Null` <br/> Each server application can only be associated with one script.  <br/> |
| _ScriptName_ <br/> |Optional  <br/> |System.String  <br/> |Path to the Microsoft SIP Processing Language (MSPL) script used by the application. MSPL is a scripting language used for filtering and routing SIP messages.  <br/> |
| _Uri_ <br/> |Optional  <br/> |System.String  <br/> |Unique Uniform Resource Identifier (URI) for the application. For example, the QoEAgent application has the URI http://www.microsoft.com/LCS/QoEAgent.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application object. The **Set-CsServerApplication** cmdlet accepts pipelined instances of the server application object.
  
## Return Types

The **Set-CsServerApplication** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.application object.
  
## See also

#### 

[Get-CsServerApplication](get-csserverapplication.md)
  
[New-CsServerApplication](new-csserverapplication.md)
  
[Remove-CsServerApplication](remove-csserverapplication.md)

