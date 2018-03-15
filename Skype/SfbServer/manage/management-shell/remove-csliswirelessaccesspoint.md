---
title: "Remove-CsLisWirelessAccessPoint"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 656190b0-bde0-4a92-a6b5-b96a389c4863
description: "Removes a Location Information Server (LIS) wireless access point (WAP). This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsLisWirelessAccessPoint
 
Removes a Location Information Server (LIS) wireless access point (WAP). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLisWirelessAccessPoint -BSSID <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 removes the LIS WAP location with the BSSID 99-99-99-99-99-99.
  
If this WAP was associated with a location, that location will not be removed, only the WAP will be removed from the location mapping.
  
```
Remove-CsLisWirelessAccessPoint -BSSID 99-99-99-99-99-99
```

### EXAMPLE 2

This example removes all WAPs in building 30. The example begins with a call to the **Get-CsLisWirelessAccessPoint** cmdlet, which returns a collection of all WAPs. This collection is piped to the **Where-Object** cmdlet, which finds the items in that collection that have a Location property that contains the string Bldg30 anywhere in the value; in other words, a Location that is like (-like) Bldg30. Finally, we pipe this collection of WAPs in building 30 to the **Remove-CsLisWirelessAccessPoint** cmdlet, which removes everything in that collection.
  
Note that, as in Example 1, no locations are removed from the location configuration database, only the WAPs that reference those locations are removed.
  
```
Get-CsLisWirelessAccessPoint | Where-Object {$_.Location -like "*Bldg30*"} | Remove-CsLisWirelessAccessPoint
```

## Detailed Description

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet removes a WAP from the location configuration database. Removing the WAP will not remove the location associated with that WAP. Use the **Remove-CsLisLocation** cmdlet to remove a location.
  
If you attempt to remove a WAP that does not exist, no action will be taken and you will not receive an error or a warning message.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BSSID_ <br/> |Required  <br/> |System.String  <br/> |The Basic Service Set Identifier (BSSID) of the wireless access point you want to remove. This value will be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Accepts pipelined input of LIS wireless access point objects.
  
## Return Types

This cmdlet removes an object of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)
  
[Get-CsLisWirelessAccessPoint](get-csliswirelessaccesspoint.md)
  
[Remove-CsLisLocation](remove-cslislocation.md)

