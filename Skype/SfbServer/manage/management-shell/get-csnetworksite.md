---
title: "Get-CsNetworkSite"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9627869d-101f-4668-bee2-01fce1d84cbd
description: "Retrieves one or more network sites defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010."
---

# Get-CsNetworkSite
 
Retrieves one or more network sites defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsNetworkSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Calling the **Get-CsNetworkSite** cmdlet with no parameters will return all network sites configured for CAC or E9-1-1 within the Skype for Business Server 2015 deployment.
  
```
Get-CsNetworkSite
```

### EXAMPLE 2

This command retrieves the site with the Identity (and, by definition, the NetworkSiteID) Redmond.
  
```
Get-CsNetworkSite -Identity Redmond
```

### EXAMPLE 3

The command in Example 3 calls the **Get-CsNetworkSite** cmdlet with the Filter parameter. The value of the Filter parameter is NA*, meaning that this command will retrieve all sites with an Identity beginning with the string NA and followed by any number of characters. This will return sites such as NARedmond, NAVancouver, and NAChicago.
  
```
Get-CsNetworkSite -Filter NA*
```

### EXAMPLE 4

Example 4 uses two cmdlets, the **Get-CsNetworkSite** cmdlet and the **Where-Object** cmdlet, to retrieve all the sites that are part of the NorthAmerica region. The command begins by calling the **Get-CsNetworkSite** cmdlet with no parameters to retrieve all network sites. This collection of sites is then piped to the **Where-Object** cmdlet, which filters the collection, looking for all sites in the collection where the NetworkRegionID property is equal to (-eq) NorthAmerica.
  
```
Get-CsNetworkSite | Where-Object {$_.NetworkRegionID -eq "NorthAmerica"}
```

## Detailed Description

Network sites are the offices or locations configured within each region of a CAC or E9-1-1 deployment. This cmdlet retrieves the settings for one or more existing sites.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A wildcard string that allows you to retrieve multiple sites based on matching the site Identity to the Filter value.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network site you want to retrieve. Sites are created only at the global scope, so you do not need to specify a scope. Instead, you need to specify only the site ID. (Note that this is the same value as the NetworkSiteID for the network site.)  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network site information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Retrieves an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.
  
## See also

#### 

[New-CsNetworkSite](new-csnetworksite.md)
  
[Remove-CsNetworkSite](remove-csnetworksite.md)
  
[Set-CsNetworkSite](set-csnetworksite.md)

