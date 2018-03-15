---
title: "Get-CsLisWirelessAccessPoint"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 060ea753-2fa8-4473-8e90-cb3e0fd91e63
description: "Retrieves one or more wireless access points (WAPs) from the location configuration database. Each WAP can be associated with a location, in which case this cmdlet will also retrieve the location information of the WAPs. This location association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsLisWirelessAccessPoint
 
Retrieves one or more wireless access points (WAPs) from the location configuration database. Each WAP can be associated with a location, in which case this cmdlet will also retrieve the location information of the WAPs. This location association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLisWirelessAccessPoint

```

## Examples

### EXAMPLE 1

Example 1 retrieves all Location Information Server (LIS) WAPs that have been defined in the Skype for Business Server 2015 deployment.
  
```
Get-CsLisWirelessAccessPoint
```

### EXAMPLE 2

This example retrieves all information for all WAPs that have a Basic Service Set Identifier (BSSID) equal to 99-99-99-99-99-99. Because BSSIDs must be unique, this command will retrieve, at most, one WAP location. The command begins by calling the **Get-CsLisWirelessAccessPoint** cmdlet to retrieve all WAP location associations. This collection of WAP locations is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet checks the BSSID property of each item in the collection and returns the item with the BSSID value 99-99-99-99-99-99.
  
```
Get-CsLisWirelessAccessPoint | Where-Object {$_.BSSID -eq "99-99-99-99-99-99"}
```

### EXAMPLE 3

This example retrieves all information for all WAPs that have been associated with a location in the city of Redmond. The command begins by calling the **Get-CsLisWirelessAccessPoint** cmdlet to retrieve all WAP location associations. This collection of WAP locations is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet checks the City property of each item in the collection to determine whether the value is equal to (-eq) Redmond.
  
```
Get-CsLisWirelessAccessPoint | Where-Object {$_.City -eq "Redmond"}
```

## Detailed Description

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet retrieves information on associations between physical locations and the WAP through which the client is connected.
  
This cmdlet does not take any parameters (other than the Windows PowerShell common parameters). The cmdlet will retrieve all instances of WAP to location mappings. To narrow down the information retrieved, you must pipe the output from this cmdlet to another Windows PowerShell cmdlet such as the **Where-Object** cmdlet or the **Select-Object** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types

None.
  
## Return Types

This cmdlet retrieve one or more objects of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Remove-CsLisWirelessAccessPoint](remove-csliswirelessaccesspoint.md)
  
[Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)

