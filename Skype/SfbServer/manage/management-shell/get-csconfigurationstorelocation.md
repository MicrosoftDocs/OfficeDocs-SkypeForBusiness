---
title: "Get-CsConfigurationStoreLocation"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: abfda147-02fa-46a5-a988-d83daf4cc455
description: "Reports back the location of the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsConfigurationStoreLocation
[]
Reports back the location of the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsConfigurationStoreLocation [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns the SQL Server path to the computer (or pool) hosting the Central Management store.
  
```
Get-CsConfigurationStoreLocation
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the Report parameter is included in order to specify a path for the report generated when you run the **Get-CsConfigurationStoreLocation** cmdlet.
  
```
Get-CsConfigurationStoreLocation -Report "C:\Logs\ConfigurationStore.html"
```

## Detailed Description

Active Directory Domain Services uses service control points (SCP) to help computers locate services. For example, when you install Skype for Business Server 2015, a service control point is created that provides location information for the Central Management store used to maintain Skype for Business Server 2015 data. Computers that need access to the database connect to Active Directory and use the information contained in the SCP to help them locate the correct computer and the correct instance of SQL Server.
  
The **Get-CsConfigurationStoreLocation** cmdlet is used to report back the SQL Server path (for example, atl-sql-001.litwareinc.com/rtc) to the computer running the Central Management store.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a domain controller where global settings are stored. If global settings are stored in the Active Directory System container, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\ConfigurationStore.html"` <br/> |
   
## Input Types

None. The **Get-CsConfigurationStoreLocation** cmdlet does not accept pipelined input.
  
## Return Types

String. The **Get-CsConfigurationStoreLocation** cmdlet reports back the location of the configuration store.
  
## See also

#### 

[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)
  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

