---
title: "Remove-CsLisSwitch"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 53456988-4b37-4f34-825d-bebee5124856
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsLisSwitch
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a Location Information Server (LIS) network switch. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLisSwitch -ChassisID <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 removes the LIS switch with the MAC address (ChassisID) 99-99-99-99-99-99.
  
This command will not succeed if the ChassisID is referenced by a port. Also, if this switch was associated with a location, that location will not be removed, only the switch will be removed from the location mapping.
  
```
Remove-CsLisSwitch -ChassisID 99-99-99-99-99-99
```

### EXAMPLE 2

This example removes all switches that do not have a city. The example begins with a call to the **Get-CsLisSwitch** cmdlet, which returns a collection of all switches. This collection is piped to the **Where-Object** cmdlet, which finds the items in that collection that have a City property that is empty; in other words, a City that is equal to (-eq) an empty string (""). Finally, we pipe this collection of switches that don't have cities to the **Remove-CsLisSwitch** cmdlet, which removes everything in that collection. 
  
Note that, as in Example 1, no locations are removed from the location database, only the switches that reference those locations are removed. In this case that means there will be invalid locations (they're invalid because City is a required property for a location) in the location database that should also be removed. You can remove locations by calling the **Remove-CsLisLocation** cmdlet. 
  
```
Get-CsLisSwitch | Where-Object {$_.City -eq ""} | Remove-CsLisSwitch
```

## Detailed Description
<a name="sectionSection1"> </a>

Enhanced 9-1-1 (E9-1-1) allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet removes a switch from the location configuration database. Removing a switch will not remove the actual location; it removes only the switch. To remove the location, call the **Remove-CsLisLocation** cmdlet. 
  
You cannot remove a switch if the ChassisID of the switch is in use by a port. (Run the following command to find out which ChassisIDs are in use by ports: Get-CsLisPort | Select-Object ChassisID.) You must first remove all ports with the given ChassisID before you can remove the switch.
  
If you attempt to remove a switch that does not exist, no action will be taken and you will not receive an error or a warning message.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLisSwitch** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsLisSwitch"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ChassisID_ <br/> |Required  <br/> |System.String  <br/> |The Media Access Control (MAC) address of the network switch. This value will be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Accepts pipelined input of LIS switch objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type System.Management.Automation.PSCustomObject.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsLisSwitch](set-cslisswitch.md)
  
[Get-CsLisSwitch](get-cslisswitch.md)
  
[Remove-CsLisLocation](remove-cslislocation.md)
  
[Get-CsLisPort](get-cslisport.md)

