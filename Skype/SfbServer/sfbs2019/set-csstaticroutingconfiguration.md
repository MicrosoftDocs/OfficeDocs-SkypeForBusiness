---
title: "Set-CsStaticRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8f3e923e-f1e1-4a22-8252-5ef24fbc3cb3
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsStaticRoutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies an existing collection of static routing configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsStaticRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The commands shown in Example 1 copy a route from the global static routing collection, and then assign that route to a second static routing collection, one with the Identity service:Registrar:atl-cs-001.litwareinc.com. To carry out this task, the first command in the example connects to the global collection and returns an object reference to the route with the MatchUri litwareinc.com and a MatchOnlyPhoneUri equal to True. 
  
To do this, the command calls the **Get-CsStaticRoutingConfiguration** cmdlet to return information from the global routing static configuration collection. This data is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to expand the values in the Route property. These expanded values (which represent the individual routes assigned to the collection) are then piped to the **Where-Object** cmdlet, which picks out the one route where the MatchUri property is equal to litwareinc.com and the MatchOnlyPhoneUri property is equal to True. The returned route is stored in a variable named $x. 
  
After the route has been retrieved, the second command in the example adds that route to the service: Registrar:atl-cs-001.litwareinc.com collection. To do this, the **Set-CsStaticRoutingConfiguration** cmdlet is called along with the Route parameter; the parameter value @{Add=$x} instructs the **Set-CsStaticRoutingConfiguration** cmdlet to append the route stored in the variable $x to the collection of routes maintained in the Route property. 
  
```
$x = Get-CsStaticRoutingConfiguration -Identity global | Select-Object -ExpandProperty Route | Where-Object {$_.MatchUri -eq "litwareinc.com" -and $_.MatchOnlyPhoneUri -eq $True}
Set-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com -Route @{Add=$x}

```

### EXAMPLE 2

The commands shown in Example 2 delete a route from a static routing collection. To do this, the first command in the example connects to the collection with the Identity service:Registrar:atl-cs-001.litwareinc.com and returns an object reference to the route with the MatchUri litwareinc.com and a MatchOnlyPhoneUri equal to True. To do that, the command calls the **Get-CsStaticRoutingConfiguration** cmdlet to return information from the service:Registrar:atl-cs-001.litwareinc.com collection. This data is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to expand the values in the Route property. These expanded values (which represent the individual routes assigned to the collection) are then piped to the **Where-Object** cmdlet, which picks out the one route where the MatchUri property is equal to litwareinc.com and the MatchOnlyPhoneUri property is equal to True. The returned route in then stored in a variable named $x. 
  
After the route has been retrieved, the second command deletes that route from the collection. To do this, the **Set-CsStaticRoutingConfiguration** cmdlet is called along with the Route parameter; the parameter value @{Remove=$x} instructs the **Set-CsStaticRoutingConfiguration** cmdlet to delete the route stored in the variable $x. 
  
```
$x = Get-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com | Select-Object -ExpandProperty Route | Where-Object {$_.MatchUri -eq "litwareinc.com" -and $_.MatchOnlyPhoneUri -eq $True}
Set-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com -Route @{Remove=$x}

```

### EXAMPLE 3

Example 3 shows how you can remove all the routes assigned to a static routing configuration collection. To do this, simply include the Route parameter and set the parameter value to null. After the command completes, the collection will still exist, but it will no longer have any routes assigned to it.
  
```
Set-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com -Route $Null

```

## Detailed Description
<a name="sectionSection1"> </a>

When you send a SIP message to someone that message might need to traverse multiple subnets and networks before it is delivered; the path traveled by the message is often referred to as a route. In networking, there are two types of routes: dynamic and static. With dynamic routing, servers use algorithms to determine the next location (the next hop) where a message should be forwarded. With static routing, message paths are predetermined by system administrators. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server that has been preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers. The downside to static routes is that messages are not dynamically rerouted in the event of a network failure.
  
When you install Lync Server, a global collection of static routes is automatically created for you. (The collection is created, but there are no routes assigned to that collection.) In addition, the software enables you to create additional collections applied to the service scope (these new collections can only be assigned to the Registrar service). The **Set-CsStaticRoutingConfiguration** cmdlet enables you to modify the property values of an existing static routing collection. This means that you can use the cmdlet to add new routes to a collection, or to delete existing routes from a collection. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsStaticRoutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsStaticRoutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the static routing configuration collection to be modified. To modify the global collection, use this syntax: -Identity global. To modify a collection applied to the service scope, use syntax similar to this: -Identity "service:Registrar:atl-cs-001.litwareinc.com". You cannot use wildcards when specifying the Identity.  <br/> If this parameter is not included the **Set-CsStaticRoutingConfiguration** cmdlet will automatically modify the global collection.  <br/> |
| _Instance_ <br/> |Optional  <br/> |RoutingSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Route_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Individual static routes maintained within the collection. Routes to be added to a collection must either be copied from another collection or created by using the **New-CsStaticRoute** cmdlet; to delete a route from a collection, you must first create an object reference to that route. For details, see the Examples section of help topic.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings object. The **Set-CsStaticRoutingConfiguration** cmdlet accepts pipelined instances of the static routing settings object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsStaticRoutingConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)
  
[New-CsStaticRoute](new-csstaticroute.md)
  
[New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)
  
[Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)

