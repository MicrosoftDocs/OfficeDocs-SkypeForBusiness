---
title: "Get-CsNetworkInterface"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 06a5fedf-d87e-4469-9bd6-ad16c1f9a801
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsNetworkInterface
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the network interfaces in use on computers running Lync Server services or server roles. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsNetworkInterface [-Identity <NetworkInterfaceIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 returns information for all the network interfaces configured for use in the organization.
  
```
Get-CsNetworkInterface
```

### EXAMPLE 2

The command shown in Example 2 returns information about a single network interface: the interface that has the Identity atl-cs-001.litwareinc.com.com/Primary/1.
  
```
Get-CsNetworkInterface -Identity atl-cs-001.litwareinc.com/Primary/1
```

### EXAMPLE 3

In Example 3, information is returned for all the network interfaces in the domain litwareinc.com. To do this, the Filter parameter is included, along with the filter value "\*.litwareinc.com\*". This filter value limits the returned data to interfaces that have an Identity that includes the string value "litwareinc.com".
  
```
Get-CsNetworkInterface -Filter "*.litwareinc.com*"
```

### EXAMPLE 4

Example 4 returns information about all the network interfaces configured for the IP address 192.168.0.240. To do this, the command first calls the **Get-CsNetworkInterface** cmdlet without any parameters; this returns a collection of all the network interfaces configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those interfaces where the IPAddress property is equal to 192.168.0.240. 
  
```
Get-CsNetworkInterface | Where-Object {$_.IPAddress -eq "192.168.0.240"}
```

### EXAMPLE 5

The command shown in Example 5 is a variation of the command shown in Example 4; in this case, however, information is returned for all the network interfaces configured for the subnet "192.168.0.*". This is done by retrieving a collection of all the network interfaces, piping that collection to the **Where-Object** cmdlet, and then picking out only those interfaces where IPAddress starts with the string value "192.168.0.". 
  
```
Get-CsNetworkInterface | Where-Object {$_.IPAddress -like "192.168.0.*"}
```

### EXAMPLE 6

Example 6 returns all the network interfaces that have been configured for external access. To do this, the **Get-CsNetworkInterface** cmdlet is first called without any parameters; this returns a collection of all the network interfaces currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those items where the Interface property is equal to External. 
  
```
Get-CsNetworkInterface | Where-Object {$_.Interface -eq "External"}
```

## Detailed Description
<a name="sectionSection1"> </a>

In order for information to be transmitted from one computer to another, computers need network interfaces: connections between a computer and the network. Computers running Lync Server services or server roles must have at least one network interface; otherwise they will not be able to communicate with other computers. However, these computers can also have multiple network interfaces; for example, an Edge Server might have one interface for connecting to the internal network and a second interface for connecting to the Internet. The **Get-CsNetworkInterface** cmdlet provides a way for administrators to return information about the network interfaces currently in use on computers running Lync Server services or server roles. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkInterface** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsNetworkInterface"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of the computer for which network interface information is to be returned. For example, to return network interface information for the computer atl-cs-001.litwareinc.com (and only for that computer) use this syntax: -ComputerFqdn atl-cs-001.litwareinc.com.  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the network interface (or interfaces) to be returned. For example, this syntax returns information about the Primary network interface used on all of your computers running a Lync Server service or server role: -Filter "\*/Primary/\*".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.NetworkInterfaceIdentity  <br/> |Unique identifier for the network interface to be returned. A network interface Identity consists of three parts:  <br/> The fully qualified domain name (FQDN) of the computer itself (for example, atl-cs-001.litwareinc.com).  <br/> The network interface "side" (Primary; Internal; External; public switched telephone network). The side indicates the type of traffic the port is used for.  <br/> The network interface number for that particular side.  <br/> For example: -Identity "atl-cs-001.litwareinc.com/Primary/1".  <br/> The Identity, ComputerFqdn, and Filter parameters must be used separately; for example, you cannot run a command that uses both ComputerFqdn and Identity. In addition, you cannot use wildcard characters when specifying the Identity. To employ wildcards, use the Filter parameter.  <br/> If neither the Identity, ComputerFqdn, nor Filter parameters are used, then the **Get-CsNetworkInterface** cmdlet returns information about all the network interfaces currently in use on your computers running a Lync Server service or server role.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsNetworkInterface** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsNetworkInterface** cmdlet returns an instance of the Microsoft.Rtc.Management.Xds.DisplayNetworkInterface object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsComputer](get-cscomputer.md)

