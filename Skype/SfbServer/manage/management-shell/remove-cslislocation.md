---
title: "Remove-CsLisLocation"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 24e49a83-01a9-48ce-b940-fb0503f52077
description: "Removes a location from the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsLisLocation
[]
Removes a location from the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLisLocation -City <String> -CompanyName <String> -Country <String> -HouseNumber <String> -HouseNumberSuffix <String> -Location <String> -PostalCode <String> -PostDirectional <String> -PreDirectional <String> -State <String> -StreetName <String> -StreetSuffix <String> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 removes a location named Bldg30NEWing. This command specifies values for the parameters Location, HouseNumber, StreetName, City, State, and Country. This means that those are the only properties of the location to be deleted that contain non-null values. If you don't supply parameter values for all non-null properties, the location will not be deleted. You will be prompted for any parameter that you haven't specified in the command, but if they contain null values you can simply press Enter at each prompt.
  
```
Remove-CsLisLocation -Location Bldg30NEWing -HouseNumber 1000 -StreetName Main -City Redmond -State WA -Country US
```

### EXAMPLE 2

This example will remove all locations that are not referenced by a LIS port, subnet, switch, or wireless access point. The command begins with a call to the **Get-CsLisLocation** cmdlet, specifying the Unreferenced parameter. This will return a collection of all locations that are not referenced by a LIS port, subnet, switch, or wireless access point. This collection is then piped to the **Remove-CsLisLocation** cmdlet, which removes each location in the collection.
  
```
Get-CsLisLocation -Unreferenced | Remove-CsLisLocation
```

## Detailed Description

E9-1-1 enables those who answer emergency calls to determine the caller's geographic location without having to ask the caller for that information. In Skype for Business Server 2015 the location is determined based on mapping the caller's port, subnet, switch, or wireless access point to a specific location. This cmdlet removes a location from the location configuration database. All properties of a location combined make the location unique, so you must enter all non-null properties of the location to remove it. If you do not enter all non-null properties of the location you want to remove (and no other location contains only the properties you specified), no locations will be removed. You won't receive an error in this case, but no action will occur.
  
This cmdlet will not remove locations that are associated with a Location Information Server (LIS) port, subnet, switch, or wireless access point. If you attempt to remove a location referenced by any of these devices, you'll receive an error. You must remove all references before removing the location. You can use the **Remove-CsLisPort** cmdlet, the **Remove-CsLisSubnet** cmdlet, the **Remove-CsLisSwitch** cmdlet, and the **Remove-CsLisWirelessAccessPoint** cmdlet to remove these references.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _City_ <br/> |Required  <br/> |System.String  <br/> |The location city.  <br/> |
| _CompanyName_ <br/> |Required  <br/> |System.String  <br/> |The name of the company at this location.  <br/> |
| _Country_ <br/> |Required  <br/> |System.String  <br/> |The country/region this location is in. This value will contain two characters or less.  <br/> |
| _HouseNumber_ <br/> |Required  <br/> |System.String  <br/> |The house number of the location. For a company this is the number on the street where the company is located.  <br/> |
| _HouseNumberSuffix_ <br/> |Required  <br/> |System.String  <br/> |Additional information for the house number, such as 1/2 or A. For example, 1234 1/2 Oak Street or 1234 A Elm Street.  <br/> |
| _Location_ <br/> |Required  <br/> |System.String  <br/> |The name for this location.  <br/> |
| _PostalCode_ <br/> |Required  <br/> |System.String  <br/> |The postal code associated with this location.  <br/> |
| _PostDirectional_ <br/> |Required  <br/> |System.String  <br/> |The directional designation of a street name. For example, NE or NW for Main Street NE or 7th Avenue NW.  <br/> |
| _PreDirectional_ <br/> |Required  <br/> |System.String  <br/> |The directional designation for a street name that precedes the name of the street. For example, NE or NW for NE Main Street or NW 7th Avenue.  <br/> |
| _State_ <br/> |Required  <br/> |System.String  <br/> |The state or province associated with this location. This value will be two characters or less.  <br/> |
| _StreetName_ <br/> |Required  <br/> |System.String  <br/> |The name of the street for this location.  <br/> |
| _StreetSuffix_ <br/> |Required  <br/> |System.String  <br/> |The type of street designated in a street name, such as Street, Avenue, or Court.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Accepts pipelined input of LIS location objects.
  
## Return Types

This cmdlet does not return a value or object. It removes an object of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Set-CsLisLocation](set-cslislocation.md)
  
[Get-CsLisLocation](get-cslislocation.md)
  
[Remove-CsLisPort](remove-cslisport.md)
  
[Remove-CsLisSubnet](remove-cslissubnet.md)
  
[Remove-CsLisSwitch](remove-cslisswitch.md)
  
[Remove-CsLisWirelessAccessPoint](remove-csliswirelessaccesspoint.md)
  
[Get-CsLisCivicAddress](get-csliscivicaddress.md)

