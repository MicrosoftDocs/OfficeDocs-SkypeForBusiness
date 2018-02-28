---
title: "Set-CsLisSwitch"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ad2a1890-724a-4f9f-bd50-de0c9de86f8e
description: "Creates a Location Information Server (LIS) switch, creates an association between a switch and a location (creating a new location if that location doesn't exist), or modifies an existing switch and its associated location. The association between a switch and location is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsLisSwitch
[]
Creates a Location Information Server (LIS) switch, creates an association between a switch and a location (creating a new location if that location doesn't exist), or modifies an existing switch and its associated location. The association between a switch and location is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsLisSwitch -ChassisID <String> [-City <String>] [-CompanyName <String>] [-Country <String>] [-Description <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-Location <String>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 creates or updates a LIS switch location entry. The command in this example includes only one (required) parameter: ChassisID. The value of the ChassisID is the MAC address of the switch, in this case 99-99-99-99-99-99.
  
Notice that this example does not include any address information. It's possible to create a switch entry on the Location Information Server without associating it with an address. However, emergency calls routed through this switch may not (depending on subnet or port locations that have been defined) contain enough information for the emergency operator to identify a location.
  
IMPORTANT: If a LIS switch location with this ChassisID already exists, it will be replaced by the values in this command. That means that if this switch were associated with an address (a physical location), that association would no longer exist because we didn't include any location information in this command. The location will still exist in the location database, but it will not be associated with this switch.
  
```
Set-CsLisSwitch -ChassisID 99-99-99-99-99-99
```

### EXAMPLE 2

Example 2 updates the switch created in Example 1 by adding address information. (This is actually deleting the existing entry and replacing it with this new entry.) If the address does not exist in the location database, this cmdlet will create that location.
  
```
Set-CsLisSwitch -ChassisID 99-99-99-99-99-99 -Location "30/1000" -HouseNumber 1234 -PreDirectional NE -StreetName First -StreetSuffix Avenue -City Redmond -State WA -Country US -PostalCode 99999
```

## Detailed Description

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet allows the administrator to map physical locations to the network switch through which the client is connected.
  
The ChassisID parameter is the only required parameter for this cmdlet. If you enter a ChassisID value that already exists, this cmdlet will update the location for that switch based on the location parameters that are supplied. If the ChassisID does not exist, a new switch location will be created.
  
If a location with an address exactly matching the address parameters entered here (including null values) does not exist in the location database, a new address will be created based on the parameters entered with this cmdlet. (You can retrieve a list of locations by calling the **Get-CsLisLocation** cmdlet.) The **Set-CsLisSwitch** cmdlet does not require or prompt for location parameters; you can create a switch entry without associating it with a location. It's also possible to create an invalid location with this cmdlet. A valid location consists of, at minimum, the Location, HouseNumber, StreetName, City, State, and Country. If you do not supply all of these parameters, calls that are received by the referenced switch may not contain the information required by the emergency operator (depending on whether valid settings are available for a subnet or wireless access point that can be used in place of switch settings). It is recommended that you be as specific as possible with the location parameters and fill in as many as possible.
  
Note that switch entries can also be created by calling the **Set-CsLisPort** cmdlet. If the **Set-CsLisPort** cmdlet is called with a ChassisID value that does not have an existing switch entry, that switch will be created.
  
It's important to note that these changes will take effect only if you have configured the MACResolverUrl property using the [New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md) cmdlet or the[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md) cmdlet. The MACResolverUrl property specifies the URL for a web service that is capable of taking an IP address and determining the Media Access Control (MAC) address of the network card associated with that IP address.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ChassisID_ <br/> |Required  <br/> |System.String  <br/> |The Media Access Control (MAC) address of the network switch. This value must be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab, or in the form of an IP address. If an entry with the specified ChassisID value does not exist, a new switch location will be created. If an entry with the specified ChassisID does exist, that entry will be replaced.  <br/> |
| _City_ <br/> |Optional  <br/> |System.String  <br/> |The location city.  <br/> Maximum length: 64 characters.  <br/> |
| _CompanyName_ <br/> |Optional  <br/> |System.String  <br/> |The name of the company at this location.  <br/> Maximum length: 60 characters  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Country_ <br/> |Optional  <br/> |System.String  <br/> |The country/region this location is in.  <br/> Maximum length: 2 characters  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A detailed description of this network switch location.  <br/> |
| _HouseNumber_ <br/> |Optional  <br/> |System.String  <br/> |The house number of the location. For a company this is the number on the street where the company is located.  <br/> Maximum length: 10 characters  <br/> |
| _HouseNumberSuffix_ <br/> |Optional  <br/> |System.String  <br/> |Additional information for the house number, such as 1/2 or A. For example, 1234 1/2 Oak Street or 1234 A Elm Street.  <br/> Note: To designate an apartment number or office suite, you must use the Location parameter. For example,  `-Location "Suite 100/Office 150"`.  <br/> Maximum length: 5 characters  <br/> |
| _Location_ <br/> |Optional  <br/> |System.String  <br/> |The name for this location. Typically this value is the name of a location more specific than the civic address, such as an office number, but it can be any string value.  <br/> Maximum length: 20 characters  <br/> |
| _PostalCode_ <br/> |Optional  <br/> |System.String  <br/> |The postal code associated with this location.  <br/> Maximum length: 10 characters  <br/> |
| _PostDirectional_ <br/> |Optional  <br/> |System.String  <br/> |The directional designation of a street name. For example, NE or NW for Main Street NE or 7th Avenue NW.  <br/> Maximum length: 2 characters  <br/> |
| _PreDirectional_ <br/> |Optional  <br/> |System.String  <br/> |The directional designation for a street name that precedes the name of the street. For example, NE or NW for NE Main Street or NW 7th Avenue.  <br/> Maximum length: 2 characters  <br/> |
| _State_ <br/> |Optional  <br/> |System.String  <br/> |The state or province associated with this location.  <br/> Maximum length: 2 characters  <br/> |
| _StreetName_ <br/> |Optional  <br/> |System.String  <br/> |The name of the street for this location.  <br/> Maximum length: 60 characters  <br/> |
| _StreetSuffix_ <br/> |Optional  <br/> |System.String  <br/> |The type of street designated in a street name, such as Street, Avenue, or Court.  <br/> Maximum length: 10 characters  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Accepts pipelined input of LIS switch objects.
  
## Return Types

This cmdlet creates or modifies an object of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Remove-CsLisSwitch](remove-cslisswitch.md)
  
[Get-CsLisSwitch](get-cslisswitch.md)
  
[Get-CsLisLocation](get-cslislocation.md)
  
[Set-CsLisPort](set-cslisport.md)
  
[Get-CsLisPort](get-cslisport.md)

