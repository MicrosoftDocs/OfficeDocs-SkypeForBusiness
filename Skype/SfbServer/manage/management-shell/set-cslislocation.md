---
title: "Set-CsLisLocation"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 955cdce0-250d-48b7-8891-5355d801911f
description: "Creates a new location or modifies an existing location in the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010."
---

# Set-CsLisLocation
 
Creates a new location or modifies an existing location in the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsLisLocation -City <String> -CompanyName <String> -Country <String> -HouseNumber <String> -HouseNumberSuffix <String> -Location <String> -PostalCode <String> -PostDirectional <String> -PreDirectional <String> -State <String> -StreetName <String> -StreetSuffix <String> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 creates a new location named Bldg30NEWing. This command fills in all the parameters that are required to have values for a location to be created. In this example the address of the location is 1000 Main, Redmond, WA, US. That address is entered by specifying the HouseNumber parameter with the value 1000; the StreetName parameter with the value Main; the City parameter with the value Redmond; and the Country parameter with the value US.
  
Note that if you run a command with just the parameters shown here you will be prompted to enter additional parameters. However, you can simply press Enter at each prompt without supplying values and your location will be created.
  
```
Set-CsLisLocation -Location Bldg30NEWing -HouseNumber 1000 -StreetName Main -City Redmond -State WA -Country US
```

### EXAMPLE 2

This example is similar to Example 1 in that it creates a new location. However, in this example the command specifies all the parameters for the cmdlet. This will avoid the prompts that will follow the command in Example 1 because this example instead simply sets any values we want to leave blank to empty strings. 
  
```
Set-CsLisLocation -Location "Suite 100/Office 20" -CompanyName "Litware, Inc." -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName Main -StreetSuffix St -PostDirectional "" -City Redmond -State WA -PostalCode 99999 -Country US
```

### EXAMPLE 3

This example modifies the location created in Example 1. The first line in the example begins with a call to the **Get-CsLisLocation** cmdlet. This returns a collection of all locations defined within the Skype for Business Server 2015 deployment. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet retrieves all items from the collection where the Location property is equal to (-ceq, case-sensitive equals) Bldg30NEWing. The object matching this criteria is assigned to the variable $a.
  
In line 2 we call the **Set-CsLisLocation** cmdlet. The first parameter is the Instance parameter. We pass this parameter the variable ($a) containing the object we retrieved in line 1, which just happens to be the object we want to modify. We then specify the StreetSuffix parameter, passing it a value of Street. This will change the value of the StreetSuffix property of the location in variable $a to Street.
  
Keep in mind that because Location is not a unique property, the **Where-Object** cmdlet could return more than one location. If it does, this example will not work. To modify multiple locations at once, see Example 4.
  
```
$a = Get-CsLisLocation | Where-Object {$_.Location -ceq "Bldg30NEWing"}
Set-CsLisLocation -Instance $a -StreetSuffix Street
```

### EXAMPLE 4

Example 4 modifies the StreetSuffix property of one or more location objects. The example begins much like Example 3. We begin by calling the **Get-CsLisLocation** cmdlet to retrieve all the locations. We then pipe this collection of locations to the **Where-Object** cmdlet, which narrows down the collection to only those locations with a Location property equal to NorthCampus. This new collection is stored in variable $a. In line 2 we pipe the contents of $a to the **Set-CsLisLocation** cmdlet. This cmdlet will go through each object (each location) that was stored in $a and modify that object. In this case the modification is to change the StreetSuffix property of each object to Avenue.
  
The commands in this example can also be accomplished without the use of a variable. Simply pipe the results of the **Where-Object** cmdlet command to the **Set-CsLisLocation** cmdlet, like this:
  
```
Get-CsLisLocation | Where-Object {$_.Location -ceq "NorthCampus"} | Set-CsLisLocation -StreetSuffix Avenue

```

```
$a = Get-CsLisLocation | Where-Object {$_.Location -ceq "NorthCampus"}
$a | Set-CsLisLocation -StreetSuffix Avenue
```

## Detailed Description

