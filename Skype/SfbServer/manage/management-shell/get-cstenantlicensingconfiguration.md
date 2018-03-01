---
title: "Get-CsTenantLicensingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0df23143-f1aa-4850-b0f7-750422762925
description: "Indicates whether licensing information for the specified tenant is available in the Skype for Business admin center."
---

# Get-CsTenantLicensingConfiguration
 
Indicates whether licensing information for the specified tenant is available in the Skype for Business admin center.
  
This cmdlet can only be used with Skype for Business Online.
  
```
Get-CsTenantLicensingConfiguration [-Filter] <Object>] [-Identity] <Object>] [-Tenant] <Object>] [-LocalStore]

```

## Detailed Description

The Get-CsTenantLicensingConfiguration cmdlet indicates whether licensing information for the specified tenant is available in the Skype for Business admin center. The cmdlet returns information similar to this:
  
Identity : Global
  
Status : Enabled
  
If the Status is equal to Enabled then licensing information is available in the Skype for Business admin center. If not, then licensing information is not available in the Skype for Business admin center.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Filter** <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection of tenant licensing configuration settings. Because each tenant is limited to a single, global collection of licensing configuration settings there is no need to use the Filter parameter.  <br/> |
|**Identity** <br/> |Optinal  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Specifies the collection of tenant licensing configuration settings to be returned. Because each tenant is limited to a single, global collection of licensing settings there is no need include this parameter when calling the Get-CsTenantLicensingConfiguration cmdlet.  <br/> |
|**LocalStore** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the tenant licensing configuration data from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
|**Tenant** <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the tenant account whose licensing settings are being returned. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> |
   
## Input Types

The Get-CsTenantLicensingConfiguration cmdlet does not accept pipelined input.
  
## Return Types

The Get-CsTenantLicensingConfiguration cmdlet returns instances of the Deserialized.Microsoft.Rtc.Management.WritableConfig.Settings.TenantConfiguration.TenantLicensingConfiguration object.
  
## Example

The command shown in Example 1 returns licensing configuration information for the current tenant:
  
```
Get-CsTenantLicensingConfiguration
```


