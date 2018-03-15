---
title: "Get-CsServerApplication"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 46769cc2-9e61-4437-b74a-24f3cf118f39
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsServerApplication
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the server applications in use in your organization. Server applications are applications that are hosted by Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsServerApplication [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns information about all the server applications currently in use in the organization. This is done by calling the **Get-CsServerApplication** cmdlet without any parameters. 
  
```
Get-CsServerApplication
```

### EXAMPLE 2

In Example 2, information is returned for all the server applications running on the service EdgeServer:atl-edge-001.litwareinc.com.
  
```
Get-CsServerApplication -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"
```

### EXAMPLE 3

Example 3 returns information for a single server application: the application that has the Identity Registrar:atl-cs-001.litwareinc.com/ExumRouting".
  
```
Get-CsServerApplication -Identity "service:Registrar:atl-cs-001.litwareinc.com/ExumRouting"
```

### EXAMPLE 4

Example 4 returns all the server applications configured for use in the pool atl-cs-001.litwareinc.com. This is done by using the Filter parameter and the filter value "service:\*:atl-cs-001.litwareinc.com\*". The filter value limits the returned data to applications that have an Identity that begins with the characters "service:" and includes the characters ":atl-cs-001.litwareinc.com".
  
```
Get-CsServerApplication -Filter "service:*:atl-cs-001.litwareinc.com*"
```

### EXAMPLE 5

In Example 5, information is returned for all the server applications that are currently disabled. To carry out this task, the command first calls the **Get-CsServerApplication** cmdlet to return a collection of all the server applications configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those applications where the Enabled property is equal to False. 
  
```
Get-CsServerApplication | Where-Object {$_.Enabled -eq $False}
```

### EXAMPLE 6

Example 6 is a variation of the command shown in Example 5. In Example 6, information is returned for all the server applications that are marked as critical and are currently disabled. To do this, the command first calls the **Get-CsServerApplication** cmdlet without any parameters; that returns a collection of all the server applications configured for use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those applications that meet two criteria: the Critical property must be equal to True; and, the Enabled property must be equal to False. The -and operator ensures that only objects that meet both criteria will be returned. 
  
```
Get-CsServerApplication | Where-Object {$_.Critical -eq $True -and $_.Enabled -eq $False}
```

### EXAMPLE 7

In Example 7, information is returned for any server application that has the string value "routing" somewhere in its Uri. This task is accomplished by first using the **Get-CsServerApplication** cmdlet to retrieve all the server applications currently in use. The resulting collection is then piped to the **Where-Object** cmdlet, which selects only those applications in which the Uri property includes the string value "routing". 
  
```
Get-CsServerApplication | Where-Object {$_.Uri -like "*routing*"}
```

### EXAMPLE 8

Example 8 returns information for all the server applications that have been assigned a script. To do this, the command first retrieves a collection of all the server applications currently in use; this information is retrieved by calling the **Get-CsServerApplication** cmdlet without any parameters. The complete collection of server applications is then piped to the **Where-Object** cmdlet, which selects only those applications where the ScriptName property is not equal to a null value. If the ScriptName property is not equal to a null value that means that a script has been assigned to that application. 
  
```
Get-CsServerApplication | Where-Object {$_.ScriptName -ne $Null}
```

## Detailed Description
<a name="sectionSection1"> </a>

Server applications refer to the individual programs that run under Lync Server. The **Get-CsServerApplication** cmdlet provides a way for administrators to return information about any (or all) of the applications running as part of Lync Server. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsServerApplication** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsServerApplication"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when returning a server application or set of server applications. For example, to return all the server applications that have the string value "IIMFilter" somewhere in their Identity use this syntax: -Filter "\*IIMFilter\*".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the server application to be retrieved. Server application Identities are composed of the service where the application is hosted plus the application name. For example, the server application named QoEAgent might have an Identity similar to this: service: Registrar:atl-cs-001.litwareinc.com/QoEAgent.  <br/> To retrieve a collection of all the applications running on a given service, simply leave off the application name:  <br/> -Identity "Registrar:atl-cs-001.litwareinc.com "  <br/> If this parameter is omitted, then all the server applications will be returned when you call the **Get-CsServerApplication** cmdlet.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the server application data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsServerApplication** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsServerApplication** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsServerApplication](new-csserverapplication.md)
  
[Remove-CsServerApplication](remove-csserverapplication.md)
  
[Set-CsServerApplication](set-csserverapplication.md)