E9-1-1 enables those who answer emergency calls to determine the caller's geographic location without having to ask the caller for that information. In Skype for Business Server 2015 the location is determined based on mapping the caller's port, subnet, switch, or wireless access point to a specific location. (This map is known as a wiremap.) This cmdlet adds a new address to or modifies an existing address in the list of locations that are stored in the location configuration database on the Location Information Server (LIS). The locations are subsequently matched to a list of valid addresses provided by the emergency services provider working with the company.
  
The combination of all required parameters (other than Instance) for this cmdlet constitutes a unique entry. Changing any of these parameters will create a new location rather than modifying an existing location. Note that although all these parameters are required, some can contain null values. The parameters that must contain non-null values are: Location, HouseNumber, StreetName, City, State, and Country. To change an existing value, you must use the Instance parameter (or pipe an instance to the cmdlet).
  
In addition to using this cmdlet to create a location, a location will also be created automatically when a new address is entered for port, subnet, switch, or wireless access point information. This information can be entered by using the **Set-CsLisPort** cmdlet, the **Set-CsLisSubnet** cmdlet, the **Set-CsLisSwitch** cmdlet, and the **Set-CsLisWirelessAccessPoint** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _City_ <br/> |Required  <br/> |System.String  <br/> |The location city.  <br/> Maximum length: 64 characters.  <br/> |
| _CompanyName_ <br/> |Required  <br/> |System.String  <br/> |The name of the company at this location.  <br/> Maximum length: 60 characters  <br/> |
| _Country_ <br/> |Required  <br/> |System.String  <br/> |The country/region this location is in.  <br/> Maximum length: 2 characters  <br/> |
| _HouseNumber_ <br/> |Required  <br/> |System.String  <br/> |The house number of the location. For a company this is the number on the street where the company is located.  <br/> Maximum length: 10 characters  <br/> |
| _HouseNumberSuffix_ <br/> |Required  <br/> |System.String  <br/> |Additional information for the house number, such as 1/2 or A. For example, 1234 1/2 Oak Street or 1234 A Elm Street.  <br/> Note: To designate an apartment number or office suite, you must use the Location parameter. For example,  `-Location "Suite 100/Office 150"`.  <br/> Maximum length: 5 characters  <br/> |
| _Instance_ <br/> |Required  <br/> |PSObject  <br/> |A reference to a location object. This object must contain the properties required to create a location. You can retrieve an object of this type by calling the **Get-CsLisLocation** cmdlet. <br/> |
| _Location_ <br/> |Required  <br/> |System.String  <br/> |The name for this location. Typically this value is the name of a location more specific than the civic address, such as an office number, but it can be any string value.  <br/> Maximum length: 20 characters  <br/> |
| _PostalCode_ <br/> |Required  <br/> |System.String  <br/> |The postal code associated with this location.  <br/> Maximum length: 10 characters  <br/> |
| _PostDirectional_ <br/> |Required  <br/> |System.String  <br/> |The directional designation of a street name. For example, NE or NW for Main Street NE or 7th Avenue NW.  <br/> Maximum length: 2 characters  <br/> |
| _PreDirectional_ <br/> |Required  <br/> |System.String  <br/> |The directional designation for a street name that precedes the name of the street. For example, NE or NW for NE Main Street or NW 7th Avenue.  <br/> Maximum length: 2 characters  <br/> |
| _State_ <br/> |Required  <br/> |System.String  <br/> |The state or province associated with this location.  <br/> Maximum length: 2 characters  <br/> |
| _StreetName_ <br/> |Required  <br/> |System.String  <br/> |The name of the street for this location.  <br/> Maximum length: 60 characters  <br/> |
| _StreetSuffix_ <br/> |Required  <br/> |System.String  <br/> |The type of street designated in a street name, such as Street, Avenue, or Court.  <br/> Maximum length: 10 characters  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Accepts pipelined input of LIS location objects.
  
## Return Types

This cmdlet does not return a value or object. It creates or modifies an object of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Remove-CsLisLocation](remove-cslislocation.md)
  
[Get-CsLisLocation](get-cslislocation.md)
  
[Set-CsLisPort](set-cslisport.md)
  
[Set-CsLisSubnet](set-cslissubnet.md)
  
[Set-CsLisSwitch](set-cslisswitch.md)
  
[Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)
  
[Get-CsLisCivicAddress](get-csliscivicaddress.md)

