---
title: "Get-CsBandwidthPolicyServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9cb9cf59-c47e-40f6-9f9e-235b83329a69
description: "Retrieves one or more bandwidth policy service configurations. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsBandwidthPolicyServiceConfiguration
 
Retrieves one or more bandwidth policy service configurations. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsBandwidthPolicyServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 retrieves all bandwidth policy service configurations defined within the Skype for Business Server 2015 implementation.
  
```
Get-CsBandwidthPolicyServiceConfiguration
```

### EXAMPLE 2

This example retrieves the bandwidth policy service configuration defined for the Redmond site ( `-Identity site:Redmond`).
  
```
Get-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond
```

### EXAMPLE 3

In this example we use the Filter parameter to retrieve all bandwidth policy service configurations defined at the site level. We do this by passing the value site:\* to the Filter parameter. This will search the Identity property of all bandwidth policy service configurations for values that begin with site: and are followed by any other characters. Because all site-level configurations have Identity values beginning with site: and followed by the name of the site, this filter will find all configurations for all sites.
  
```
Get-CsBandwidthPolicyServiceConfiguration -Filter site:*
```

### EXAMPLE 4

Example 4 retrieves all bandwidth policy service configurations that allow log files to reach sizes greater than four megabytes. The example begins with a call to the **Get-CsBandwidthPolicyServiceConfiguration** cmdlet. As in Example 1, this cmdlet retrieves a collection of all configurations defined within the Skype for Business Server 2015 deployment. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet cycles through the collection one item at a time. For each item in the collection, the **Where-Object** cmdlet checks to see whether the value of the MaxLogFileSizeMb property is greater than (-gt) 4. If it is, that item remains part of the collection and is part of the command output. If the value of MaxLogFileSizeMb is not greater than 4, the item is ignored and will not be returned.
  
```
Get-CsBandwidthPolicyServiceConfiguration | Where-Object {$_.MaxLogFileSizeMb -gt 4}
```

## Detailed Description

Call admission control (CAC) is a way of determining whether to allow real-time communications sessions, such as voice or video calls, to be established based on bandwidth constraints. Within the Skype for Business Server 2015 implementation of CAC, regions, sites, and subnets are defined within a network along with the relationships and links between those entities in order to place bandwidth constraints between them. Bandwidth Policy service is the component that performs CAC functionality in the Skype for Business Server 2015 deployment, enabling the decision as to whether sufficient bandwidth exists for a call to be established. The **Get-CsBandwidthPolicyServiceConfiguration** cmdlet retrieves settings for one or more bandwidth policy services.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string containing one or more wildcard characters that will be used to search the Identity property of all bandwidth policy service configurations to find every configuration with an Identity that matches the wildcard pattern. For example, the Filter value site:\* will retrieve all configurations with Identity values that begin with the string site: and end with any set of characters.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the configuration you want to retrieve. This identifier will consist of the scope (for the global configuration) or the scope and name (for a site-level configuration, such as site:Redmond).  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the bandwidth policy service configuration from the local replica of the Central Management store, rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Returns one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration.
  
## See also

#### 

[New-CsBandwidthPolicyServiceConfiguration](new-csbandwidthpolicyserviceconfiguration.md)
  
[Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)
  
[Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)

