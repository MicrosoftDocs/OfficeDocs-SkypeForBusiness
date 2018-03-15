---
title: "Remove-CsStaticRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 844e849e-a2f6-42fd-a49c-1ab234a07a65
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsStaticRoutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes the specified collection of static routing configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsStaticRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 removes the static routing configuration collection that has the Identity service:Registrar:atl-cs-001.litwareinc.com.
  
```
Remove-CsStaticRoutingConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com"
```

### EXAMPLE 2

In Example 2, all the static routing configuration collections applied to the service scope are removed. To do this, the command starts off by using the **Get-CsStaticRoutingConfiguration** cmdlet and the Filter parameter; the filter value "service:*" limits the returned data to collections that have an Identity that begins with the string value "service:". This filtered collection is then piped to the **Remove-CsStaticRoutingConfiguration** cmdlet, which deletes each item in that collection. 
  
```
Get-CsStaticRoutingConfiguration -Filter "service:*" | Remove-CsStaticRoutingConfiguration
```

### EXAMPLE 3

Example 3 shows how you can delete all the static routing configuration collections that have not been assigned any actual routes. To perform this task, the command first calls the **Get-CsStaticRoutingConfiguration** cmdlet; this returns information about all the static routing collections in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those collections where the number of routes (Route.Count) is equal to 0. The filtered information is then piped to the **Remove-CsStaticRoutingConfiguration** cmdlet, which deletes each collection that has not been assigned at least one route. 
  
```
Get-CsStaticRoutingConfiguration | Where-Object {$_.Route.Count -eq 0} | Remove-CsStaticRoutingConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

When you send a SIP message to someone that message might need to traverse multiple subnets and networks before it is delivered; the path traveled by the message is often referred to as a route. In networking, there are two types of routes: dynamic and static. With dynamic routing, servers use algorithms to determine the next location (the next hop) where a message should be forwarded. With static routing, message paths are predetermined by system administrators. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server that has been preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers. The downside to static routes is that messages are not dynamically rerouted in the event of a network failure.
  
When you install Lync Server, a global collection of static routes is automatically created for you. (The collection is created, but there are no routes assigned to that collection.) In addition, the software enables you to create additional collections applied to the service scope (these new collections can only be assigned to the Registrar service). If you later change your mind, you can use the **Remove-CsStaticRoutingConfiguration** cmdlet to delete the collections applied to the service scope. 
  
You can also run the **Remove-CsStaticRoutingConfiguration** cmdlet against the global collection. In that case, however, the global collection will not be removed; Lync Server does not allow you to remove global collections. Instead, all the properties in the global collection will be reset to their default values. That means that all the routes assigned to the global collection will be deleted. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsStaticRoutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsStaticRoutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the static routing configuration collection to be removed. To remove a collection configured at the service scope, use syntax similar to this: -Identity "service:Registrar:atl-cs-001.litwareinc.com".  <br/> The **Remove-CsStaticRoutingConfiguration** cmdlet can also be run against the global collection; to do so, use this syntax: -Identity global. Keep in mind, however, that the global collection will not actually be removed. Instead, the properties in that collection will be reset to their default values. That means that all the items in the Route property will be deleted.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings object. The **Remove-CsStaticRoutingConfiguration** cmdletaccepts pipelined instances of the static routing settings object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Remove-CsStaticRoutingConfiguration** cmdlet does not return a value or object. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)
  
[New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)
  
[Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

