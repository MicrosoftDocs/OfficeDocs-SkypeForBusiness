---
title: "Remove-CsLisPort"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b8a648af-1064-4a1e-8462-f267b7b72be1
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsLisPort
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an association between a Location Information Server (LIS) port and a location. This association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLisPort -ChassisID <String> -PortID <String> -PortIDSubType <InterfaceAlias | InterfaceName | LocallyAssigned> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 removes the LIS port with the MAC address (ChassisID) 99-99-99-99-99-99, the PortID 4200, and the PortIDSubType 1. (Note that a value of 1 for PortIDSubType translates into a value of InterfaceAlias. This parameter and value could also have been entered like this: -PortIDSubType InterfaceAlias)
  
If this port was associated with a location, that location will not be removed, only the port will be removed from the location mapping.
  
```
Remove-CsLisPort -ChassisID 99-99-99-99-99-99 -PortID 4200 -PortIDSubType 1
```

### EXAMPLE 2

This example removes all port locations that do not have a house number. The example begins with a call to the **Get-CsLisPort** cmdlet, which returns a collection of all LIS ports. This collection is piped to the **Where-Object** cmdlet, which finds the items in that collection that have a HouseNumber property that is empty; in other words, a HouseNumber that is equal to (-eq) an empty string (""). Finally, we pipe this collection of port locations that don't have house numbers to the **Remove-CsLisPort** cmdlet, which removes everything in that collection. 
  
Note that, as in example 1, no locations are removed from the location configuration database, only the ports that reference those locations are removed. In this case that means there will be invalid locations (they're invalid because HouseNumber is a required property for a location) in the location database that should also be removed. You can remove locations by calling the **Remove-CsLisLocation** cmdlet. 
  
```
Get-CsLisPort | Where-Object {$_.HouseNumber -eq ""} | Remove-CsLisPort
```

## Detailed Description
<a name="sectionSection1"> </a>

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet removes an association between a physical location and a port through which calls will be routed by removing the port from the location configuration database.
  
Removing a port location will not remove the actual location of the port; it removes only the port. To remove the location, call the **Remove-CsLisLocation** cmdlet. Removing the port will also not remove the switch with the given ChassisID; to remove the switch, call the **Remove-CsLisSwitch** cmdlet. 
  
If you attempt to remove a port that does not exist, no action will be taken and you will not receive an error or a warning message.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLisPort** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsLisPort"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ChassisID_ <br/> |Required  <br/> |System.String  <br/> |The Media Access Control (MAC) address of the port's switch. This value will be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.  <br/> |
| _PortID_ <br/> |Required  <br/> |System.String  <br/> |The ID of the port you want to remove.  <br/> |
| _PortIDSubType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Lis.PortIDSubType  <br/> |The subtype of the port you want to remove. This value can be entered as a numeric value or a string, but it must be a valid subtype. Valid subtypes are:  <br/> 1: InterfaceAlias  <br/> 5: InterfaceName  <br/> 7: LocallyAssigned  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Accepts pipelined input of LIS port objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type System.Management.Automation.PSCustomObject.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsLisPort](set-cslisport.md)
  
[Get-CsLisPort](get-cslisport.md)
  
[Remove-CsLisLocation](remove-cslislocation.md)
  
[Remove-CsLisSwitch](remove-cslisswitch.md)

